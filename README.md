# Realworld Problems solved with alternative Flask UX
Instead of VUE, React and Angular, what alternatives are there to JQuery. 

## HTMX, Hyperscript + Alpine.js in the real world.
There is nothing worse than trying to get to figure something out and you end up with lengthy tutorials, that start off with you instaling a Flask app. So this article assumes you have a certain level of experience or a grasp of the fundamentals. 


### Problem1: Navigate to a new page at the same time update a visit date and counter to the DB.

Scenario: Click hyperlink, navigate to a new page, record the date time visited at the same time. 
Solution: HTMX and hyperscript. 

url.html
``` python
  <a href="{{ bm.url }}" target="_blank"
   hx-post="{{ url_for('api_launch_url', id = bm.id) }}"
   hx-trigger="click"
   hx-swap="innerHTML"
   hx-target="{{ '#d'~bm.id }}"
   _="on click go to url '{{ bm.url }}' in new window" >

   <img src="https://img.youtube.com/vi/{{ bm.yt_thumb }}/0.jpg" alt="yt"
</a>
<div {{ 'd'~bm.id }}></div>
```
**hx-post** The Ajax call to end point.


**hx-target** This is where we return the ajax response.  ID is dynamically created. 


`_="on click go to url..`   Hypertext - the syntax is easy to follow. On click to to Url, as simple as that. 







