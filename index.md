---
#
# By default, content added below the "---" mark will appear in the home page
# between the top bar and the list of recent posts.
# To change the home page layout, edit the _layouts/home.html file.
# See: https://jekyllrb.com/docs/themes/#overriding-theme-defaults
#
layout: home
---

![HerCloudLogo](/assets/Herlogo.png){:.centered.home-logo}

<div class="home-intro">
  <h1>Welcome to Her Cloud</h1>
  <p>Her Cloud is a student-led organization supporting women and nonbinary students in information technology and related fields. We create a supportive, inclusive environment where members grow technical skills, gain career insights, and build meaningful connections.</p>
  <p>Whether you're exploring your first line of code or preparing for internships and full-time roles, you belong here. Join us to learn, collaborate, and thrive in tech.</p>
</div>

<div class="photo-carousel" id="photoCarousel"
     data-images='[
       "/images/gallery/unnamed.jpg",
       "/images/gallery/unnamed-1.jpg",
       "/images/gallery/unnamed-2.jpg",
       "/images/gallery/screenshot-2025-10-31-10-44-45.png"
     ]'>
  <div class="carousel-viewport">
    <div class="carousel-track"></div>
  </div>
  <button class="carousel-btn carousel-prev" aria-label="Previous">&#10094;</button>
  <button class="carousel-btn carousel-next" aria-label="Next">&#10095;</button>
  <div class="carousel-dots" aria-label="Carousel pagination"></div>
</div>

<script>
(function() {
  const root = document.getElementById('photoCarousel');
  if (!root) return;
  const images = JSON.parse(root.getAttribute('data-images') || '[]');
  const track = root.querySelector('.carousel-track');
  const dots = root.querySelector('.carousel-dots');
  const prev = root.querySelector('.carousel-prev');
  const next = root.querySelector('.carousel-next');
  let index = 0;
  let timer;

  function render() {
    track.innerHTML = '';
    images.forEach((src, i) => {
      const slide = document.createElement('div');
      slide.className = 'carousel-slide' + (i === index ? ' is-active' : '');
      const img = document.createElement('img');
      img.loading = 'lazy';
      img.decoding = 'async';
      img.src = src;
      img.alt = 'Her Cloud photo ' + (i + 1);
      slide.appendChild(img);
      track.appendChild(slide);
    });

    dots.innerHTML = '';
    images.forEach((_, i) => {
      const dot = document.createElement('button');
      dot.className = 'carousel-dot' + (i === index ? ' is-active' : '');
      dot.setAttribute('aria-label', 'Go to slide ' + (i + 1));
      dot.addEventListener('click', () => goTo(i));
      dots.appendChild(dot);
    });
  }

  function goTo(i) {
    index = (i + images.length) % images.length;
    root.querySelectorAll('.carousel-slide').forEach((el, j) => {
      el.classList.toggle('is-active', j === index);
    });
    root.querySelectorAll('.carousel-dot').forEach((el, j) => {
      el.classList.toggle('is-active', j === index);
    });
    restartTimer();
  }

  function nextSlide() { goTo(index + 1); }
  function prevSlide() { goTo(index - 1); }

  function startTimer() { timer = setInterval(nextSlide, 4000); }
  function stopTimer() { if (timer) clearInterval(timer); }
  function restartTimer() { stopTimer(); startTimer(); }

  prev.addEventListener('click', prevSlide);
  next.addEventListener('click', nextSlide);
  root.addEventListener('mouseenter', stopTimer);
  root.addEventListener('mouseleave', startTimer);

  if (images.length > 0) {
    render();
    startTimer();
  }
})();
</script>
