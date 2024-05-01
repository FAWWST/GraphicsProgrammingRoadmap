# My Computer Graphics Programming Roadmap
This project's sole purpose is for me to remind myself of what I need to do in order to become a graphics engineer. If you plan to use this for yourself please take some time to read the sections of each stage in this graphics programming roadmap, to make sure it fits with what you want to do! ~~I might also make the same roadmap on my [Website](https://j-2k.github.io) WIP.~~

***VERY IMPORTANT NOTE! Since this repository is gaining some stars, I feel the need to address the fact that this roadmap is how I plan to venture through graphics programming AS A LEARNER, I AM NOT an already established expert in the field! So for this reason you might actually prefer this over other roadmaps as we are both learners(?)! Anyways these graphics roadmaps are pretty much very close/the same.***

Finally, if I make a spelling/grammar mistake feel free to make a pull request.

**Alternative really good graphics developer roadmap:**
- https://github.com/prographon/graphics-developer-roadmap

<br>

**General game programming roadmap with many additional specializations (graphics, multiplayer, etc):**
- https://github.com/miloyip/game-programmer  
- https://roadmap.sh/game-developer

# Contents
0. [Roadmap Start & Graphics Advice](#resources0) 
1. [Math & C++](#m&c1)
2. [Raytracing](#raytracing2)
3. [Software Renderer](#rasterizer3)
4. [Graphics Specialization](#gfxspec4)
5. [Diving Deep](#dd5)
6. [Miscellaneous Notes](#mn6)

## My progress & chosen resources for graphics! (You can skip this part!)
#### (in brackets will mark a resource I chose to follow & learn with)
Emoji Keys = ✔️ Completed, ⌛ In Progress, ❌ Not Started
1. Write a software raytracer. ✔️ (Cherno Raytracing Series)  
2. Write a software rasterizer. ✔️ (SSloy Tiny rasterizer, 90% Done)  
3. Write a Hello World Triangle. ❌ (Use a graphics specialization!)  
4. Create a project with the Graphics API of choice (OpenGL, Vulkan, or DX12) & Render 1 Mesh with lighting. ❌  

#### By here we are done technically, & now we just have to be passionate & make something or explore other topics such as:  
- PBR (Physically Based Rendering).   
- PPFX (Post Processing Effects like AO (Ambient Occlusion)).  
- Shaders (Ray-marching fun or Fast Fourier transforms for insane water).  
- This can go on forever but by here we can do whatever as long as we are learning, I personally, will have my next steps below.  

#### Fun Section (How I will be continuing)  
5. Create a graphics-focused Minecraft Sim with any Graphics API.  
6. [Extras] Extend the Minecraft Sim to feature the following/any:  
+ Lighting & Water Shader
+ Any Post Processing Effects (Motion blur / Ambient Occlusion / Depth of Field / Bloom / etc.)
+ Multithreading / GPU-Acceleration <br>

<strong><i>Example of an extremely good [Minecraft Sim](https://www.youtube.com/watch?v=M98Th82wC7c) by [Danol](https://github.com/CZDanol)</i></strong>

# <a name="resources0">Graphics Roadmap</a>

**Prerequisite Note:** 
- **If you already know C++ & the math required for graphics, skip to [section 2](#raytracing2), if you don't continue below.**  
- Firstly, *Learn the Math it's the one and only thing important, especially when it comes to graphics programming. Even more so than C++.* Learn it to the point where you can understand almost exactly what is happening, because if you do, you will have an easier time in everything, from problem-solving to debugging, & etc, especially in the future.

*If you are not interested in my personal advice before starting graphics engineering (I suggest you continue reading since I am a learner like you!), skip to the graphics advice of professionals by clicking [here](ga0) or start the graphics pre-requisites section by clicking [here](m&c1).*

---

**My personal & honest advice as a learner to new comers!** 
  
- Even though I mentioned learn math, I mean seriously take math to the next level. Additonally, slowly try to learn some math notation when you are bored, since graphics concepts (especially on wikipedia) are mostly shown in ugly and scary math symbols. Example: Do you know what sigma or product do & what they look like? What does the cross product and dot product do/look like? Integrals??? Rendering equation?!?!? What the fuck is Calculus??? 🗣🗣🗣🔥🔥🔥

---

Jokes aside, here are some answers to the previous questions:

$$\LARGE \sum_{sigma}^{im} | \prod_{product}^{im} | \int_{integral}^{im}$$

$$\LARGE Rendering \ Equation\Rightarrow  L_o(\mathbf{x}, \omega_o) = L_e(\mathbf{x}, \omega_o) + \int_\Omega f_r(\mathbf{x}, \omega_i, \omega_o) L_i(\mathbf{x}, \omega_i) (\omega_i \cdot \mathbf{n}) \, d\omega_i$$

---

*An example of what you will see on wikipedia! (Literally STOLEN from wikipedia btw!)*  
Try to guess what this is if you have done some game development previously! Spoilers below!  
<details>
  <summary>Click here to reveal the answer!</summary>
  Rotation Matrix! Rotating around Z then Y then X!
</details>

$$ \LARGE
R = R_{z}(\gamma) \, R_{y}(\beta) \, R_{x}(\alpha) =
\begin{bmatrix}
    \cos \gamma & -\sin \gamma & 0 \\
    \sin \gamma & \cos \gamma & 0 \\
    0 & 0 & 1 \\
\end{bmatrix}
\begin{bmatrix}
    \cos \beta & 0 & \sin \beta \\
    0 & 1 & 0 \\
    -\sin \beta & 0 & \cos \beta \\
\end{bmatrix}
\begin{bmatrix}
    1 & 0 & 0 \\
    0 & \cos \alpha & -\sin \alpha \\
    0 & \sin \alpha & \cos \alpha \\
\end{bmatrix} $$

$$ \LARGE
= \begin{bmatrix}
    \cos \beta \cos \gamma & \sin \alpha \sin \beta \cos \gamma - \cos \alpha \sin \gamma & \cos \alpha \sin \beta \cos \gamma + \sin \alpha \sin \gamma \\
    \cos \beta \sin \gamma & \sin \alpha \sin \beta \sin \gamma + \cos \alpha \cos \gamma & \cos \alpha \sin \beta \sin \gamma - \sin \alpha \cos \gamma \\
    -\sin \beta & \sin \alpha \cos \beta & \cos \alpha \cos \beta \\
\end{bmatrix} 
$$

---

*An example of Sigma being used, in a VERY popular math operation! (Literally STOLEN from Google btw!)*  
Again! Try to guess what this formula is being used in! Spoilers below!  

<details>
  <summary>Click here to reveal the answer!</summary>
  Dot Product! $$\LARGE\mathbf{a} \cdot \mathbf{b} = \sum_{i=1}^{n} a_i b_i $$
</details>

$$ \LARGE ? = \sum_{i=1}^{n} a_i b_i $$

---

***START OF THE GRAPHICS ROADMAP, THE ORDER IS IMPORTANT & IT'S OKAY TO DEVIATE BUT NOT TOO FAR FROM EACH INDEX.***

#### <a name="ga0">0. Graphics Advice</a>
*You can skip this as I list my resources in order according to many sources when it comes to learning CG*
- [Beginner Computer Graphics Starter Guide](https://erkaman.github.io/posts/beginner_computer_graphics.html) Erkaman's guide on starting Computer Graphics.
- [Graphics Programming Github Page](https://graphics-programming.org/resources/) Made up from people of the Graphics Programming Discord Server.

#### <a name="m&c1">1. Math & C++ (Prerequisite Resources!)</a>
Learn these 3 topics > Linear Algebra, Trigonometry, C++.
- [Immersive Mathemathics](https://immersivemath.com/ila/index.html#), Learn math needed through a website that shows mathematics in an immersive 3D environment.
- [Essence of linear algebra](https://www.youtube.com/playlist?list=PLZHQObOWTQDPD3MizzM2xVFitgF8hE_ab) Learning Linear Transformations, & see how they move in space via video (3blue1brown).
- [Cherno C++ Series](https://www.youtube.com/playlist?list=PLlrATfBNZ98dudnM48yfGUldqGD0S4FFb) Chernos C++ Series for the pre-requisite section (Video Format)
- [Learn CPP Website](https://www.learncpp.com) Learn C++ website, literally everything covered (Reading Format)
- [Scratchapixel](https://scratchapixel.com) You can learn all math prerequisites in here (Geometry Section) & other computer graphics topics!

#### <a name="raytracing2">2. Raytracing</a>
First graphics project will be simple raytracing! **(Basically 1 math formula, understand it!)**   
All resources below will cover the math & implementation, pick your poison.  
- [Cherno Raytracing Series](https://www.youtube.com/playlist?list=PLlrATfBNZ98edc5GshdBtREv5asFW3yXl) (REAL TIME RAYTRACER) Cherno Raytracing Guide that im following.
- [Raytracing in 1 Weekend](https://raytracing.github.io) (OFFLINE RAYTRACER) Infamous book for learning raytracing.
- [Scratchapixel, Intro to Raytracing](https://scratchapixel.com/lessons/3d-basic-rendering/introduction-to-ray-tracing/how-does-it-work.html) (OFFLINE RAYTRACER) Scratchapixel raytracer, but personally, I would go with 1 of the other ones above for raytracing. You should also go over scratch a pixels math lessons though for real graphics programming!
- [Ssloy Tiny Raytracer](https://github.com/ssloy/tinyraytracer/wiki/Part-1:-understandable-raytracing) (OFFLINE RAYTRACER) SSloy Raytracer (again id personally go with 1 of the top 2 in this section, you will do ssloy renderer instead which is much more important!).

#### <a name="rasterizer3">3. Software Renderer (Rasterizer)</a>
IMPORTANT! THIS IS SKIPPABLE BUT READ ALL BEFORE DECIDING > You can skip this section & dive into a graphics API if you want, but the point of this section is to teach you LITERALLY what a graphics specialization (API) is doing for you, which means you will do everything that the graphics specialization does for you in the back, this will help you understand most of the things for the future when you start & pick a graphics API to use.  
- [ssloy](https://github.com/ssloy/tinyrenderer/wiki/Lesson-0:-getting-started) Ssloy Tiny Renderer, I personally am following this, but if you have another software rasterizer tutorial you are free to choose others ofc, just make sure its good! I just chose this because I see tons of other graphics engineers suggest this!

#### <a name="gfxspec4">4. Pick your Graphics Specialization!</a>
**Welcome to Hell! Pick your choice of pain carefully! (not really, they all give pain)**  
You mainly have 2 choices, either go to the deep end (Vulkan, DX12) if you have prior experience (or if your a beginner with a death wish like me💃), or if you want to stay safe go with OpenGL. Personally, I have heard mixed opinions at this stage people argue that learning OpenGL is bad nowadays even if they are a "beginner" & should always go to DX 11 at the minimum or just do Vulkan or DX12. & Vice Versa. IMO, whatever you pick, understand it! please, understand it properly, especially the math & what a graphics function does for you in the back is very important!  
Quick difficulity tier list: [Hard] Vulkan => DX12 > DX11 > OpenGL ["Easy"] no graphics api is "easy" 😉    
LEARN WHAT ALL GFX API'S DO IN COMMON! THE CONCEPT BETWEEN THEM IS SIMILAR BUT YOU MUST UNDERSTAND I CAN'T STRESS THIS ENOUGH.  

#### Vulkan
- [Vulkan Game Engine Tutorials](https://www.youtube.com/playlist?list=PL8327DO66nu9qYVKLDmdLW_84-yE4auCR) Learn Vulkan from Brendan Galea, *THIS RESOURCE IS INSANELY INFORMATIVE & HELPFUL THIS SERIES HELPED ME A TON* (Optional choice to OpenGL with the benefit that its more updated & its a better graphics specialization, however is difficult for beginners, or just dive in & be a gigachad)
- [Vulkan Tutorial](https://vulkan-tutorial.com/) Most popular Vulkan Tutorial page.  
(No entry for DX12, because personally I would go with vlk than dx12, if you want dx12 just google should be easy to find a decent one)

#### DX11
- [LearnDXD11](https://graphicsprogramming.github.io/learnd3d11/1-introduction/1-1-getting-started/1-1-3-hello-triangle/) Learn DirectX11, from the people @ the graphics programming discord server.

#### OpenGL
- [Learnopengl](https://learnopengl.com/) The most popular openGL resource out there.
- [Learning Modern 3D Graphics Programming](https://paroj.github.io/gltut/index.html) Style is different & uses openGL but the point is to teach you how to program graphics not use OpenGL! not fixed learning & rather more programming read the about for more info.
- [Scratchapixel](https://scratchapixel.com) Learn almost everything you need in the computer graphics domain, this uses OpenGL.
- [Cherno OpenGL Series](https://www.youtube.com/playlist?list=PLlrATfBNZ98foTJPJ_Ev03o2oq3-GGOS2) Learn OpenGL from Chernos OpenGL Series (Probably really old but whatever)

#### External notes:
Even though some of these resources are popular dosn't mean they are all "good" & "correct", a popular example of a flawed implementation of a PPFX like bloom for example in a popular resource like learn opengl is actually inaccurate & straight up wrong. Watch [Cherno's Bloom Video](https://www.youtube.com/watch?v=tI70-HIc5ro) where he talks about this.  
So why am I writing this? Because its also important to take small breaks & watch some good graphics programmers do stuff for fun while educating you on the side about popular gfx topics to keep you hooked in & keep you interested! I listed some of my favourite graphics people below with their specializations!
- [Cherno](https://www.youtube.com/@TheCherno) Full on Graphics Engineering youtube channel.
- [Acerola](https://www.youtube.com/@Acerola_t) Shader Specialized (specifically post processing/screen based shaders) youtube channel.

#### <a name="dd5"> 5. Do fun stuff now! Dive Deeper! Or learn more! (Random Resources) </a>
Here the list will deviate, & you have to do whatever you enjoy and essentially use whatever API you used before & maybe make something for fun, or dive deeper in specific areas for example getting better at shaders (raymarching, FFT water, post processing shaders, GPU instancing etc.). 

#### Shaders
- [Catlike Coding](https://catlikecoding.com/unity/tutorials/) Probably the best shader tutorials out there easily. It's a crime that I forgot to put this in.
- [Art of Code Youtube Channel](https://www.youtube.com/@TheArtofCodeIsCool) For learning & Writing better shaders using GLSL on Shadertoy (Easily transferable to HLSL/CG).
- [Kishimisu Youtube Channel](https://www.youtube.com/@kishimisu) Mainly this is for people that are BRAND-NEW to shaders & want to learn in video rather than text, Kishi has great quality videos.

#### Dive Deep into Computer Graphics (Advanced)
- [Infamous PBR Book](https://pbr-book.org/) Physically Based Rendering Book
- [Real Time Rendering](https://realtimerendering.com/) Core book for Real-Time Graphics

#### Extras
- [Big Randy Resources (Not just Graphics)](https://github.com/bigrando420/resources/wiki) Big Randy's resources are actually pretty good too.
- [DirectX Tutorial](http://www.directxtutorial.com/Lesson.aspx?lessonid=11-4-1) Seem's a little old but still pretty good, can be subbed out for LearnDXD11, your choice.
- [Brian Will OpenGL Rants](https://www.youtube.com/watch?v=hPmEyAXdOdY&list=PLIbUZ3URbL0ESKHrvzXuHjrcLi7gxhBby) I personally like Brian, I think he does decent videos (some of it is really old but the concept is still valid). IMO I wouldn't follow it as a real tutorial but rather watch the video and try to understand the concept because hes explanations are whats important I feel like not the implementation as much if that makes sense.

##### <a name="mn6">Miscellaneous Notes</a>
- [MathIsFun.com Trigonometry](https://www.mathsisfun.com/algebra/trigonometry.html) For Learning Trigonometry & can literally be used to learn everything in the prereqs & other math related topics that come later on in graphics.
- Getting A Masters Degree in Computer Science with the final project (the thesis or dissertation whatever the place you choose calls it) based on something related to graphics. This note is for myself, because it sounds fun might do it. Ideas for final project could be a Minecraft Sim / a good raytracer / Voxel Engine & etc.<br>

<strong><i>A very nice example of a [voxel engine](https://www.youtube.com/watch?v=8ptH79R53c0) by [John Lin](https://github.com/Lin20)</i></strong>


##### Life Advice & Closing Notes
Will probably add more stuff here, but I have to mention it's extremely important to find out what you want to do in life, specifically if it's graphics then what with graphics?<br>
Games Industry? Positions that exist are:<br>
- Technical Artist/Shader Developer (Maybe even VFX position, dealing with particles & shaders).
- Graphics Engineer / Engine & Graphics Developer. <br>
(These are the main positions I look for, many other positions also exist just check the image below by hitmarker.)
- Possibly even a research based position if you get really good & can land a place @ NVIDIA. <br>
Adding this image for you to see more positions that a graphics dev can also work on alongside pursuing graphics. This image was not made by me, credits go to people @ [hitmarker.net](https://hitmarker.net/).
<img src="gameprofessions-byhitmarker.png"  width="100%" height="100%">

Movies Industry? I don't really know/care about them, so I won't talk about it here. But I heard there are opportunities over there also for graphics people.
