# Festival2 Submodule Changes

This document describes the changes made to the festival2 submodule to implement the anti-overlap velocity system.

## Files Modified

### 1. js/AntiOverlap.js (NEW FILE)
Complete anti-overlap system implementation with:
- Overlap detection between agents
- Anti-overlap velocity vector calculation
- Multi-agent overlap handling
- Obstacle collision prevention
- Exact position overlap handling

### 2. js/Agent.js
Added:
- `allAgents` property to store reference to all agents
- `antiOverlapVx` and `antiOverlapVy` properties for visualization
- Red line visualization for anti-overlap vectors in draw() method

### 3. js/AgentState.js
Modified:
- Import anti-overlap functions
- IdleState: Calculate and apply anti-overlap forces even when idle
- MovingState: Calculate and combine pathfinding + anti-overlap velocities

### 4. js/Simulation.js
Modified:
- Handle exact overlap cases before updating agents
- Pass all agents to each agent for anti-overlap calculation

### 5. index.html
Changed button text from "Show Destinations" to "Show Lines"

### 6. js/main.js
Updated button text toggle to use "Show Lines" / "Hide Lines"

### 7. tests/AntiOverlap.test.js (NEW FILE)
Comprehensive test suite covering all anti-overlap functionality

## How It Works

1. **Overlap Detection**: Each frame, agents check if they overlap with other agents (distance < combined radius)

2. **Vector Calculation**: For each overlapping pair, calculate a velocity vector:
   - Direction: Away from the other agent
   - Magnitude: Proportional to overlap amount (scaling factor: 50)

3. **Vector Combination**: Multiple overlap vectors are summed (not averaged) for stronger combined effect

4. **Obstacle Capping**: Anti-overlap vectors are capped to 0 if they would cause collision with obstacles

5. **Exact Overlap Handling**: If two agents are at exact same position, one is moved 1 pixel right

6. **Visualization**: Red lines show anti-overlap vectors when "Show Lines" is enabled

## Testing

All 255 tests pass, including 29 new tests for the anti-overlap system.

## Visual Confirmation

The system was manually tested with 50+ agents. The agents successfully avoid overlapping while maintaining pathfinding behavior.
