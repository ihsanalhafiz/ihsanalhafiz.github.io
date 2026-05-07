---
layout: page
permalink: /repositories/
title: repositories
description: Selected GitHub repositories related to hardware acceleration, neuromorphic computing, FPGA development, and research workflows.
nav: true
nav_order: 4
---

<style>
  .repository-intro {
    margin-bottom: 2rem;
  }

  .repository-actions {
    display: flex;
    flex-wrap: wrap;
    gap: 0.75rem;
    margin-top: 1rem;
  }

  .repository-grid {
    display: grid;
    grid-template-columns: repeat(auto-fit, minmax(260px, 1fr));
    gap: 1rem;
    margin-top: 1.25rem;
  }

  .repository-card {
    border: 1px solid var(--global-divider-color);
    border-radius: 8px;
    padding: 1rem;
    min-height: 100%;
    background: var(--global-card-bg-color);
  }

  .repository-card h3 {
    font-size: 1.15rem;
    margin-bottom: 0.5rem;
  }

  .repository-card p {
    margin-bottom: 0.85rem;
  }

  .repository-meta,
  .repository-topics {
    display: flex;
    flex-wrap: wrap;
    gap: 0.5rem;
    align-items: center;
  }

  .repository-meta {
    justify-content: space-between;
    margin-top: 1rem;
  }

  .repository-topic {
    border: 1px solid var(--global-divider-color);
    border-radius: 999px;
    color: var(--global-text-color-light);
    font-size: 0.8rem;
    padding: 0.15rem 0.55rem;
  }

  .repository-link {
    white-space: nowrap;
  }
</style>

<div class="repository-intro">
  <p>
    A small selection of code and project repositories connected to my work in hardware acceleration,
    neuromorphic computing, FPGA platforms, and reproducible research workflows.
  </p>

  <div class="repository-actions">
    {% for user in site.data.repositories.github_users %}
      <a class="btn btn-sm btn-outline-primary" href="https://github.com/{{ user }}" target="_blank" rel="noopener noreferrer">
        <i class="fa-brands fa-github"></i>
        GitHub profile
      </a>
    {% endfor %}
  </div>
</div>

{% if site.data.repositories.featured_repositories %}

## Featured repositories

<div class="repository-grid">
  {% for repo in site.data.repositories.featured_repositories %}
    <article class="repository-card">
      <h3>
        <a href="{{ repo.url }}" target="_blank" rel="noopener noreferrer">{{ repo.name }}</a>
      </h3>
      <p>{{ repo.summary }}</p>

      {% if repo.topics %}
        <div class="repository-topics" aria-label="{{ repo.name }} topics">
          {% for topic in repo.topics %}
            <span class="repository-topic">{{ topic }}</span>
          {% endfor %}
        </div>
      {% endif %}

      <div class="repository-meta">
        <span class="text-muted">{{ repo.owner }}</span>
        <a class="repository-link" href="{{ repo.url }}" target="_blank" rel="noopener noreferrer">
          View repository
          <i class="fa-solid fa-arrow-up-right-from-square"></i>
        </a>
      </div>
    </article>
  {% endfor %}
</div>

{% endif %}
