# Closing the Loop in Simulation

A few years ago, building a robot to shoot a basketball while the robot was moving would have meant a lot of time standing next to a robot. Write some code, deploy, watch it miss, tweak a constant, deploy again. Repeat dozens, sometimes hundreds, of times. The robot was the bottleneck.

**The combination of simulation and an AI coding agent compressed my engineering feedback loop so dramatically that the real robot became the place I confirmed solutions, not the place I discovered them.**

## The old way

Physical-first development is slow in ways that have nothing to do with the problem you're solving. Robots need batteries. Motors overheat. Someone has to walk across the room and press reset. Every iteration carries overhead that has nothing to do with whether your algorithm is correct. You spend most of your time fighting the process, not thinking about the problem.

The loop looks like this: write code, deploy to hardware, test, walk to the robot, watch it fail, guess at why, repeat. It's slow enough that you start making fewer experiments. You get conservative. You tune by feel instead of by evidence, because evidence is expensive to collect.

## The shift

Instead of starting on hardware, I built the entire system in simulation. Using an AI coding agent, I described the behavior I wanted - a robot that could shoot while moving, accounting for both its own motion and the ball's trajectory. The agent implemented the logic, iterated on the code, and helped debug the system entirely in a virtual environment.

The development loop became: write code, simulate, iterate, validate. Hundreds of iterations faster than I could ever manage on physical hardware. I could inspect trajectories, visualize failures, tweak assumptions, and ask the AI agent to modify the implementation almost instantly. Mistakes cost seconds instead of minutes.

## Why it transferred

The key wasn't that the simulation was perfect. It wasn't. The key was that the logic was parameterized.

Instead of hardcoding values specific to the simulated world, I built the system around measurable physical parameters - shooter velocity, release speed, robot velocity, geometry, and timing. Those values could later be measured on the real robot and swapped in without changing the underlying algorithm.

Once the behavior looked right in simulation, I transferred it to hardware. It worked. Not perfectly, but close enough that the remaining work was tuning parameters, not redesigning the system. I only had to tune twice before the robot stopped missing - making every shot while moving across the field. The architecture was already correct. Reality just needed its own numbers plugged in.

## The bigger point

This isn't just a better robotics workflow. I think it's a glimpse of how many physical systems will get built going forward.

Simulation removes the friction of reality. AI removes the friction of implementation. Together, they let you spend almost all of your time on the actual problem - the physics, the strategy, the design - instead of on the mechanics of testing. The real world becomes your final validation step, not your development environment.

That single shift changes the speed at which robotics can improve. When every experiment is cheap and fast, you run more of them. When you run more of them, you find better solutions. The bottleneck moves from "how quickly can I test" to "how clearly can I think." And that's a much better bottleneck to have.
