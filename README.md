# CS2 Grenade Trajectory Study

An archived design study for an offline grenade-trajectory simulator inspired by Counter-Strike 2 physics.

## Status

This repository currently contains **concept documentation only**. It has no simulator, map parser, overlay, game integration, executable, test suite, or validated physics model. It should not be treated as a completed project or production claim.

## Intended safe scope

A future implementation would be a standalone training and visualization tool using user-supplied parameters or legally reusable map geometry. It would not read game memory, inject code, automate competitive play, or bypass anti-cheat controls.

## Proposed model

The simulator would accept:

- a start position
- a target position
- throw strength and direction
- gravity and drag coefficients
- simplified collision surfaces
- bounce restitution and friction

At each time step, it would update position and velocity, test the segment against scene geometry, apply a bounce response when necessary, and retain the sampled path for visualization.

```text
velocity = velocity + gravity * dt
velocity = velocity * drag
position = position + velocity * dt
```

## Possible milestones

1. **Flat-plane prototype**
   - simulate a ballistic arc with configurable gravity and drag
   - solve for candidate angles and throw strength
   - visualize the path in a standalone window
2. **Collision model**
   - add simple planes and meshes
   - apply bounce and rolling behavior
   - compare deterministic fixtures in automated tests
3. **Offline map research**
   - evaluate legally reusable geometry sources and formats
   - document coordinate conversion and surface assumptions
   - keep the simulator independent from a running game process
4. **Calibration**
   - compare recorded training examples against the model
   - publish error bounds and known deviations

## Evidence required before calling it complete

- authored source code and a reproducible build
- automated tests for trajectory integration and collision response
- documented geometry and asset licenses
- recorded calibration inputs and error measurements
- screenshots or a video of the standalone simulator

Until those artifacts exist, this repository remains an experiment brief and is excluded from featured portfolio projects.
