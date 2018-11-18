---
title: Industries
layout: default
root: ../
css:
- https://unpkg.com/mermaid@7.0.5/dist/mermaid.neutral.min.css
scripts:
- https://unpkg.com/mermaid@7.0.5/dist/mermaid.min.js
---

Each company will likely have to focus on a particular industry to be successful.
To enter an industry, you either need to research the required technology or
buy a company which already has it.

Legend:

<ul class="legend">
	<li style="background:#99C794;">Products</li>
	<li style="background:#C594C5;">Tools / Machinery</li>
	<li style="background:#FAC863;">Level 2</li>
	<li style="background:#F99157;">Level 1</li>
	<li style="background:#EC5f67;">Raw</li>
</ul>

<div id="craftTree" class="mermaid">
	<p>Loading craft tree...</p>
</div>

<script>
	mermaid.initialize({
		startOnLoad: true,
	});

	var request = new XMLHttpRequest();
	request.open("GET", "crafting.mermaid");
	request.responseType = "text";

	request.onload = function() {
		var element = document.querySelector("#craftTree");
		element.innerHTML = "<p>Failed to load craft tree data.</p>";

		var graphDefinition = request.response;
		if (graphDefinition != "")
			mermaidAPI.render("craftTree", graphDefinition, function(svgCode, bindFunctions) {
				element.innerHTML = svgCode;

				var svg = element.firstChild;
				var bb  = svg.getBBox();
				svg.setAttribute("viewBox", [bb.x, bb.y, bb.width, bb.height].join(" "));
			});
	};

	request.send();
</script>
