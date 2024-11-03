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
</head>
<body>
    <div class="media-player" data-video="YOUR_VIDEO_ID" id="player1">
        <!-- Player UI elements go here -->
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
