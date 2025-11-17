---
title: "Ideological Threat and Perceptual Bias"
excerpt: Sociopolitical information processing on perceptual bias <br/><img src='/images/pb.jpg' style="width:400px;">
collection: portfolio
---

Ideologies—shared systems of political or religious beliefs—serve as powerful psychological lenses that shape how people interpret information. Even when presented with the same content, individuals may reach different conclusions depending on their ideological beliefs and motivations to maintain them. The current project I am coordinating at Rutgers investigates whether ideology influences how people visually perceive sociopolitical imagery. 

In a study conducted in the days before the 2024 U.S. presidential election, we examined how people perceived the size of political rallies. Using a novel visual matching tool (see below!), participants estimated how many people they saw in a photograph described as either a Trump or a Harris rally. We found evidence for ideologically motivated visual perception; when participants thought the photograph depicted their preferred candidate’s rally, they perceived more people than when they thought the photograph depicted the opposing candidate’s rally. Such findings reveal polarization at early stages of information processing.

Ongoing data collection is investigating these effects in other polarizing sociopolitical topics, including immigration policy, research funding cuts, and LGBTQ+ rights. Specifically, we are exploring this motivated perception through the lens of parallel processes of fear and danger control; those low in response-efficacy might visually minimize ideological threat to decrease fear and defensive activism, while those high in response-efficacy might visually exaggerate ideological threat to increase fear and defensive activism. Thus, current studies are employing response-efficacy manipulation to assess the relationship between efficacy, threat, and visual perception.

<div class="center-text">
 <b>Below is the visual perception tool used in our election study—and one of several tools employed across our projects. All participants viewed the same rally photograph but were told it depicted either a pro-Trump or a pro-Harris event. They then adjusted a slider until the number of dots in the box matched the number of people they believed were in the photo. (Although this demonstration displays a dot count, participants did not see this information.) We recorded each participant’s final dot estimate to compare perceptions across conditions.</b>
</div>

<html>

<head>
  <title>Visual Matching Task</title>

  <style>
    /* Center everything */
    #pageContainer {
      display: flex;
      flex-direction: column;
      align-items: center;
      margin-top: 20px;
    }

    /* Image 100px smaller than before */
    #imageContainer img {
      width: 500px; /* was 600px */
      height: auto;
      border: 2px solid #ccc;
    }

    /* Box: 100px smaller */
    #boxContainer {
      width: 500px;   /* was 600px */
      height: 250px;  /* was 300px */
      border: 4px solid blue;
      position: relative;
      background: white;
      margin-top: 15px;
    }

    .dot {
      width: 4px;
      height: 4px;
      background-color: black;
      border-radius: 50%;
      position: absolute;
      transform: translate(-50%, -50%);
    }

    #dotsSliderContainer {
      width: 50%;
      margin-top: 15px;
    }
  </style>
</head>

<body>
  <div id="pageContainer">

    <!-- IMAGE -->
    <div id="imageContainer">
      <img src="https://rutgers.yul1.qualtrics.com/ControlPanel/Graphic.php?IM=IM_9SNB2MQ5D76drt4" alt="Your Image">
    </div>

    <!-- DOTS + SLIDER -->
    <div id="boxContainer"></div>

    <div id="dotsSliderContainer">
      <input type="range" min="0" max="5500" value="0" class="slider" id="dotsSlider" style="width: 100%;">
    </div>

    <div id="sliderValue"></div>
    <input type="hidden" id="finalDotCount" name="finalDotCount">

  </div>

  <script>
    window.onload = function () {

      var boxContainer = document.getElementById('boxContainer');
      var dotsSlider = document.getElementById('dotsSlider');
      var sliderValueDisplay = document.getElementById('sliderValue');

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
          var dotToRemove = existingDots.pop();
          boxContainer.removeChild(dotToRemove);
        }
      }

      function updateDots(value) {
        boxContainer.innerHTML = '';
        existingDots = [];

        var boxWidth = boxContainer.clientWidth;
        var boxHeight = boxContainer.clientHeight;
        var dotSize = 4;

        for (var i = 0; i < value; i++) {
          addRandomDot(boxWidth, boxHeight, dotSize);
        }

        document.getElementById('finalDotCount').value = value;
        sliderValueDisplay.innerHTML = "Dots: " + value;

        if (typeof Qualtrics !== "undefined") {
          Qualtrics.SurveyEngine.setEmbeddedData('finalDotCount', value);
        }
      }

      dotsSlider.addEventListener('input', function () {
        updateDots(parseInt(this.value));
      });

      updateDots(parseInt(dotsSlider.value));
    };
  </script>

</body>

</html>

You can find more tools like this on my github! https://github.com/abacij
