# Anti-Overlap System Usage Instructions

## For Repository Maintainers

Since `festival2` is a submodule, the changes need to be applied to the festival2 repository first, then the www repository can update its submodule reference.

### Step 1: Apply changes to festival2 repository

```bash
cd festival2
git apply ../festival2-changes.patch
git add .
git commit -m "Add anti-overlap velocity system for agents"
git push
```

### Step 2: Update submodule reference in www repository

```bash
cd ..
git add festival2
git commit -m "Update festival2 submodule with anti-overlap system"
git push
```

## How It Works

The anti-overlap system prevents agents from overlapping by calculating repulsion forces:

1. **Automatic Detection**: System automatically detects when agents overlap (distance < combined radius)

2. **Repulsion Forces**: Agents experiencing overlap receive velocity vectors pushing them apart
   - Direction: Away from overlapping agent
   - Magnitude: Proportional to overlap amount (more overlap = stronger push)

3. **Smart Obstacle Avoidance**: Anti-overlap forces are disabled if they would push an agent into an obstacle

4. **Visualization**: Enable "Show Lines" button to see:
   - Green lines: Pathfinding destinations
   - Red lines: Anti-overlap forces (length shows force magnitude)

## User Experience

- Agents still move toward their destinations using pathfinding
- When agents get too close, they gently push each other apart
- The system is subtle - agents maintain natural movement while avoiding overlap
- Works for both moving and idle agents

## Testing

Run tests with:
```bash
cd festival2
npm test
```

All 255 tests should pass, including 29 new anti-overlap tests.
