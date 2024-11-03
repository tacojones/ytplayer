## YouTube Audio Player

### Overview
This project provides a customizable audio player that uses YouTube videos as the audio source. It supports play, pause, stop functionality, and displays elapsed and total playback time. 

**Key Features**:
- Play, pause, and stop audio control
- Dynamic progress bar with elapsed and total time display
- Customizable CSS and SVG icons for buttons
- Responsive and user-friendly design
- Lightweight and easy to integrate into existing web projects

Here's a suggested README entry about the requirement to include the YouTube IFrame API script for your media player:

---

### Requirements

To ensure the proper functionality of the audio player, you must include the YouTube IFrame Player API in your HTML file. This is essential for controlling the playback of the YouTube videos embedded in the player. 

### How to Include the YouTube IFrame API

Add the following line to your HTML file before your custom JavaScript code that interacts with the API:

```html
<script src="https://www.youtube.com/iframe_api"></script>
```

### Example Usage

Here’s an example of how to set up your HTML:

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>YouTube Audio Player</title>
<style>
.media-player {
    display: flex;
    align-items: center;
    justify-content: center;
    padding: 10px;
    background-color: #01154a40;
    border-radius: 4px;
    width: 100%;
    height: 50px;
    border: 1px solid #01154a99;
    margin-bottom: 3px;
    box-sizing: border-box; /* Ensures padding doesn't affect total width */
}

.media-player button {
    background-color: transparent !important;
    color: #65b2ff50 !important;
    padding: 0;
    border: 0;
    width: 40px;
    height: 40px;
    margin: 0 1px;
    cursor: pointer;
}

.media-player button:hover {
    background-color: transparent !important;
    color: #9af36990 !important;
    border: 0;
    box-shadow: none;
}

/* General styles for the progress bar */
.progress-bar {
    -webkit-appearance: none; /* Removes default styling */
    appearance: none;
    width: 100%; /* Full width */
    height: 1px; /* Height of the progress bar */
    background-color: #01154a00; /* Base track color */
    border-radius: 2px;
    outline: none;
    border: none;
    margin: 0 6px 0 0;
    padding: 1px;
    border: 1px solid #01154a99;
}
/* Progress fill (for Chrome, Safari, Edge) */
.progress-bar::-webkit-slider-runnable-track {
    background-color: transparent; /* Track color */
}

/* Firefox track */
.progress-bar::-moz-range-track {
    background-color: transparent;
    height: 8px; /* Height of the progress bar */
    border-radius: 0px;
}

/* Styling for the filled portion of the bar (WebKit) */
.progress-bar::-webkit-slider-runnable-track {
    background: #65b2ff50; /* Progress color */
}

/* Styling for the thumb (WebKit) */
.progress-bar::-webkit-slider-thumb {
    -webkit-appearance: none;
    appearance: none;
    width: 40px;
    height: 8px;
    background-color: #65b2ff50;
    cursor: pointer;
    border: none;
    border-radius: 2px;
}

/* Firefox thumb */
.progress-bar::-moz-range-thumb {
    width: 40px;
    height: 8px;
    background-color: #65b2ff50;
    cursor: pointer;
    border: none;
    border-radius: 2px;
    box-shadow: 0 0 3px #65b2ff20;
}

/* Firefox thumb */
.progress-bar::-moz-range-thumb:hover {
    background-color: #9af36990;
    box-shadow: 0 0 10px #9af36990;
}

/* For Internet Explorer */
.progress-bar::-ms-track {
    background-color: transparent;
    border-color: transparent;
    color: transparent;
    width: 100%;
    height: 8px;
}

.progress-bar::-ms-fill-lower {
    background: transparent;
}

.progress-bar::-ms-fill-upper {
    background: transparent;
}

.progress-bar::-ms-thumb {
    width: 40px;
    height: 8px;
    background-color: #8c7dff99;
    cursor: pointer;
    border: none;
    border-radius: 3px;
}

.letter {
   transition: color 0.3s ease;
}

.youtube-audio {
  display: flex;               /* Use flexbox for alignment */
  justify-content: center;     /* Center items horizontally */
  align-items: center;         /* Center items vertically (optional) */
  margin: 20px 0;             /* Add some vertical spacing */
}

.youtube-audio img {
  max-width: none;            /* Keep the original size of the image */
  width: auto;               /* Maintain aspect ratio */
}

/* SVG Icon Styling */
.icon {
    width: 24px;
    height: 24px;
    transition: fill 0.3s ease;
}

/* Play Icon Styling */
.play-icon, .pause-icon, .stop-icon {
    fill: #65b2ff50 !important;
    filter: drop-shadow(0 0 3px #65b2ff40); /* Blue glow */
}

.play-icon:hover, .pause-icon:hover, .stop-icon:hover {
    fill: #9af36990 !important;
    filter: drop-shadow(0 0 3px #9af36999); /* Blue glow */
}

/*@import url('https://fonts.googleapis.com/css?family=Lobster');*/


.neon-display {
    text-align: center;
	font-family: 'Lobster', cursive;
    margin-bottom: 10px;
}

.band-name {
    font-size: 1.5em;
    color: #9af36990;
    text-shadow: 0 0 10px #9af36990, 0 0 20px #9af36990;
}

.song-title {
    font-size: 1.2em;
    color: #8c7dff90;
    text-shadow: 0 0 10px #8c7dff90, 0 0 20px #8c7dff90;
}

.time-display {
    color: #65b2ff50; /* Text color */
    width: 100px;
    margin: 0 0 2px 0;
    font-size: 0.7em; /* Adjust size as needed */
    text-shadow: 0 0 3px #65b2ff40;
}
</style>
</head>
<body>
<div class="media-player" data-video="4ClzRT9__4U" id="player1">
    <input type="range" class="progress-bar" value="0" step="1" min="0" />
    <span class="time-display">
        <span class="elapsed-time">0:00</span> / <span class="total-time">0:00</span>
    </span>
    <button class="toggle-play-btn">
        <!-- Initial Play Icon -->
        <svg class="play-icon" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24">
            <path d="M8 5v14l11-7z"/>
        </svg>
    </button>
    <button class="stop-btn">
        <!-- Stop Icon -->
        <svg class="icon stop-icon" xmlns="http://www.w3.org/2000/svg" width="24" height="24" viewBox="0 0 24 24">
            <path class="stop-icon" d="M6 6h12v12H6z" />
        </svg>
    </button>
</div>


    
    <script src="https://www.youtube.com/iframe_api"></script>
    <script src="path/to/your/script.js"></script> <!-- Link to your JavaScript file -->
</body>
</html>
```

### Important Note
Make sure that the `<script>` tag for the YouTube IFrame API is placed **before** your custom JavaScript file. This ensures that the API is loaded and ready before your script attempts to use it.

### License
This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
