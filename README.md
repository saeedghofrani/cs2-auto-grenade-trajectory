# cs2-auto-grenade-trajectory
auto calculate the trajectory of grenade from starting point to the pinpoint location


🧠 Concept Overview
CS2 grenade throw planner/simulator that:

Hooks into CS2 via modding or external tools.

Lets you place a start point and an end point in the game world.

Simulates the real grenade physics (arc, gravity, air resistance, bounces).

Renders a visual curved path from start to target—like a training assist tool.

🔧 What We Likely Need
1. Access to CS2 Map Data
You need the actual 3D map geometry (or at least nav mesh) to:

Place start/target points.

Detect when grenades would hit walls or the ground.

Options:

Extract map data from CS2 files (.bsp) using something like BSPSrc.

Use existing tools like Mapbase or GCFScape to parse map layouts.

OR: Start small by recreating a simplified map layout (e.g., Dust2 A-site area) in 3D just for testing.

2. Grenade Physics Model
CS2 uses Source 2 physics, so you’ll want to replicate these grenade behaviors:

Initial throw speed varies (left-click, right-click, both).

Gravity and drag affect arc.

Grenades bounce off surfaces and roll.

Smokes detonate on timer (or under certain rules, e.g., bounce count).

model:

position += velocity * dt
velocity += gravity * dt
velocity *= drag (air resistance)

And check for collisions with surfaces to apply bounces.

3. Trajectory Simulation Engine

Takes a starting position and initial velocity (angle, power).

Runs a physics loop to simulate movement over time.

Detects when it hits walls or ground and adjusts trajectory accordingly.

Stores all the points in the path so you can render a curve.

4. In-Game Visualization
Options:

Build a CS2 mod/overlay using CSGO cheats-style framework (e.g., ImGui + OpenGL DirectX overlay).

Use OpenCV or DirectX overlay to draw paths on the screen in real-time.

🗺️ Project Phases
✅ Phase 1: Simple External Tool
small app to simulate throws on a flat plane.

Allow manual placement of start/target.

Simulate trajectory based on initial velocity/gravity/drag.

Visualize the curve.

🔜 Phase 2: Real Map Integration
Load map geometry from a .bsp file.

Handle collisions/bounces properly.

Add different throw types.

🧪 Phase 3: Hook into CS2
Add overlay or mod to place start point in real match.

 suggest throw angles and crosshair positions.