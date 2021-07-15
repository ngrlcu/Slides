<!-- .slide: data-state="layout-title"  -->

# IMAGE RENDERER

## Physically based raytracer

![Operating Systems](https://img.shields.io/badge/OS-Linux%20%7C%20MacOS%20%7C%20Windows-lightgrey)
![License](https://img.shields.io/github/license/teozec/image-renderer)
![Top Language](https://img.shields.io/github/languages/top/teozec/image-renderer)
![Version](https://img.shields.io/github/v/release/teozec/image-renderer)
![Size](https://img.shields.io/github/repo-size/teozec/image-renderer)

<p>By Luca Nigro & Matteo Zeccoli Marazzini</p>

<p>A C++ software that generates photo-realistic images.</p>
  
<p class="no-fragment btn-group" role="group" aria-label="Basic example">
<a class="btn btn-lg btn-warning text-dark" href="https://github.com/teozec/image-renderer">Github Repo</a>
</p>

---

# Getting Started

```bash [1|2-5|6]
git clone git@github.com:teozec/image-renderer.git
mkdir build
cd build
cmake ..
make
source ../tools/bash-completion.bash
```

And you are good to go!

---

# Renderers

<div class="card-group">
  <div class="card fragment fade-in-then-semi-out" style="width: 12em">
    <img data-src="images/empty_room.png" class="card-img-top img-fluid" alt="Sample Image">
    <div class="card-body">
      <h3 class="card-title">OnOffRenderer</h3>
      <p class="card-text">
          <code>
           [...] -R onoff
          </code>
      </p>
    </div>
  </div>
  <div class="card-group">
  <div class="card fragment fade-in-then-semi-out" style="width: 12em">
    <img data-src="images/empty_room.png" class="card-img-top img-fluid" alt="Sample Image">
    <div class="card-body">
      <h3 class="card-title">DebugRenderer</h3>
      <p class="card-text">
          <code>
            [...] -R debug
          </code>
      </p>
    </div>
  </div>
  <div class="card fragment fade-in-then-semi-out" style="width: 12em">
    <img data-src="images/empty_room.png" class="card-img-top img-fluid" alt="Sample Image">
    <div class="card-body">
      <h3 class="card-title">FlatRenderer</h3>
      <p class="card-text">
          <code>
            [...] -R flat
          </code>
      </p>
    </div>
  </div>
  <div class="card fragment fade-in-then-semi-out" style="width: 12em">
    <img data-src="images/empty_room.png" class="card-img-top img-fluid" alt="Sample Image">
    <div class="card-body">
      <h3 class="card-title">PathTracer</h3>
      <p class="card-text">
          <code>
            [...] -R path
          </code>
    </div>
  </div>
</div>

---

# Help

```bash [1|3-13|15-20]
Usage: ./image-renderer render [options] <inputfile>

General options:
	-h, --help							Print this message.
	-q, --quiet							Do not show rendering progress.
	-y, --dryRun							Parse scenefile, but do not render image. Useful to check correctness of scenes.
	-f <variable1:value1,variable2:value2,...>, --float=<...>	Define float variables to be used in the scenefile.
	-w <value>, --width=<value>					Width of the final image (default 640).
	-h <value>, --height=<value>					Height of the final image (default 480).
	-a <value>, --aspectRatio=<value>				Aspect ratio of the final image (default width/height).
	-A <value>, --antialiasing=<value>				Number of samples per single pixel (default 0). Must be a perfect square, e.g. 4.
	-R <renderer>, --renderer=<renderer>				Rendering algorithm (default 'path'). Can be 'path', 'debug', 'onoff', 'flat'.
	-o <string>, --outfile=<string>					Filename of output image (default input filename with '.pfm' extension).

Options for 'path' rendering algorithm:
	-s <value>, --seed=<value>					Random number generator seed (default 42).
	-i <value>, --initSeq=<value>					Random number generator init sequence (default 54).
	-n <value>, --nRays=<value>					Number of rays started at each intersection (default 3).
	-d <value>, --depth=<value>					Max ray depth (default 4).
	-r <value>, --roulette=<value>					Ray depth to start Russian roulette (default 3).
```

---

# Shapes

<div class="card-group">
  <div class="card fragment fade-in-then-semi-out" style="width: 8em">
    <img data-src="images/shape_box.gif" class="card-img-top img-fluid" alt="Sample Image">
    <div class="card-body">
      <h3 class="card-title">Box</h3>
    </div>
  </div>
</div>
<div class="card-group">
  <div class="card fragment fade-in-then-semi-out" style="width: 8em">
    <img data-src="images/shape_plane.gif" class="card-img-top img-fluid" alt="Sample Image">
    <div class="card-body">
      <h3 class="card-title">Plane</h3>
    </div>
  </div>
</div>
<div class="card-group">
  <div class="card fragment fade-in-then-semi-out" style="width: 8em">
    <img data-src="images/shape_sphere.gif" class="card-img-top img-fluid" alt="Sample Image">
    <div class="card-body">
      <h3 class="card-title">Sphere</h3>
    </div>
  </div>
</div>
<div class="card-group">
  <div class="card fragment fade-in-then-semi-out" style="width: 8em">
    <img data-src="images/shape_union.gif" class="card-img-top img-fluid" alt="Sample Image">
    <div class="card-body">
      <h3 class="card-title">CSGUnion</h3>
    </div>
  </div>
</div>
<div class="card-group">
  <div class="card fragment fade-in-then-semi-out" style="width: 8em">
    <img data-src="images/shape_difference.gif" class="card-img-top img-fluid" alt="Sample Image">
    <div class="card-body">
      <h3 class="card-title">CSGDifference</h3>
    </div>
  </div>
</div>
<div class="card-group">
  <div class="card fragment fade-in-then-semi-out" style="width: 8em">
    <img data-src="images/shape_intersection.gif" class="card-img-top img-fluid" alt="Sample Image">
    <div class="card-body">
      <h3 class="card-title">CSGIntersection</h3>
    </div>
  </div>
</div>
---

<!-- .slide: data-state="layout-background-video" data-background-video="images/materials.mp4" -->
  
# Materials

---

# Features

---

<!-- .slide: data-state="layout-background-image" data-background-image="images/antialiasing.gif" -->
