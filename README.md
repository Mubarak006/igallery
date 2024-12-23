# Ex.08 Design of Interactive Image Gallery
## Date: 23-12-20204

## AIM:
To design a web application for an inteactive image gallery with minimum five images.

## DESIGN STEPS:

### Step 1:
Clone the github repository and create Django admin interface.

### Step 2:
Change settings.py file to allow request from all hosts.

### Step 3:
Use CSS for positioning and styling.

### Step 4:
Write JavaScript program for implementing interactivity.

### Step 5:
Validate the HTML and CSS code.

### Step 6:
Publish the website in the given URL.

## PROGRAM :
```
igallery.html

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Image Gallery</title>
    <link rel="stylesheet" href="style.css">
</head>
<body>

    </div>
    <div class="banner">
        <div class="slider" style="--quantity: 10">
            <div class="item" style="--position: 1"><img src="pokemon1.jpeg" alt=""></div>
            <div class="item" style="--position: 2"><img src="pokemon2.jpeg" alt=""></div>
            <div class="item" style="--position: 3"><img src="pokemon3.jpeg" alt=""></div>
            <div class="item" style="--position: 4"><img src="pokemon4.jpeg" alt=""></div>
            <div class="item" style="--position: 5"><img src="pokemon5.jpeg" alt=""></div>
            <div class="item" style="--position: 6"><img src="pokemon6.jpeg" alt=""></div>
            <div class="item" style="--position: 7"><img src="pokemon7.jpeg" alt=""></div>
            <div class="item" style="--position: 8"><img src="pokemon8.jpeg" alt=""></div>
            <div class="item" style="--position: 9"><img src="pokemon9.jpeg" alt=""></div>
            <div class="item" style="--position: 10"><img src="pokemon10.jpeg"  alt=""></div>
        </div>
        <div class="content">
            <h1 data-content="Attractive Image Gallery">
                Ittractive Image Gallery
            </h1>

            <div class="author">
                <h2>Mubarak R</h2>
                <p><b>24900694</b></p>
                <p>Interactive Image Gallery</p>
            
            </div>
            <div class="model"></div>
        </div>
    </div>
    <script>
    document.addEventListener('DOMContentLoaded', function () {
       
        const allPhotos = document.querySelectorAll('.banner .slider .item img'); // Select all images in the slider
        const modal = document.createElement('div'); // Create modal element dynamically
        const modalImage = document.createElement('img'); // Create image element for modal
        const closeModal = document.createElement('span'); // Create close button for modal
    
        modal.id = 'imageModal';
        modal.classList.add('modal');
        modal.appendChild(closeModal);
        modal.appendChild(modalImage);
        document.body.appendChild(modal);
    
        
        modal.style.position = 'fixed';
        modal.style.zIndex = '1';
        modal.style.left = '0';
        modal.style.top = '0';
        modal.style.width = '100%';
        modal.style.height = '100%';
        modal.style.backgroundColor = 'rgba(0, 0, 0, 0.8)';
        modal.style.display = 'none';
        modalImage.style.display = 'block';
        modalImage.style.margin = 'auto';
        modalImage.style.maxWidth = '90%';
        modalImage.style.maxHeight = '90%';
        closeModal.style.position = 'absolute';
        closeModal.style.top = '15px';
        closeModal.style.right = '35px';
        closeModal.style.color = '#fff';
        closeModal.style.fontSize = '40px';
        closeModal.style.fontWeight = 'bold';
        closeModal.style.cursor = 'pointer';
    
       
        closeModal.textContent = '×';
  
        allPhotos.forEach((img) => {
            img.addEventListener('click', function () {
                modal.style.display = 'flex';
                modalImage.src = this.src;  // Set clicked image to modal
            });
        });
    
        
        closeModal.addEventListener('click', () => {
            modal.style.display = 'none';
        });
    
        
        modal.addEventListener('click', (e) => {
            if (e.target === modal) {
                modal.style.display = 'none';
            }
        });
    
        
        const sliderElement = document.querySelector('.slider');
        let angle = 0;
    
        function rotateSlider() {
            angle += 1; // Rotate 1 degree for each iteration
            sliderElement.style.transform = `perspective(1000px) rotateX(-16deg) rotateY(${angle}deg)`;
        }
    
        setInterval(rotateSlider, 20);
    });
</script>    
    </body>
    </html>

    style.css

    
*{
    margin: 0;
    padding: 0;
    box-sizing: border-box;
}
body{
    background-color: #D2D2D2;
    background-image:
    repeating-linear-gradient(
        to right, transparent 0 100px,
        #25283b22 100px 101px
    ),
    repeating-linear-gradient(
        to bottom, transparent 0 100px,
        #25283b22 100px 101px
    );
}

body::before{
    position: absolute;
    width: min(1400px, 90vw);
    top: 10%;
    left: 50%;
    height: 90%;
    transform: translateX(-50%);
    content: '';
    background-image: url(images/bg.png);
    background-size: 100%;
    background-repeat: no-repeat;
    background-position: top center;
    pointer-events: none;
}
@import url('https://fonts.cdnfonts.com/css/ica-rubrik-black');
@import url('https://fonts.cdnfonts.com/css/poppins');

.banner{
    width: 100%;
    height: 100vh;
    text-align: center;
    overflow: hidden;
    position: relative;
}
.banner .slider{
    position: absolute;
    width: 200px;
    height: 250px;
    top: 10%;
    left: calc(50% - 100px);
    transform-style: preserve-3d;
    transform: perspective(1000px);
    animation: autoRun 20s linear infinite;
    z-index: 2;
}
@keyframes autoRun{
    from{
        transform: perspective(1000px) rotateX(-16deg) rotateY(0deg);
    }to{
        transform: perspective(1000px) rotateX(-16deg) rotateY(360deg);
    }
}

.banner .slider .item{
    position: absolute;
    inset: 0 0 0 0;
    transform: 
        rotateY(calc( (var(--position) - 1) * (360 / var(--quantity)) * 1deg))
        translateZ(550px);
}
.banner .slider .item img{
    width: 100%;
    height: 100%;
    object-fit: cover;
}
.banner .content{
    position: absolute;
    bottom: 0;
    left: 50%;
    transform: translateX(-50%);
    width: min(1400px, 100vw);
    height: max-content;
    padding-bottom: 100px;
    display: flex;
    flex-wrap: wrap;
    justify-content: space-between;
    align-items: center;
    z-index: 1;
}
.banner .content h1{
    font-family: 'ICA Rubrik';
    font-size: 16em;
    line-height: 1em;
    color: #25283B;
    position: relative;
}
.banner .content h1::after{
    position: absolute;
    inset: 0 0 0 0;
    content: attr(data-content);
    z-index: 2;
    -webkit-text-stroke: 2px #d2d2d2;
    color: transparent;
}
.banner .content .author{
    font-family: Poppins;
    text-align: right;
    max-width: 200px;
}
.banner .content h2{
    font-size: 3em;
}
.banner .content .model{
    background-image: url(images/model.png);
    width: 100%;
    height: 75vh;
    position: absolute;
    bottom: 0;
    left: 0;
    background-size: auto 130%;
    background-repeat: no-repeat;
    background-position: top center;
    z-index: 1;
}
@media screen and (max-width: 1023px) {
    .banner .slider{
        width: 160px;
        height: 200px;
        left: calc(50% - 80px);
    }
    .banner .slider .item{
        transform: 
            rotateY(calc( (var(--position) - 1) * (360 / var(--quantity)) * 1deg))
            translateZ(300px);
    }
    .banner .content h1{
        text-align: center;
        width: 100%;
        text-shadow: 0 10px 20px #000;
        font-size: 7em;
    }
    .banner .content .author{
        color: #fff;
        padding: 20px;
        text-shadow: 0 10px 20px #000;
        z-index: 2;
        max-width: unset;
        width: 100%;
        text-align: center;
        padding: 0 30px;
    }
}
@media screen and (max-width: 767px) {
    .banner .slider{
        width: 100px;
        height: 150px;
        left: calc(50% - 50px);
    }
    .banner .slider .item{
        transform: 
            rotateY(calc( (var(--position) - 1) * (360 / var(--quantity)) * 1deg))
            translateZ(180px);
    }
    .banner .content h1{
        font-size: 5em;
    }
}

```

## OUTPUT:
![alt text](<Screenshot (133)-1.png>)
![alt text](<Screenshot (134)-1.png>) 
![alt text](<Screenshot (135)-1.png>)
![alt text](<Screenshot (136)-1.png>) 
![alt text](<Screenshot (137)-1.png>)
![alt text](<Screenshot (138)-1.png>)
## RESULT:
The program for designing an interactive image gallery using HTML, CSS and JavaScript is executed successfully.
