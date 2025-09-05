---
title: Getting Started With Shaders
layout: post
nav_order: 1
published: True
---
{: .WIP }
> This article is a WIP. Some parts may not be finished!

{: .VRChat }
> This article is Unity/VRChat focused. It may still be helpful for you in your shader journey though! I plan to make a general shader quickstart in the future!

# Getting Started With Shaders for Unity/VRChat
<div style="font-size: 0.9em; color: #858585ff; margin-bottom: 1.5rem;">
  <span style="margin-right: 1.5rem;"><strong>Author:</strong> <a href="{{ site.FirstPartyAuthorLink }}" style="color: inherit;">Zekk</a></span>
  <span style="margin-right: 1.5rem;"><strong>Last updated:</strong> 9/5/2025</span>
  <span><strong>Page Views: </strong><span id="hit-count">...</span></span>
</div>

When getting started learning shaders for Unity, you immediately have a decision to make: to Node or to Code?

Unity has a built in node editor called [shadergraph](https://learn.unity.com/tutorial/introduction-to-shader-graph){:target="_blank"} that allows you to build shaders using drag and drop nodes. There are also third party packages like [Amplify Shader Editor](https://amplify.pt/unity/amplify-shader-editor/){:target="_blank"} that offer more functionality.

{: .Caution }
> VRChat currently does not support native shadergraph, to use shadergraph for VRChat, you can use a custom fork by z3y which fixes the incompatibilities: [https://github.com/z3y/ShaderGraphVRC](https://github.com/z3y/ShaderGraphVRC){:target="_blank"}

These are both node based solutions for writing shaders. However, amplify is a paid package while shadergraph is free.

On the other hand, shaders can also be directly programmed in [HLSL](https://learn.microsoft.com/en-us/windows/win32/direct3dhlsl/dx-graphics-hlsl){:target="_blank"} (wrapped in Unity's [Shaderlab](https://docs.unity3d.com/6000.2/Documentation/Manual/SL-Reference.html){:target="_blank"}).

Broadly speaking, its best to pick a path, and stick with it for now. One nice thing is that whichever path you take, nodes or code, you are still learning the core fundamentals behind writing shaders. A lot of the nodes that you use in a node based solution like shadergraph are actually functions that can be directly called from code under the hood. This means that if later you want to switch your path, the learning curve is just getting used to the medium (though this can be deceptively hard). In a lot of ways the "flow" of the shader is the same in nodes and code.

That being said... in my opinion, you should start learning with code. Especially for VRChat shaders. 

There are a few reasons for this, but the core three are this: 
1. Most other popular shaders for VRChat are code which helps get you used to digging into them if you want to add features, or make modifications.
2. Nodes become unwieldy as they get more complex. At some point your graph is so big that you spend more time managing your graph than working on the shader. This also happens for code, but its much easier to manage.
3. Nodes cannot* do some things that advanced VRChat shader tech requires (Geometry shaders, Loops).<br>
<small>*Nodes can do some of these in certain cases, I believe amplify now supports geometry shaders, and loops can be done in the custom code node, but at that point you are just writing code in your nodes...</small>

There is also a resources issue. The reality is that most interesting shader stuff is not written in nodes. Once you get past the beginner stage where you are following tutorials, you will likely find yourself starved for new content. This often means that to learn often you are just converting code to nodes anyway.

The main **advantages** of using nodes is that they are less intimidating, faster to get started with, and offer a *very* useful live preview at each node of what the effect currently looks like.

If you already know a programming language, to me this is a no-brainer, go for code. If you don't, and are considering nodes because they are less intimidating and don't require you to learn to code, I would seriously consider how deep you hope to go with shaders. If the answer is "deep" consider learning programming along with shaders! I promise you won't regret it :P

---

### Getting Started With Nodes

With all that in mind, if you are going with nodes, this is your stop. Remember when watching any shadergraph resource for VRChat use to ignore the setup/installation instructions they say, and instead make a normal project with VCC and install shadergraph from [https://github.com/z3y/ShaderGraphVRC](https://github.com/z3y/ShaderGraphVRC){:target="_blank"}.

For starting node resources, these were the best that I could find:
1. [Daniel Lett Videos](https://www.youtube.com/playlist?list=PLsaDw3p1XpJiGHPnA8gZH6gO2gQYz3JH1){:target="_blank"}
2. [Daniel Lett Articles](https://danielilett.com/2023-09-26-tut7-3-intro-to-shader-graph/){:target="_blank"}
3. [Game Dev Bill Video](https://www.youtube.com/watch?v=FLVNfBQgeQc){:target="_blank"}

For most stuff, a simple google for the effect that you are attempting + shadergraph will likely surface a tutorial on how to do that thing. Try to avoid getting stuck in tutorial jail though! At some point when you feel comfortable, pick an effect you want to do, and try to create it without using any tutorials, only googling for specific nodes or issues you encounter.

---

### Getting Started With Code

So you want to go the code route, in that case...

For starting code resources, I highly recommend these resources:
1. [Freya Holmér's "Shaders for Game Devs" Videos](https://www.youtube.com/playlist?list=PLImQaTpSAdsCnJon-Eir92SZMl7tPBS4Z){:target="_blank"}
2. [Catlike Coding's "Shader Fundamentals" Articles (starting at part 2)](https://catlikecoding.com/unity/tutorials/rendering/part-2/){:target="_blank"}
3. [Unity's "Writing Your First Shader in Unity" Videos](https://www.youtube.com/watch?v=zCkC5e_Pkz4&list=PLX2vGYjWbI0RS_lkb68ApE2YPcZMC4Ohz&index=1){:target="_blank"}

Freya Holmér's "Shaders for Game Devs" series is in my opinion the absolute best series for getting started on this stuff. Freya Holmér breaks down Unity shaders into an incredibly digestible soup that is easy to drink for a beginner. This series is personally where I started learning. The only drawback is that the series is rather long. The first episode is almost 4 hours, with the full series being almost 11 hours. That being said, you probably don't need more than the first video to get started.

Catlike coding on the other hand is not for the feign of heart. It goes into an extreme amount of depth, which makes it both comprehensive and intimidating. I would recommend using this as an auxiliary resource rather than your primary source of learning.

Unity's "Writing Your First Shader in Unity" is kind of like a speedrun of what is covered in "Shaders for Game Devs". This would be my recommendation if you really want to quickly get into things.

---

### VRChat specific considerations

When making shaders for VRChat there are a few really important limitations to keep in mind.

One huge one is that we can't write c# scripts. Lots of shader tutorials and techniques call for c# scripts that do one thing or another. Sometimes these can be worked around directly in the shader, other times its just something that isn't possible to do in VRChat, or can be done in worlds but not on avatars.

At some point I might do an article with as many workarounds as I can list, but for now, there are two amazing resources that cover some of those workarounds. They also cover some of the more arcane things that we have to do in VRChat to get certain effects. Some of this stuff will not make sense as a brand new beginner, but I highly recommend putting these in your pocket for later:

[Shader-Knowledge](https://github.com/pema99/shader-knowledge/tree/main){:target="_blank"} by Pema99 <br>
[Shadertrixx](https://github.com/cnlohr/shadertrixx){:target="_blank"} by CNLohr <br>

These repos have VRC specific information on how to do screen effects, object tracking, access the depth texture without c#, persist shader data across frames, and more. They are indispensable information when you get to the right point in learning.

---

For now, that will be the end of this article. I hope to expand this further in the future with tips and tricks, but those resources are the core of what you need to get started in my opinion.

