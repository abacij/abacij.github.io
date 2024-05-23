---
layout: archive
title: "CV"
permalink: /cv/
author_profile: true
redirect_from:
  - /resume
---

<div id="pdf-container" style="width: 100%; height: 600px;"></div>
<p>This browser does not support PDFs. Please download the PDF to view it: 
<a href="/files/cv.pdf">Download PDF</a>.</p>

<script src="https://mozilla.github.io/pdf.js/build/pdf.js"></script>
<script>
var url = '/files/cv.pdf';

// Load the PDF
pdfjsLib.GlobalWorkerOptions.workerSrc = 'https://mozilla.github.io/pdf.js/build/pdf.worker.js';
var loadingTask = pdfjsLib.getDocument(url);
loadingTask.promise.then(function(pdf) {
  console.log('PDF loaded');

  // Fetch the first page
  var pageNumber = 1;
  pdf.getPage(pageNumber).then(function(page) {
    console.log('Page loaded');

    var scale = 1.5;
    var viewport = page.getViewport({ scale: scale });

    // Prepare canvas using PDF page dimensions
    var canvas = document.createElement('canvas');
    var context = canvas.getContext('2d');
    canvas.height = viewport.height;
    canvas.width = viewport.width;

    // Append the canvas to the container
    document.getElementById('pdf-container').appendChild(canvas);

    // Render PDF page into canvas context
    var renderContext = {
      canvasContext: context,
      viewport: viewport
    };
    var renderTask = page.render(renderContext);
    renderTask.promise.then(function() {
      console.log('Page rendered');
    });
  });
}, function(reason) {
  console.error(reason);
});
</script>