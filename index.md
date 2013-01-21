---
layout: default
---

## Hi! I'm Dave

<div class="row">
  <div class="span6">
{% capture content %}
{% include homeleft.md %}
{% endcapture %}
{{ content | unindent | markdownify }}
  </div>
  <div class="span2" id="homeRight">
{% capture content %}
{% include homeright.md %}
{% endcapture %}
{{ content | unindent | markdownify }}
  </div>
</div>