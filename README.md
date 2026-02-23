<!DOCTYPE html>
<html lang="pl">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Moje Portfolio</title>

<link href="https://fonts.googleapis.com/css2?family=Poppins:wght@300;600&display=swap" rel="stylesheet">

<style>
body {
    margin: 0;
    font-family: 'Poppins', sans-serif;
    background: linear-gradient(to bottom, #007BFF, #0056b3);
    color: white;
    overflow-x: hidden;
}

/* Napis */
.title {
    text-align: center;
    font-size: 50px;
    font-weight: 600;
    margin-top: 100px;
    letter-spacing: 3px;
    animation: fadeIn 2s ease;
}

/* Galeria */
.gallery {
    display: flex;
    justify-content: center;
    gap: 40px;
    flex-wrap: wrap;
    margin: 80px 20px;
}

.gallery img {
    width: 300px;
    border-radius: 20px;
    box-shadow: 0 20px 40px rgba(0,0,0,0.3);
    transition: 0.4s ease;
}

.gallery img:hover {
    transform: scale(1.05);
}

/* Gwiazdki */
.star {
    position: fixed;
    top: -10px;
    width: 4px;
    height: 4px;
    background: white;
    border-radius: 50%;
    opacity: 0.8;
    animation: fall linear infinite;
}

@keyframes fall {
    to {
        transform: translateY(100vh);
    }
}

/* Mgła */
.fog {
    position: fixed;
    bottom: 0;
    width: 100%;
    height: 200px;
    background: linear-gradient(to top, white, transparent);
    pointer-events: none;
    opacity: 0;
    transition: 1s;
}

/* Animacja napisu */
@keyframes fadeIn {
    from { opacity: 0; transform: translateY(-20px); }
    to { opacity: 1; transform: translateY(0); }
}
</style>
</head>

<body>

<h1 class="title">MOJE PRACE:</h1>

<div class="gallery">
    <img src="https://i.imgur.com/Nv5LnVS.png" alt="Minecraft skin 1">
    <img src="https://i.imgur.com/DPt0Oio.png" alt="Minecraft skin 2">
    <img src="https://i.imgur.com/Z5uZjkQ.png" alt="Minecraft skin 3">
    <img src="https://i.imgur.com/7xlob6m.png" alt="Minecraft skin 4">
</div>

<div class="fog" id="fog"></div>

<script>
/* Gwiazdki */
function createStar() {
    const star = document.createElement("div");
    star.classList.add("star");
    star.style.left = Math.random() * window.innerWidth + "px";
    star.style.animationDuration = (Math.random() * 3 + 2) + "s";
    document.body.appendChild(star);

    setTimeout(() => {
        star.remove();
    }, 5000);
}

setInterval(createStar, 100);

/* Mgła przy scroll */
window.addEventListener("scroll", function() {
    let scroll = window.scrollY;
    let maxScroll = document.body.scrollHeight - window.innerHeight;
    let opacity = scroll / maxScroll;
    document.getElementById("fog").style.opacity = opacity;
});
</script>

</body>
</html>
