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

<!-- .slide: data-state="layout-has-icon" -->

# Renderers

<div class="card-group">
  <div class="card fragment fade-in-then-semi-out" style="width: 12em">
    <img data-src="images/empty_room.png" class="card-img-top img-fluid" alt="Sample Image">
    <div class="card-body">
      <h3 class="card-title">OnOffRenderer</h3>
      <p class="card-text"><pre><code>
          ./image-renderer render -R onoff
        </pre>
        </code>
      </p>
    </div>
  </div>
  <div class="card-group">
  <div class="card fragment fade-in-then-semi-out" style="width: 12em">
    <img data-src="images/empty_room.png" class="card-img-top img-fluid" alt="Sample Image">
    <div class="card-body">
      <h3 class="card-title">DebugRenderer</h3>
      <p class="card-text"><code>
          ./image-renderer render -R debug
        </code>
      </p>
    </div>
  </div>
  <div class="card fragment fade-in-then-semi-out" style="width: 12em">
    <img data-src="images/empty_room.png" class="card-img-top img-fluid" alt="Sample Image">
    <div class="card-body">
      <h3 class="card-title">FlatRenderer</h3>
      <p class="card-text">
        ```bash
          ./image-renderer render -R flat
        ```
      </p>
    </div>
  </div>
  <div class="card fragment fade-in-then-semi-out" style="width: 12em">
    <img data-src="images/empty_room.png" class="card-img-top img-fluid" alt="Sample Image">
    <div class="card-body">
      <h3 class="card-title">PathTracer</h3>
        ```bash
          ./image-renderer render -R path
        ```
    </div>
  </div>
</div>

---

<!-- .slide: data-state="layout-has-icon" -->

# Shapes

---

<!-- .slide: data-state="layout-background-video" data-background-video="images/materials.mp4" -->
  
# Materials

---

<!-- .slide: data-state="layout-has-icon" -->

# Features

---

<!-- .slide: data-state="layout-background-image" data-background-image="images/antialiasing.gif" -->
