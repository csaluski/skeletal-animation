<script lang="ts">
	import World0 from "./View0/World0.svelte";
	import World1 from "./View1/World1.svelte";
	import { width, height } from "./stores";
</script>

<main class="container-md">
	<div class="rounded bg-light">
		<p class="h1">Let's build a skeletal animation system</p>
		<p class="lead">Some setup</p>
		<p>
			I'm choosing to write this blog using
			<a href="http://https://svelte.dev/">Svelte</a>
			, since its approach to reactive event processing will greatly simplify some
			of our later steps. I'm also using
			<a href="https://mljs.github.io/matrix/">ml-matrix</a>
			for matrix representation and operations. The code for this blog and others
			is available on my Github.
		</p>
		<p>
			Let's start with making a figure to draw to the screen, then we'll apply
			some basic transformations to it and see where that leaves us. We'll
			define this figure as a set of points and a set of lines that connect any
			two of those points together. These points will be defined as row vectors,
			with the first component being the x coordinate, and the second the y.
			This will make the programming slightly easier, and makes the application
			of transformation matrices we'll look at later more intuitive as well.
			We'll render to SVG, since it's entirely text and DOM based and is easy to
			inspect in the browser to see what's going on. However, we don't use any
			of SVG's built in transformation functions, because we want to implement
			those ourselves by transforming points and drawing the updated lines from
			those. We'll also draw a bounding box, this will help visualize some of
			our transformations, especially as we move move to a hierarchy
			transformations.
		</p>
		<World0 viewHeight="60" viewWidth="40" />
		<p>
			Great, we have our figure standing on the origin. This position at the
			origin is not important at this point, but in future steps we'll see that
			it's important to define each element in terms of its offset from its
			local origin. Now let's start with the easiest transformations,
			translating along the x and y plane. Because our figure is already defined
			in terms of row vectors, all we have to do is create a vector representing
			the offset transformation and add it to each of the row vectors in our
			point matrix. We'll render the transformed figure with blue points, so
			that we can clearly see what's happened to it.
		</p>
		<World1 viewHeight="100" viewWidth="80" />
	</div>
</main>

<style>
</style>
