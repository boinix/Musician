<!DOCTYPE html>
<html lang="en">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>PulseBeat Pro</title>

<style>
*{
    margin:0;
    padding:0;
    box-sizing:border-box;
    font-family:Arial, Helvetica, sans-serif;
}

body{
    background:#0f172a;
    color:white;
}

header{
    background:#020617;
    padding:20px;
    text-align:center;
}

header h1{
    color:#22c55e;
}

nav button{
    padding:8px 16px;
    margin:5px;
    border:none;
    border-radius:6px;
    background:#22c55e;
    color:white;
    cursor:pointer;
}

section{
    padding:40px 20px;
}

.blog-container{
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(250px,1fr));
    gap:20px;
}

.post{
    background:#111827;
    padding:20px;
    border-radius:12px;
}

.like-btn{
    margin-top:10px;
    padding:6px 12px;
    border:none;
    background:#ef4444;
    color:white;
    border-radius:6px;
    cursor:pointer;
}

/* MUSIC PLAYER */
.player{
    background:#111827;
    padding:20px;
    border-radius:12px;
    text-align:center;
    max-width:500px;
    margin:auto;
}

.player button{
    margin-top:10px;
    padding:8px 16px;
}

/* ARTISTS */
.artist-grid{
    display:grid;
    grid-template-columns:repeat(auto-fit,minmax(200px,1fr));
    gap:20px;
}

.artist{
    background:#111827;
    padding:15px;
    border-radius:10px;
    text-align:center;
}

/* ADMIN */
.admin{
    background:#020617;
    padding:20px;
    border-radius:12px;
    max-width:600px;
    margin:auto;
}

.admin input, .admin textarea{
    width:100%;
    padding:8px;
    margin:6px 0;
    border-radius:6px;
    border:none;
}

footer{
    text-align:center;
    padding:20px;
    background:#020617;
}
</style>
</head>
<body>

<header>
    <h1>🎧 PulseBeat Pro</h1>
    <nav>
        <button onclick="scrollToSection('posts')">Blog</button>
        <button onclick="scrollToSection('player')">Player</button>
        <button onclick="scrollToSection('artists')">Artists</button>
        <button onclick="scrollToSection('admin')">Admin</button>
    </nav>
</header>

<!-- BLOG POSTS -->
<section id="posts">
<h2>📰 Latest Posts</h2>
<div class="blog-container" id="blogContainer">

<div class="post">
<h3>🔥 Afrobeats Taking Over</h3>
<p>The global rise of Afrobeats continues in 2026.</p>
<button class="like-btn" onclick="likePost(this)">❤️ Like (<span>0</span>)</button>
</div>

</div>
</section>

<!-- MUSIC PLAYER -->
<section id="player">
<h2>🎵 Music Player</h2>

<div class="player">
<h3 id="nowPlaying">No song selected</h3>

<audio id="audioPlayer" controls style="width:100%; margin-top:10px;">
    Your browser does not support audio.
</audio>

<button onclick="playSample()">▶ Load Sample Track</button>
</div>
</section>

<!-- ARTISTS -->
<section id="artists">
<h2>🎤 Featured Artists</h2>

<div class="artist-grid" id="artistGrid">

<div class="artist">
<h3>Burna Boy</h3>
<p>Afrofusion superstar</p>
</div>

<div class="artist">
<h3>Tems</h3>
<p>Global soulful voice</p>
</div>

<div class="artist">
<h3>Rema</h3>
<p>Young Afrobeats hitmaker</p>
</div>

</div>
</section>

<!-- ADMIN DASHBOARD -->
<section id="admin">
<h2>⚙️ Admin Dashboard</h2>

<div class="admin">

<h3>Add Blog Post</h3>
<input type="text" id="postTitle" placeholder="Post title">
<textarea id="postContent" placeholder="Post content"></textarea>
<button onclick="addPost()">Add Post</button>

<hr style="margin:20px 0;">

<h3>Add Song to Player</h3>
<input type="text" id="songName" placeholder="Song name">
<input type="text" id="songUrl" placeholder="MP3 URL">
<button onclick="loadCustomSong()">Load Song</button>

</div>
</section>

<footer>
<p>© 2026 PulseBeat Pro</p>
</footer>

<script>
// LIKE BUTTON
function likePost(btn){
    let span = btn.querySelector("span");
    span.innerText = parseInt(span.innerText) + 1;
}

// SCROLL
function scrollToSection(id){
    document.getElementById(id).scrollIntoView({behavior:"smooth"});
}

// SAMPLE TRACK
function playSample(){
    const player = document.getElementById("audioPlayer");
    player.src = "https://www.soundhelix.com/examples/mp3/SoundHelix-Song-1.mp3";
    document.getElementById("nowPlaying").innerText = "Now Playing: Sample Track";
    player.play();
}

// ADD BLOG POST
function addPost(){
    const title = document.getElementById("postTitle").value;
    const content = document.getElementById("postContent").value;

    if(!title || !content) return alert("Fill all fields");

    const container = document.getElementById("blogContainer");

    const post = document.createElement("div");
    post.className = "post";
    post.innerHTML = `
        <h3>${title}</h3>
        <p>${content}</p>
        <button class="like-btn" onclick="likePost(this)">❤️ Like (<span>0</span>)</button>
    `;

    container.prepend(post);
}

// LOAD CUSTOM SONG
function loadCustomSong(){
    const name = document.getElementById("songName").value;
    const url = document.getElementById("songUrl").value;

    if(!name || !url) return alert("Enter song details");

    const player = document.getElementById("audioPlayer");
    player.src = url;
    document.getElementById("nowPlaying").innerText = "Now Playing: " + name;
    player.play();
}
</script>

</body>
</html>
