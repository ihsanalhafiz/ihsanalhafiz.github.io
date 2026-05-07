---
layout: post
title: play with always_comb and always_ff in systemverilog
date: 2026-05-07
description: how to manage _d and _q in systemverilog
tags: systemverilog
categories: HDL
chart:
  plotly: false
---

When we write HDL in SystemVerilog, one common best practice is to separate the value that is stored in a flip-flop from the value that will be stored on the next clock edge. A popular naming convention is to use `_q` for the registered value and `_d` for the next value.

This style is often used in a Finite State Machine (FSM). The state movement is calculated in `always_comb` using blocking assignment `=`, and the result is assigned to the `_d` signal. Then, in `always_ff`, the `_q` signal is updated from `_d` using non-blocking assignment `<=`.

In short:

- `_q` means the current registered value.
- `_d` means the next value that will be loaded into the register.
- `always_comb` describes combinational logic.
- `always_ff` describes sequential logic.

## Why use `_d` and `_q`?

The `_d` and `_q` convention makes the design easier to read because it follows the behavior of a D flip-flop:

- `D` is the input of the flip-flop.
- `Q` is the output of the flip-flop.

For an FSM, the current state is stored in `state_q`, and the next state is calculated in `state_d`.

## Example: simple traffic light FSM

The example below has three states: red, green, and yellow. On every clock cycle, the FSM moves to the next state.

```systemverilog
module traffic_light_fsm (
    input  logic clk_i,
    input  logic rst_ni,
    output logic red_o,
    output logic yellow_o,
    output logic green_o
);

    typedef enum logic [1:0] {
        RED,
        GREEN,
        YELLOW
    } state_e;

    state_e state_d;
    state_e state_q;

    // Combinational logic: decide the next state.
    always_comb begin
        state_d = state_q;

        case (state_q)
            RED: begin
                state_d = GREEN;
            end

            GREEN: begin
                state_d = YELLOW;
            end

            YELLOW: begin
                state_d = RED;
            end

            default: begin
                state_d = RED;
            end
        endcase
    end

    // Sequential logic: update the current state on the clock edge.
    always_ff @(posedge clk_i or negedge rst_ni) begin
        if (!rst_ni) begin
            state_q <= RED;
        end else begin
            state_q <= state_d;
        end
    end

    // Output logic based on the current state.
    always_comb begin
        red_o    = 1'b0;
        yellow_o = 1'b0;
        green_o  = 1'b0;

        case (state_q)
            RED: begin
                red_o = 1'b1;
            end

            GREEN: begin
                green_o = 1'b1;
            end

            YELLOW: begin
                yellow_o = 1'b1;
            end

            default: begin
                red_o = 1'b1;
            end
        endcase
    end

endmodule
```

## Important pattern

The most important part is this pair:

```systemverilog
always_comb begin
    state_d = state_q;

    case (state_q)
        RED:    state_d = GREEN;
        GREEN:  state_d = YELLOW;
        YELLOW: state_d = RED;
        default: state_d = RED;
    endcase
end

always_ff @(posedge clk_i or negedge rst_ni) begin
    if (!rst_ni) begin
        state_q <= RED;
    end else begin
        state_q <= state_d;
    end
end
```

The `always_comb` block decides what should happen next. The `always_ff` block stores that decision on the clock edge.

## Blocking vs non-blocking assignment

Inside `always_comb`, use blocking assignment:

```systemverilog
state_d = GREEN;
```

This is because combinational logic should behave like immediate logic calculation.

Inside `always_ff`, use non-blocking assignment:

```systemverilog
state_q <= state_d;
```

This is because sequential logic updates registers together on the clock edge.

## Common mistake

A common mistake is to update the current state directly in `always_comb`:

```systemverilog
always_comb begin
    state_q = GREEN; // Avoid this
end
```

This is not the correct style because `state_q` should be controlled only by the flip-flop in `always_ff`. The combinational block should calculate `state_d`, and the sequential block should update `state_q`.

## Conclusion

Using `_d` and `_q` helps separate combinational logic from sequential logic. The `_d` signal represents the next value, while the `_q` signal represents the registered value. This makes an FSM easier to understand, easier to debug, and safer to modify later.
