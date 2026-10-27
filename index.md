---
---
#### Specifications of the Calypso Networks Association Terminal APIs

<table>
 <thead>
   <tr><th>Specification</th><th>Latest stable</th></tr>
 </thead>
 <tbody>
   {% assign dirs = site.pages | map: 'path' | sort %}
   {% assign seen_dirs = "" | split: "," %}
   {% for dir in dirs %}
     {% assign parts = dir | split: '/' %}
     {% if parts.size > 1 %}
       {% assign subdir = parts[0] %}
       {% unless subdir == "" or subdir == "." or subdir == "assets" or subdir == "archived" or seen_dirs contains subdir %}
         {% comment %} Published under a short slug: the label is the API name (doc_name), or the title of the API page (its repository name) until its next publication {% endcomment %}
         {% assign index_path = subdir | append: "/index.md" %}
         {% assign api_page = site.pages | where: "path", index_path | first %}
         <tr>
           <td><a href="{{ subdir | append: '/' | relative_url }}">{{ api_page.doc_name | default: api_page.title | default: subdir }}</a></td>
           <td>{{ api_page.latest_stable | default: "&mdash;" }}</td>
         </tr>
         {% assign seen_dirs = seen_dirs | push: subdir %}
       {% endunless %}
     {% endif %}
   {% endfor %}
 </tbody>
</table>

#### Archived APIs (now maintained in the [Eclipse Keypop project](https://keypop.org))

<table>
 <thead>
   <tr><th>Archived API</th></tr>
 </thead>
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
