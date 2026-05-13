---
tags: [{% for t in tags %}{{t.tag}}{% if not loop.last %}, {% endif %}{% endfor %}]
title: "{{title}}"
authors: {{ authors }} 
year: {{date|format("YYYY")}}
url: {{ url }} 
citekey: {{ citekey }} 
aliases: "{{title}}"
created: 
modified:
---
zoteroLink: {% if pdfZoteroLink %}{{pdfZoteroLink}}{% else %}No PDF{% endif %}
relations: {% if relations and relations.length > 0 %} {% for relation in relations %} [[@{{relation.citekey}}]]{% if not loop.last %}, {% endif%} {% endfor %} {% endif%}

> [!abstract]-
> {{abstractNote}}

{% persist "persistent data" %} {% if isFirstImport %}
# @{{citekey}}
## 🟠1st Pass
### 1. Context

### 2. Correctness

### 3. Contributions

{% endif %} {% endpersist %}

{%-
    set zoteroColors = {
        "#2ea8e5": "blue",
        "#5fb236": "green",
        "#a28ae5": "purple",
        "#ff6666": "red",
        "#ffd400": "yellow",
        "#f19837": "orange",
        "#aaaaaa": "grey",
        "#e56eee": "magenta"
    }
-%}

{%-
   set colorHeading = {
		"yellow": "⭐Interesting Points",
		"purple": "🎯Definitions",
		"magenta": "🧝‍♀️Summarizing Points",
		"blue": "🧪Design & Methodologies",
		"red": "❗Limitations, Gaps & Critiques",
		"orange": "🍃Fleeting Thoughts",
		"green": "👀 Follow-up",
		"grey": "🔖Bookmark"
   }
-%}

{%- macro calloutHeader(type) -%}
    {%- switch type -%}
        {%- case "highlight" -%}
         [[@{{citekey}}]]
        {%- case "image" -%}
        Image
        {%- default -%}
        Note
    {%- endswitch -%}
{%- endmacro %}

{%- set newAnnot = [] -%}
{%- set newAnnotations = [] -%}
{%- set annotations = annotations %}

{%- for annot in annotations -%}
    {%- if annot.color in zoteroColors -%}
        {%- set customColor = zoteroColors[annot.color] -%}
		{%- set customColorHeading = colorHeading[customColor] -%}
    {%- elif annot.colorCategory|lower in colorHeading -%}
    	{%- set customColor = annot.colorCategory|lower -%}
    {%- else -%}
	    {%- set customColor = "other" -%}
    {%- endif -%}
    {%- set newAnnotations = (newAnnotations.push({"annotation": annot, "customColor": customColor, "customColorHeading":customColorHeading}), newAnnotations) -%}
{%- endfor -%}

{%- for entry in newAnnotations  -%}
{%- set annot = entry.annotation -%}

{%- if entry and loop.first %}
# Excerpts
{%- endif %}

{{entry.customColorHeading}}
{{calloutHeader(annot.type)}} ([Page {{annot.page}}]({{annot.desktopURI}}))

{%- if annot.annotatedText %}
> {{annot.annotatedText}} {% if annot.hashTags %}{{annot.hashTags}}{% endif -%}
{%- endif %}

{%- if annot.imageRelativePath %}
> ![[{{annot.imageRelativePath}}]]
{%- endif %}

{%- if annot.ocrText %}
> {{annot.ocrText}}
{%- endif %}

{%- if annot.comment %}
- {{annot.comment}}
{%- endif -%}

{%- endfor -%}