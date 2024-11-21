---
layout: schedule
permalink: /schedule/
title: Schedule
description: Note - This schedule is tentative and subject to change as the semester progresses.
---

{% assign current_module = 0 %}
{% assign skip_classes = 0 %}
{% assign prev_date = 0 %}
{% assign recitation_count = 0 %}

{% for item in site.data.lectures %}
{% if item.date %}
{% assign lecture = item %}
{% assign event_type = "upcoming" %}
{% assign today_date = "now" | date: "%s" | divided_by: 86400 %}
{% assign lecture_date = lecture.date | date: "%s" | divided_by: 86400 %}
{% if today_date > lecture_date %}
    {% assign event_type = "past" %}
{% elsif today_date <= lecture_date and today_date > prev_date %}
    {% assign event_type = "warning" %}
{% endif %}
{% assign prev_date = lecture_date %}


<tr class="{{ event_type }}{% if lecture.recitation != blank %} recitation-row{% elsif lecture.title contains 'Midterm' %} midterm-row{% elsif lecture.title contains 'recess' %} recess-row{% endif %}">
    <th scope="row">{{ lecture.date }}</th>
    {% if lecture.recitation != blank %} 
    {% assign recitation_count = recitation_count | plus: 1 %}
    {%endif%}
    {% if lecture.title contains 'No class' or lecture.title contains 'cancelled' or lecture.title contains 'Buffer' or lecture.title contains 'Midterm' %}
        {% assign skip_classes = skip_classes | plus: 1 %}
        <td colspan="4" align="center">{{ lecture.title }}<p align="right"  style="color:#E12222 ">{{ lecture.logistics }}</p></td>
    {% elsif lecture.quiz != blank %}
        {% assign skip_classes = skip_classes | plus: 1 %}
        <td colspan="4" align="center">{{ lecture.quiz }}<p align="right"  style="color:#E12222 ">{{ lecture.logistics }}</p></td>
    {% else %}
    <td>
        {% if lecture.title %}
            Lecture #{{ forloop.index | minus: current_module | minus: skip_classes | minus: recitation_count}}:
        {% endif %}
        {% if lecture.title %}
            <!-- <br />{{ lecture.title }}<br /> -->
            <ul>
                {% for tit in lecture.title %}
                <li>{{ tit }}</li>
            {% endfor %}
             </ul>
        {% endif %}
        {% if lecture.recitation %}
            Recitation #{{ recitation_count }}:
        {% endif %}
        {% if lecture.recitation %}
            <br />{{ lecture.recitation }}<br />
        {% endif %}
        <!-- {% if lecture.lecturer %} -->
        <!-- Presenter(s):
        <ul class="no-bullets">
            {% for lecturer in lecture.lecturer %}
                 <li style="color:#397DF6;font-weight:bold">{{ lecturer }}</li>
            {% endfor %}                
        </ul>            
        {% endif %} -->
        {% if lecture.panelists %}
        Panel:
        {% for lecturer in lecture.lecturer %}
            <span style="color:#397DF6">{{ lecturer }},</span>            
        {% endfor %}                
        <span style="color:#397DF6">{{ panelist }}</span>
        {% for panelist in lecture.panelists %}
                {% if forloop.last == false %}
                    <span style="color:#397DF6">{{ panelist }},</span>
                {% else %}    
                    <span style="color:#397DF6">{{ panelist }}</span>
                {% endif %}
        {% endfor %}                
        <!-- <p style="color:green;">{{ lecture.lecturer }}</p><br /> -->
        {% endif %}

        {% if lecture.guest %}
            {% for guest in lecture.guest %}
                <div style="margin-bottom: 0px;">
                Guest lecturer: <br/> <span style="color:#397DF6">{{ guest.name }}, {{ guest.affil }}</span>
                </div>
                {% if guest.photo %}
                    <a href="{{ guest.profile }}" target="_blank">
                        <img src="{{ guest.photo }}" alt="Photo of {{ guest.name }}" style="max-width:34%; height:auto; margin:10px 0;">
                    </a>
                {% endif %}
            {% endfor %}
            <br/>
        {% endif %}

        {% if lecture.slides or lecture.slides2 or lecture.annotated %}        
        [
        {% endif %}
            {% if lecture.slides %}
              <a href="{{ lecture.slides }}" target="_blank">slides</a>
            {% endif %}
            {% if lecture.slides2 %}
              | <a href="{{ lecture.slides2 }}" target="_blank">slides 2</a>
            {% endif %}
            {% if lecture.slides3 %}
              | <a href="{{ lecture.slides3 }}" target="_blank">slides on choosing projects</a>
            {% endif %}            
            {% if lecture.annotated %}
              (<a href="{{ lecture.annotated }}" target="_blank">annotated</a>)
            {% endif %}            
            {% if lecture.video %}
            | <a href="{{ lecture.video }}" target="_blank">video</a>
            {% else %}
            <!-- | video -->
            {% endif %}
            {% if lecture.notes %}
            | <a href="{{ lecture.notes }}" target="_blank">notes</a>
            {% endif %}
            {% if lecture.notes2 %}
              | <a href="{{ lecture.notes2 }}" target="_blank">notes 2</a>
            {% endif %}
        {% if lecture.slides or lecture.slides2 %}        
        ]
        {% endif %}
        {% if lecture.question-form %}
            <br/> [ <a href="{{ lecture.question-form }}" target="_blank">questions form</a> ] 
        {% endif %}
        {% if lecture.notebook %}
            <br/> [ <a href="{{ lecture.notebook }}" target="_blank"> {{lecture.notebook_title}} </a> ] 
        {% endif %}       


    </td>
    <td>
        {% if lecture.readings %}
        Main readings:         
        <ul class="space_list">
        {% for reading in lecture.readings %}
            <li>{{ reading }}</li> 
        {% endfor %}
        </ul>
        {% endif %}
        {% if lecture.optional %} 
        Optional readings:            
        <ul class="space_list_no_indent">
            {% for optional in lecture.optional %}
                <li>{{ optional }}</li>            
            {% endfor %}        
        </ul>            
        {% endif %}
    </td>
    <td>
        <p  style="color:#E12222 ">{{ lecture.logistics }}</p>
    </td>
    {% endif %}
</tr>
{% else %}
{% assign current_module = current_module | plus: 1 %}
{% assign module = item %}
<tr class="info">
    <td colspan="5" align="center"><strong>{{ module.title }}</strong></td>
</tr>
{% endif %}
{% endfor %}
