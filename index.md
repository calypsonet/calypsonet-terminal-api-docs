---
---
#### All available Calypso Networks Association Terminal API documentation can be found below

<table>
 <tbody>
   {% assign dirs = site.pages | map: 'path' | sort %}
   {% assign seen_dirs = "" | split: "," %}
   {% for dir in dirs %}
     {% assign parts = dir | split: '/' %}
     {% if parts.size > 1 %}
       {% assign subdir = parts[0] %}
       {% unless subdir == "" or subdir == "." or subdir == "assets" or subdir == "archived" or seen_dirs contains subdir %}
         <tr>
           <td><a href="{{ subdir | relative_url }}">{{ subdir }}</a></td>
         </tr>
         {% assign seen_dirs = seen_dirs | push: subdir %}
       {% endunless %}
     {% endif %}
   {% endfor %}
 </tbody>
</table>

#### Archived libraries (moved to [Eclipse Keypop project](https://keypop.org))

<table>
 <tbody>
   {% assign archived_dirs = site.pages | map: 'path' | sort %}
   {% assign seen_archived_dirs = "" | split: "," %}
   {% for dir in archived_dirs %}
     {% assign parts = dir | split: '/' %}
     {% if parts.size > 2 and parts[0] == "archived" %}
       {% assign archived_subdir = parts[1] %}
       {% unless seen_archived_dirs contains archived_subdir %}
         <tr>
           <td><a href="{{ 'archived/' | append: archived_subdir | relative_url }}">{{ archived_subdir }}</a></td>
         </tr>
         {% assign seen_archived_dirs = seen_archived_dirs | push: archived_subdir %}
       {% endunless %}
     {% endif %}
   {% endfor %}
 </tbody>
</table>