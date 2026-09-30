<h2 id="publications" style="margin: 2px 0px -15px;">Publications & Preprints</h2>

<div class="publications">
<ol class="bibliography">

{% for link in site.data.publications.main %}

{% assign metadata_fields = "|title|authors|conference_short|conference|image|notes|others|" %}

<li>
<div class="pub-row">
  <div class="{% if link.image %}col-sm-3{% else %}col-sm-1{% endif %} abbr" style="position: relative;{% if link.image %}padding-right: 15px;padding-left: 15px;{% else %}padding-right: 0;padding-left: 0;width: 0;{% endif %}">
    {% if link.image %} 
    <img src="{{ link.image }}" class="teaser img-fluid z-depth-1" style="width=100;height=40%">
    {% if link.conference_short %} 
    <abbr class="badge">{{ link.conference_short }}</abbr>
    {% endif %}
    {% endif %}
  </div>
  <div class="{% if link.image %}col-sm-9{% else %}col-sm-11{% endif %}" style="position: relative;{% if link.image %}padding-right: 15px;padding-left: 20px;{% else %}padding-right: 15px;padding-left: 0;width: 100%;{% endif %}">
      <div class="title"><a href="{{ link.PDF }}" data-goatcounter-click="publication:{{ link.title | escape }}">{{ link.title }}</a></div>
      <div class="author">{{ link.authors }}</div>
      <div class="periodical"><em>{{ link.conference }}</em>
      </div>
    <div class="links">
      {% for field in link %}
      {% assign field_name = field[0] %}
      {% assign field_value = field[1] %}
      {% capture field_token %}|{{ field_name }}|{% endcapture %}
      {% unless metadata_fields contains field_token %}
      {% if field_value %}
      {% assign link_label = field_name | replace: "_", " " %}
      <a href="{{ field_value }}" class="btn btn-sm z-depth-0" role="button" target="_blank" style="font-size:12px;" data-goatcounter-click="publication:{{ link.title | escape }}">{{ link_label }}</a>
      {% endif %}
      {% endunless %}
      {% endfor %}
      {% if link.notes %} 
      <strong> <i style="color:#e74d3c">{{ link.notes }}</i></strong>
      {% endif %}
      {% if link.others %} 
      {{ link.others }}
      {% endif %}
    </div>
  </div>
</div>
</li>
<br>

{% endfor %}

</ol>
</div>
