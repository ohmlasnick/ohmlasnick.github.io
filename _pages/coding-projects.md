---
permalink: /coding-projects/
title: "Coding projects"
author_profile: true
redirect_from: 
  - /coding-projects/
  - /coding-projects.html
---

## Toy sand simulator in Python

Written for / inspired by Day #14 of [Advent of Code 2022.](https://adventofcode.com/2022/day/14) Full code can be found on [GitHub](https://github.com/ohmlasnick/Sand_Simulator).

The main simulator function uses custom classes <code>Map</code> and <code>Sand</code> to track the trajectory and location of each particle. You can also change the dimensions of the map and choose whether or not to include a platform.

<pre>
def simulate():
	my_map = Map(dims=[10, 21], floor=True, platform=False)
	my_map.show_map()
	while True:
		# create new piece of sand
		sand = Sand(my_map)
		while (not sand.in_void()) and (not sand.is_settled()):
			sleep(0.01)
			if sand.free_below():
				sand.move('down')
			elif sand.free_left():
				sand.move('left-diag')
			elif sand.free_right():
				sand.move('right-diag')
			my_map.frame_counter += 1
			my_map.show_map()
		if sand.in_void():
			return sand.map.count_sand()
</pre>

See the simulator in action (with a platform!):

<video width="500" class="center" controls autoplay>
    <source src="/files/simulation_with_platform.mov" type="video/mp4">
</video>
