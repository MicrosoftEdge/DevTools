# Microsoft Edge DevTools Explainers

This folder is home to the "explainers" and related documents originating from the Microsoft Edge DevTools team.

Explainers are documents focused on describing a user/ developer/ customer problem (at a high level) and exploring potential solutions to the problem. These documents are starting points for engaging in discussion with you and other members of the community. Explainers should address their stated problems in clear and easy to understand language. Proposed solutions should be easy to follow and not too deep in technical details. When you read an explainer, we hope the stated problem is compelling and you can form an opinion for whether the proposed solution would address the problem.

## Providing feedback

We are looking for feedback! Are the stated problems relevant to you? How have they impacted your experience? Do the proposed solutions seem reasonable? Would they solve a problem you currently have? (We love to hear that; tell us more about your scenario!) Do you have related use-cases we hadn't considered?

We appreciate you taking the time to offer feedback; it helps to improve the explainers, and validate the problem and solutions they describe.

**[Start a new issue here](https://github.com/MicrosoftEdge/DevTools/issues/new/choose)**, or [join in the discussion](https://github.com/MicrosoftEdge/DevTools/issues) on existing issues. We also welcome PRs on the explainer documents themselves.

<!--
<ul>
{%- for post in site.static_files -%}
    {% if post.path contains 'explainers' %}
    {% if post.path contains '.md' %}
          <li><a href="{{ post.path }}">
        {% assign names = post.path | split: "/" %}
          {% for subpath in names %}
            {% if forloop.index0 == 2 %}{{ subpath }}{% endif %}
          {% endfor %}
             </a></li>
    {% endif %}
    {% endif %}
{%- endfor -%}
</ul>
-->