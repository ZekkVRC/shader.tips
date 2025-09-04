---
title: Link Directory
layout: page
nav_order: 2
---
# 🌐 Link Directory
<div style="font-size: 0.9em; color: #858585ff; margin-bottom: 1.5rem;">
  <span style="margin-right: 1.5rem;"><strong>Author:</strong> <a href="{{ site.FirstPartyAuthorLink }}" style="color: inherit;">Zekk</a></span>
  <span style="margin-right: 1.5rem;"><strong>Last updated:</strong> 9/4/2025</span>
  <span><strong>Page Views: </strong><span id="hit-count">...</span></span>
</div>

Collection of links I have accumulated over time. Not well organized. Use search!!! This will be constantly growing as I find and remember more links to put in here! <br>

--> Tags are WIP, currently just a list of words. Multi-tag search not implemented. <br>
<small>Noob = Good for beginner shader programmers. <br>
Collection = Sites that are a collection of articles, links, or other resources. <br>
VRChat = Possible in VRChat, Useful for VRChat shaders, etc. <br>
VRCHack = Has info on a workaround that only makes sense to use in VRC <br>
Unity = Focused on Unity. Shaderlab syntax. Unity Macros. <br>
Shadertoy = Focused on Shadertoy. Shadertoy Macros. <br>
Math = Math related. <br>
HLSL = HLSL Code. <br>
GLSL = GLSL Code. <br>
Nodes = Uses node graphs rather than code. <br>
Frag = Uses fragment shader. <br>
Vert = Uses vertex shader. <br>
Geom = Uses geometry shader. <br>
Tess = Uses tesselation (hull/domain). <br>
Compute = Uses compute shaders. <br>
Surf = Uses Unity Surface shaders. <br>
Screen = Screenspace effects. <br>
Fundamentals = Covers fundamentals concepts relevant to computer graphics.<br>
Perf = Covers performance related information.<br>
Tool = A tool for making shaders.<br>
Video = A Video
</small>
 
<table id="linkTable"  style="width: 100%; border-collapse: collapse;">
  <thead>
    <tr>
      <th>Title</th>
      <th>Description (Or abstract)</th>
      <th>Tags</th>
    </tr>
  </thead>
  <tbody>
    {% for item in site.data.links %}
      <tr>
        <td>
        <div style="display: flex; justify-content: space-between; align-items: center; width: 100%; ">
            <a href="{{ item.url }}" target="_blank" 
            style="color: #8ec5ffff; text-decoration: none; width: 90%;" 
            onmouseover="this.style.color='#8effecff'; this.style.textDecoration='underline';" 
            onmouseout="this.style.color='#8ec5ffff'; this.style.textDecoration='none';" >
            {{ item.title }}
            </a>
            <a href="https://web.archive.org/web/2/{{ item.url }}" target="_blank" title="View on Wayback Machine" style="text-decoration: none;">
            📦
            </a>
        </div>
        </td>
        <td>{{ item.description }}</td>
        <td style="width:15%">
            {% assign sorted_tags = item.tags | sort %}
            {% for tag in sorted_tags %}
            <span class="tag">{{ tag }}</span>
            {% endfor %}
        </td>
      </tr>
    {% endfor %}
  </tbody>
</table>
