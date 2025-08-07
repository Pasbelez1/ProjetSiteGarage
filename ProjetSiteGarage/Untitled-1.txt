<!-- Lightbox HTML -->
<div id="lightbox" style="display:none;">
  <span id="lightbox-close">&times;</span>
  <img id="lightbox-img" src="" alt="Agrandissement" />
</div>

<script>
  // Slider JS (déjà présent)
  const slides = document.querySelectorAll('.slide');
  const prevBtn = document.querySelector('.slider-btn.prev');
  const nextBtn = document.querySelector('.slider-btn.next');
  let current = 0;

  function showSlide(index) {
    slides.forEach((slide, i) => {
      slide.classList.toggle('active', i === index);
    });
  }

  prevBtn.addEventListener('click', () => {
    current = (current === 0) ? slides.length - 1 : current - 1;
    showSlide(current);
  });

  nextBtn.addEventListener('click', () => {
    current = (current === slides.length - 1) ? 0 : current + 1;
    showSlide(current);
  });

  showSlide(current);

  // Lightbox JS
  const lightbox = document.getElementById('lightbox');
  const lightboxImg = document.getElementById('lightbox-img');
  const lightboxClose = document.getElementById('lightbox-close');

  slides.forEach(slide => {
    slide.style.cursor = "zoom-in";
    slide.addEventListener('click', () => {
      lightboxImg.src = slide.src;
      lightbox.style.display = "flex";
    });
  });

  lightboxClose.addEventListener('click', () => {
    lightbox.style.display = "none";
    lightboxImg.src = "";
  });

  // Fermer la lightbox en cliquant en dehors de l'image
  lightbox.addEventListener('click', (e) => {
    if (e.target === lightbox) {
      lightbox.style.display = "none";
      lightboxImg.src = "";
    }
  });
</script>