---
title: Tracery
description: Generative text.
---

<script src="https://ajax.googleapis.com/ajax/libs/jquery/3.4.0/jquery.min.js"></script>
<script src="../assets/tracery.js"></script>
<script src="../assets/mods-eng-basic.js"></script>

<div id="result"></div>

<script>
	let g = tracery.createGrammar({
		vehicle: ['car', 'motorcycle', 'horse', 'unicycle']
	})
	g.addModifiers(baseEngModifiers)

	$('#result').text(g.flatten('#vehicle#'))
</script>
