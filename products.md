---
layout: default
title: Products
---
{% for product in site.data.products %}
{% capture thecycle %}{% cycle 'even', 'odd' %}{% endcapture %}
<div class="card my-5 animate__animated animate__fadeInUp animate_delay_{{ forloop.index }}s" style="border-{% if thecycle == 'even' %}left{% else %}right{% endif %}: 2px solid rgb(104, 144, 153);">
    <div class="row">
    {% if thecycle == 'odd' %}
        <div class="col">
            <img src="{{ product.image }}" class="img-fluid">
        </div>
    {% endif %}
        <div class="col-lg-7">
            <div class="card-body py-3 px-5">
                <h3 class="card-title pb-4">{{ product.name }}</h3>
                <p class="card-text">{{ product.description }}</p>
                {% if product.extra %}
                {% if product.extra.name == "link" %}
                <div class="pt-4">
                    <button class="btn btn-primary py-2 px-3" onclick="location.href='{{ product.extra.url }}'" type="button">{{ product.extra.description }}</button>
                </div>
                {% endif %}
                {% if product.extra.name == "bar_graph" %}
                {% for item in product.extra.items %}
                <div class="mt-5" style="color: rgb(118, 118, 118)">{{ item.name }}</div>
                {% for object in item.items %}
                <div style="background-color: rgb(222, 222, 222); box-shadow: 6px 6px 3px 0px rgb(230, 230, 230);">
                <div class="mt-2 mb-3" style="background-color: rgb(104, 144, 153); width: {{ object.value | times: 100}}%; color: white; font-weight: 200">
                    <div class="mx-2">{{ object.name }}</div>
                </div>
                </div>
                {% endfor %}
                {% endfor %}
                {% endif %}
                {% endif %}
            </div>
        </div>
{% if thecycle == 'even' %}
        <div class="col">
            <img src="{{ product.image }}" class="img-fluid">
        </div>
{% endif %}
    </div>
</div>
<div class="py-5"></div>
{% endfor %}