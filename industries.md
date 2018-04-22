---
title: Industries
layout: default
css:
- https://unpkg.com/mermaid@7.0.5/dist/mermaid.neutral.min.css
scripts:
- https://unpkg.com/mermaid@7.0.5/dist/mermaid.min.js
---

<div id="craftTree" class="mermaid">
	<p>Loading craft tree...</p>
</div>

<script>
	mermaid.initialize({
		startOnLoad: true,
	});

	var request = new XMLHttpRequest();
	request.open("GET", "https://raw.githubusercontent.com/rubenwardy/capitalism_game/master/docs/crafting.mermaid");
	request.responseType = "text";

	request.onload = function() {
		var element = document.querySelector("#craftTree");
		element.innerHTML = "<p>Failed to load craft tree data.</p>";

		var graphDefinition = request.response;
		var graph = mermaidAPI.render("craftTree", graphDefinition, function(svgCode, bindFunctions) {
			element.innerHTML = svgCode;

			var svg = element.firstChild;
			var bb  = svg.getBBox();
			svg.setAttribute("viewBox", [bb.x, bb.y, bb.width, bb.height].join(" "));
		});
	};

	request.send();
</script>
