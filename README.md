HTML Code



<!-- Galerie -->
<div class="gallery">
  <img src="img/" alt="Bild 1" />
  <img src="img/" alt="Bild 2" />
  <img src="img/" alt="Bild 3" />
  <img src="img/" alt="Bild 4" />
</div>

<!-- Lightbox-Overlay -->
<div id="lightbox" class="lightbox">
  <button id="prev" class="nav-button prev">&lt;</button>
  <img id="lightbox-img" src="" alt="" />
  <button id="next" class="nav-button next">&gt;</button>
</div>



CSS Code



/* Lightbox-Overlay */
.lightbox {
  display: none;
  position: fixed;
  z-index: 999;
  top: 0; left: 0;
  width: 100%; height: 100%;
  background-color: rgba(0,0,0,0.8);
  align-items: center;
  justify-content: center;
}

/* Vergrößertes Bild im Lightbox */
.lightbox img {
  max-width: 90%;
  max-height: 80%;
}

/* Positioniere die Button’s innerhalb der Lightbox */
.nav-button {
  position: absolute;
  top: 50%;
  transform: translateY(-50%);
  background-color: transparent;
  border: none;
  color: white;
  font-size: 3em;
  cursor: pointer;
  z-index: 1000;
  padding: 10px;
}

/* Links (<) */
.prev {
  left: 20px;
}

/* Rechts (>) */
.next {
  right: 20px;
}



JavaScript Code 



const galleryImages = document.querySelectorAll('.gallery img');
const images = Array.from(galleryImages);
const lightbox = document.getElementById('lightbox');
const lightboxImg = document.getElementById('lightbox-img');

let currentIndex = 0;

// Beim Klick auf ein Bild öffnen
images.forEach((img, index) => {
  img.addEventListener('click', () => {
    showImage(index);
  });
});

// Funktion, um das Bild anzuzeigen
function showImage(index) {
  if (index < 0) {
    index = images.length - 1;
  } else if (index >= images.length) {
    index = 0;
  }
  lightbox.style.display = 'flex';
  lightboxImg.src = images[index].src;
  lightboxImg.alt = images[index].alt;
  currentIndex = index;
}

// Pfeile navigieren
document.getElementById('prev').addEventListener('click', () => {
  showImage(currentIndex - 1);
});

document.getElementById('next').addEventListener('click', () => {
  showImage(currentIndex + 1);
});

// Klick auf Lightbox schließt sie
lightbox.addEventListener('click', () => {
  lightbox.style.display = 'none';
});







