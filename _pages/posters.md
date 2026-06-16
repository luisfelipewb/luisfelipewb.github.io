---
layout: page
title: posters
permalink: /posters/
description: Conference posters from my research.
nav: true
nav_order: 3
---

<div class="row row-cols-1 row-cols-md-2 g-4 mt-2">
  {% assign posters = "2026ICRA,ICRA 2026|2025VCIP,VCIP 2025|2025ICRA,ICRA 2025|2024IROS,IROS 2024|2024ECCV,ECCV 2024" | split: "|" %}

{% for item in posters %}
{% assign parts = item | split: "," %}
{% assign slug = parts[0] %}
{% assign label = parts[1] %}
{% assign pdf_path = '/assets/pdf/posters/' | append: slug | append: '_poster.pdf' %}
{% assign modal_id = 'modal-' | append: slug %}

    <div class="col">
      <div class="card h-100 hoverable">
        <!-- pointer-events:none on iframe passes clicks through to the parent div -->
        <div style="cursor: pointer;" data-bs-toggle="modal" data-bs-target="#{{ modal_id }}">
          <iframe src="{{ pdf_path | relative_url }}#view=Fit&toolbar=0"
                  style="width: 100%; height: 620px; border: none; pointer-events: none; display: block;"
                  loading="lazy"></iframe>
        </div>
        <div class="card-body d-flex justify-content-between align-items-center py-2">
          <span class="font-weight-bold">{{ label }}</span>
          <a href="{{ pdf_path | relative_url }}" target="_blank" rel="noopener noreferrer"
             class="btn btn-sm z-depth-0" role="button">
            <i class="fa-solid fa-file-pdf"></i> Download
          </a>
        </div>
      </div>
    </div>

    <!-- Full-screen modal for {{ label }} -->
    <div class="modal fade" id="{{ modal_id }}" tabindex="-1" aria-label="{{ label }}" aria-hidden="true">
      <div class="modal-dialog modal-xl modal-dialog-centered">
        <div class="modal-content">
          <div class="modal-header py-2">
            <h5 class="modal-title">{{ label }}</h5>
            <button type="button" class="btn-close" data-bs-dismiss="modal" aria-label="Close"></button>
          </div>
          <div class="modal-body p-0">
            <iframe src="{{ pdf_path | relative_url }}"
                    style="width: 100%; height: 85vh; border: none;"></iframe>
          </div>
        </div>
      </div>
    </div>

{% endfor %}

</div>
