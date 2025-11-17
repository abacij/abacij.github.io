---
title: "Ideological Threat and Perceptual Bias"
excerpt: Sociopolitical information processing on perceptual bias <br/><img src='/images/pb.jpg' style="width:400px;">
collection: portfolio
---

Ideologies—shared systems of political or religious beliefs—serve as powerful psychological lenses that shape how people interpret information. Even when presented with the same content, individuals may reach different conclusions depending on their ideological beliefs and motivations to maintain them. The current project I am coordinating at Rutgers investigates whether ideology influences how people visually perceive sociopolitical imagery. 

In a study conducted in the days before the 2024 U.S. presidential election, we examined how people perceived the size of political rallies. Using a novel visual matching tool (see below!), participants estimated how many people they saw in a photograph described as either a Trump or a Harris rally. We found evidence for ideologically motivated visual perception; when participants thought the photograph depicted their preferred candidate’s rally, they perceived more people than when they thought the photograph depicted the opposing candidate’s rally. Such findings reveal polarization at early stages of information processing.

Ongoing data collection is investigating these effects in other polarizing sociopolitical topics, including immigration policy, research funding cuts, and LGBTQ+ rights. Specifically, we are exploring this motivated perception through the lens of parallel processes of fear and danger control; those low in response-efficacy might visually minimize ideological threat to decrease fear and defensive activism, while those high in response-efficacy might visually exaggerate ideological threat to increase fear and defensive activism. Thus, current studies are employing response-efficacy manipulation to assess the relationship between efficacy, threat, and visual perception.

<html>

<head>
  <title>Resizable Box with Stylish Slider</title>

  <style>
    /* Center all content */
    #pageContainer {
      display: flex;
      flex-direction: column;
      align-items: center;
      margin-top: 10px;
    }

    /* Photo sizing — change width as needed */
    #imageContainer img {
      width: 620px;  /* Slightly larger than the 600px dot box */
      height: auto;
      display: block;
    }

    /* Dot box container */
    #boxContainer {
      width: 600px;
      height: 300px;
      border: 4px solid blue;
      position: relative;
      margin-top: 10px;
    }

    /* Dots */
    .dot {
      width: 4px;
      height: 4px;
      background-color: black;
      border-radius: 50%;
      position: absolute;
      transform: translate(-50%, -50%);
    }

    /* Slider container */
    #dotsSliderContainer {
      width: 50%;
      margin-top: 12px;
      margin-bottom: 5px;
    }
  </style>
</head>

<body>
  <div id="pageContainer">

    <!-- IMAGE ABOVE THE BOX -->
    <div id="imageContainer">
      <img src="https://rutgers.yul1.qualtrics.com/ControlPanel/Graphic.php?IM=IM_9SNB2MQ5D76drt4" alt="Your Image">
    </div>

    <!-- DOT BOX + SLIDER -->
    <div id="container">
      <div id="boxContainer"></div>

      <div id="dotsSliderContainer">
        <input type="range" min="0" max="5500" value="0" id="dotsSlider" style="width: 100%;">
      </div>

      <div id="sliderValue"></div>
      <input type="hidden" id="finalDotCount" name="finalDotCount">
    </div>

    <script>
      var boxContainer = document.getElementById('boxContainer');
      var dotsSlider = document.getElementById('dotsSlider');

      // Store dot divs here
      var existingDots = [];

      function addRandomDot(boxWidth, boxHeight, dotSize) {
        var dot = document.createElement('div');
        dot.className = 'dot';
        var randomX = Math.random() * (boxWidth - dotSize);
        var randomY = Math.random() * (boxHeight - dotSize);
        dot.style.left = randomX + 'px';
        dot.style.top = randomY + 'px';
        existingDots.push(dot);
        boxContainer.appendChild(dot);
      }

      function removeRandomDot() {
        if (existingDots.length > 0) {
          var index = Math.floor(Math.random() * existingDots.length);
          var dot = existingDots.splice(index, 1)[0];
          boxContainer.removeChild(dot);
        }
      }

      function updateDots(value) {
        var boxWidth = boxContainer.clientWidth;
        var boxHeight = boxContainer.clientHeight;
        var dotSize = 4;

        // Clear dots the safe way (keeps object references)
        while (boxContainer.firstChild) {
          boxContainer.removeChild(boxContainer.firstChild);
        }

        // Re-add stored dots
        existingDots.forEach(function (dot) {
          boxContainer.appendChild(dot);
        });

        // Add or remove dots to match slider value
        if (value > existingDots.length) {
          for (var i = existingDots.length; i < value; i++) {
            addRandomDot(boxWidth, boxHeight, dotSize);
          }
        } else if (value < existingDots.length) {
          for (var i = existingDots.length; i > value; i--) {
            removeRandomDot();
          }
        }

        // Update hidden field for Qualtrics
        document.getElementById('finalDotCount').value = value;

        // If running inside Qualtrics
        if (typeof Qualtrics !== "undefined") {
          Qualtrics.SurveyEngine.setEmbeddedData('finalDotCount', value);
        }
      }

      dotsSlider.addEventListener('input', function () {
        var sliderValue = parseInt(dotsSlider.value);
        updateDots(sliderValue);
      });

      // Initialize
      updateDots(parseInt(dotsSlider.value));
    </script>

  </div>
</body>

</html>

