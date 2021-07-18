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

# Basic Usage

```bash
./image-renderer render [options] &lt;inputfile&gt;
```

---

# Example Scene

examples/scene.txt:

``` [1-4|6-10|12-21|23-25]
# With 'float' we can declare variables (a float is expected).
float red(0.5)

[...]

# With 'materials' we can declare (guess what) materials. Each of them includes a BRDF and a pigment.
material sky_material(
	diffuse(uniform(<0.8, 0.1, 1.0>)),    # A diffuse BRDF will reflect rays in random directions.
	uniform(<0.8, 0.8, 1.0>)              # The sky is a light source, so we assign a non-black pigment to it.
)

# Now that we have all our materials, we can define the actual shapes that are in the scene.

[...]

# Let's define the ground with a 'plane'.
# The language is flexible enough to permit spaces before '('
plane (ground_material, translation([0, 0, -1]))

# Finally, the sky is a big 'sphere' of radius 7.5.
sphere(sky_material, scaling([7.5, 7.5, 7.5]))

# Without a 'camera' there is nothing to see!
# You can set the type of camera, the tranformations to apply and the distance from the screen.
camera(perspective, translation([-1, 0, 0]) * rotation_z(angle), 1.0)
```
---
# Renderers

<div class="card-group">
  <div class="card fragment fade-in-then-semi-out" style="width: 12em">
    <img data-src="images/renderer_onoff.png" class="card-img-top img-fluid" alt="Sample Image">
    <div class="card-body">
      <h3 class="card-title">OnOffRenderer</h3>
      <p class="card-text">
          <code>
           [...] -R onoff
          </code>
      </p>
    </div>
  </div>
  <div class="card fragment fade-in-then-semi-out" style="width: 12em">
    <img data-src="images/renderer_debug.png" class="card-img-top img-fluid" alt="Sample Image">
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
    <img data-src="images/renderer_flat.png" class="card-img-top img-fluid" alt="Sample Image">
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
    <img data-src="images/renderer_path.png" class="card-img-top img-fluid" alt="Sample Image">
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

# Advanced Usage

```bash [1|3-13|14-20]
Usage: ./image-renderer render [options] &lt;inputfile&gt;

General options:
	-h, --help                           Print this message.
	-q, --quiet                          Do not show rendering progress.
	-y, --dryRun                         Parse scenefile, but do not render image.
	-w &lt;value&gt;, --width=&lt;value&gt;          Width of the final image (default 640).
	-h &lt;value&gt;, --height=&lt;value&gt;         Height of the final image (default 480).
	-a &lt;value&gt;, --aspectRatio=&lt;value&gt;    Aspect ratio of the final image (default width/height).
	-A &lt;value&gt;, --antialiasing=&lt;value&gt;   Number of samples per single pixel (default 0).
	-R &lt;renderer&gt;, --renderer=&lt;renderer&gt; Rendering algorithm (default 'path').
	-o &lt;string&gt;, --outfile=&lt;string&gt;      Filename of output image.

Options for 'path' rendering algorithm:
	-s &lt;value&gt;, --seed=&lt;value&gt;           Random number generator seed (default 42).
	-i &lt;value&gt;, --initSeq=&lt;value&gt;        Random number generator init sequence (default 54).
	-n &lt;value&gt;, --nRays=&lt;value&gt;          Number of rays started at each intersection (default 3).
	-d &lt;value&gt;, --depth=&lt;value&gt;          Max ray depth (default 4).
	-r &lt;value&gt;, --roulette=&lt;value&gt;       Ray depth to start Russian roulette (default 3).
```

---

# Shapes

<div class="card-group">
  <div class="card fragment fade-in" style="width: 8em">
    <img data-src="images/shape_cube.gif" class="card-img-top img-fluid" alt="Sample Image">
    <div class="card-body">
      <h4 class="card-title">Box</h4>
    </div>
  </div>
  <div class="card fragment fade-in" style="width: 8em">
    <img data-src="images/shape_plane.gif" class="card-img-top img-fluid" alt="Sample Image">
    <div class="card-body">
      <h4 class="card-title">Plane</h4>
    </div>
  </div>
  <div class="card fragment fade-in" style="width: 8em">
    <img data-src="images/shape_sphere.gif" class="card-img-top img-fluid" alt="Sample Image">
    <div class="card-body">
      <h4 class="card-title">Sphere</h4>
    </div>
  </div>
  <div class="card fragment fade-in" style="width: 8em">
    <img data-src="images/shape_union.gif" class="card-img-top img-fluid" alt="Sample Image">
    <div class="card-body">
      <h4 class="card-title">CSG Union</h4>
    </div>
  </div>
  <div class="card fragment fade-in" style="width: 8em">
    <img data-src="images/shape_difference.gif" class="card-img-top img-fluid" alt="Sample Image">
    <div class="card-body">
      <h4 class="card-title">CSG Difference</h4>
    </div>
  </div>
  <div class="card fragment fade-in" style="width: 8em">
    <img data-src="images/shape_intersection.gif" class="card-img-top img-fluid" alt="Sample Image">
    <div class="card-body">
      <h4 class="card-title">CSG Intersection</h4>
    </div>
  </div>
</div>
<div class="card-group">
  <div class="card fragment fade-in" style="width: 6em">
    <img data-src="images/asset_chair.gif" class="card-img-top img-fluid" alt="Sample Image">
    <div class="card-body">
      <h4 class="card-title">Chair</h4>
      <div class="alert alert-danger fragment">
	<p class="card-text">ONLY API</p>
      </div>
    </div>
  </div>
  <div class="card fragment fade-in" style="width: 6em">
    <img data-src="images/asset_dice.gif" class="card-img-top img-fluid" alt="Sample Image">
    <div class="card-body">
      <h4 class="card-title">Dice</h4>
      <div class="alert alert-danger fragment">
        <p class="card-text">ONLY API</p>
      </div>
    </div>
  </div>
</div>
---

<!-- .slide: data-state="layout-background-image" data-background-image="images/materials.gif" -->
  
# Materials



---

# Features

---

<!-- .slide: data-state="layout-background-image" data-background-image="images/antialiasing.gif" -->

---

<!-- .slide: data-state="layout-background-image" data-background-image="images/stack.png" -->

## Stacking

./image-renderer stack [options] &lt;inputfiles&gt;

---

<!-- .slide: data-state="layout-mostly-image" data-background-image="images/pfm2ldr.png" -->

## PFM to LDR converter

./image-renderer pfm2ldr [options] &lt;inputfile&gt;

---

# Some Images

[Here a sort of portfolio]

---

Thanks from [Luca Nigro](https://github.com/ngrlcu) & [Matteo Zeccoli Marazzini](https://github.com/teozec)
<i class="twa twa-beaming-face-with-smiling-eyes"></i>
