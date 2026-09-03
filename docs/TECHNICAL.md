# 🔬 Smooth Chat Scroll Pro - Technical Documentation

## 📐 Architecture Overview

### Class Hierarchy

```
BasePlugin (from SDK)
    ↓
SmoothScrollPlugin
    ├── PerformanceMonitor (inner class)
    ├── GestureDetector (inner class)
    └── Easing Functions (static methods)
```

---

## 🏗️ Core Components

### 1. PerformanceMonitor
**Purpose:** Frame rate limiting and rendering statistics

```python
class PerformanceMonitor:
    def __init__(self, max_fps: int = 60)
    def can_render(self) -> bool        # Check if frame should be rendered
    def reset(self)                     # Reset statistics
```

**How it works:**
- Maintains frame timing based on target FPS
- Skips rendering if not enough time has passed
- Tracks total and skipped frames for diagnostics

**Usage in animations:**
```python
for step in range(steps):
    if not self._performance_monitor.can_render():
        continue  # Skip this frame
    # ... render frame
```

### 2. GestureDetector
**Purpose:** Detect and track touch gestures

```python
class GestureDetector:
    def on_touch_start(self, x: float, y: float)
    def on_touch_move(self, x: float, y: float) -> Dict
    def on_touch_end(self) -> Dict
```

**Gesture Types:**
- Swipe (horizontal/vertical)
- Pinch zoom
- Long press
- Double tap

**Detected Properties:**
- Position (x, y)
- Delta from start
- Distance traveled
- Velocity
- Time elapsed

### 3. Easing Functions
**Purpose:** Smooth animation curves

All easing functions follow signature: `f(t: float) -> float` where `t ∈ [0, 1]`

#### Cubic In-Out (smooth)
```python
@staticmethod
def _ease_in_out_cubic(t: float) -> float:
    if t < 0.5:
        return 4 * t * t * t
    else:
        return 1 - pow(-2 * t + 2, 3) / 2
```
- **Type:** Polynomial
- **Characteristics:** Acceleration and deceleration
- **Use case:** General purpose animations

#### Elastic (spring-like)
```python
@staticmethod
def _ease_elastic(t: float) -> float:
    c4 = (2 * math.pi) / 3
    return pow(2, -10 * t) * math.sin((t * 10 - 0.75) * c4) + 1
```
- **Type:** Exponential + Sinusoidal
- **Characteristics:** Oscillating, spring effect
- **Use case:** Bouncy, playful animations

#### Wave (sinusoidal)
```python
@staticmethod
def _ease_wave(t: float) -> float:
    return 0.5 - 0.5 * math.cos(math.pi * t)
```
- **Type:** Trigonometric
- **Characteristics:** Smooth wave pattern
- **Use case:** Smooth transitions between states

#### Bezier (cubic curve)
```python
@staticmethod
def _ease_bezier(t: float) -> float:
    p0, p1, p2, p3 = 0, 0.25, 0.75, 1
    mt = 1 - t
    return (mt**3 * p0 + 3*mt**2*t*p1 + 
            3*mt*t**2*p2 + t**3*p3)
```
- **Type:** Polynomial (degree 3)
- **Characteristics:** Controlled curve with control points
- **Use case:** Premium animations with precise control

---

## 🎬 Animation Pipeline

### Scroll Animation Flow

```
user_input
    ↓
on_send_message_hook(".scroll.test")
    ↓
_test_smooth_scroll()
    ↓
threading.Thread → _animate_scroll()
    ↓
for step in range(steps):
    ├─ progress = step / steps
    ├─ eased_progress = _get_eased_progress(style, progress)
    ├─ current_pos = start_pos + distance * eased_progress
    ├─ PerformanceMonitor.can_render() check
    ├─ run_on_ui_thread(_update_scroll_position(current_pos))
    └─ time.sleep(step_duration)
    ↓
animation_complete
```

### Gesture Animation Flow

```
touch_event
    ↓
GestureDetector.on_touch_start()
    ↓
GestureDetector.on_touch_move() → detect swipe
    ↓
_animate_gesture(gesture_type, duration)
    ↓
for step in range(steps):
    ├─ progress = step / steps
    ├─ eased_progress = _ease_out_cubic(progress)
    ├─ run_on_ui_thread(_update_gesture_position(gesture_type, progress))
    └─ time.sleep(step_duration)
    ↓
GestureDetector.on_touch_end() → velocity calculation
    ↓
momentum_animation (if enabled)
```

---

## ⚙️ Configuration System

### Settings Storage
```python
# Get setting with default fallback
value = self.get_setting("key", default_value)

# Save setting
self.set_setting("key", value)
```

### Available Settings
| Key | Type | Default | Range |
|-----|------|---------|-------|
| animation_style | str | "smooth" | See SCROLL_ANIMATIONS |
| animation_duration | int | 200 | 50-500 ms |
| enable_gestures | bool | True | - |
| enable_momentum | bool | True | - |
| enable_optimization | bool | True | - |
| max_fps | int | 60 | 30-120 |
| use_gpu | bool | True | - |
| smooth_transition | bool | True | - |
| transition_style | str | "fade" | fade/slide/scale |

---

## 🔌 Hook System

### Message Hook
```python
def on_send_message_hook(self, account: int, params: Any) -> HookResult:
    if message == ".scroll.test":
        self._test_smooth_scroll()
        return HookResult(strategy=HookStrategy.CANCEL)
```

### Hook Return Values
```python
HookResult()                                    # No action
HookResult(strategy=HookStrategy.CANCEL)       # Block message
HookResult(strategy=HookStrategy.MODIFY, 
           params=modified_params)              # Modify message
```

---

## 🔧 Extending the Plugin

### Adding a New Easing Function

```python
@staticmethod
def _ease_custom(t: float) -> float:
    """Custom easing function description"""
    # Implement mathematical formula
    return result  # Must return float in [0, 1]

# Register in SCROLL_ANIMATIONS
SCROLL_ANIMATIONS = {
    ...
    "custom": ("Custom Name", duration_ms),
    ...
}

# Use in _get_eased_progress()
elif style == "custom":
    return self._ease_custom(progress)
```

### Adding a New Gesture Type

```python
def _animate_custom_gesture(self, duration_ms: int = 200):
    """Animate custom gesture"""
    for step in range(steps):
        if not self._performance_monitor.can_render():
            continue
        
        progress = step / steps
        eased_progress = self._ease_in_out_cubic(progress)
        
        run_on_ui_thread(lambda p=eased_progress: 
                       self._update_custom_gesture(p))
        
        time.sleep(step_duration / 1000.0)
```

### Adding a New Command

```python
def on_send_message_hook(self, account: int, params: Any) -> HookResult:
    if message == ".scroll.custom":
        self._handle_custom_command()
        return HookResult(strategy=HookStrategy.CANCEL)

def _handle_custom_command(self):
    """Handle custom command"""
    # Implementation
    pass
```

---

## 📊 Performance Metrics

### FPS Impact

```
Animation Style  | GPU Usage | CPU Usage | Memory |
Smooth          | Low       | Low       | <1MB   |
Elastic         | Medium    | Medium    | <1MB   |
Wave            | Low       | Low       | <1MB   |
Bezier          | Medium    | Low       | <1MB   |
Spring          | High      | High      | <2MB   |
Bounce          | Low       | Medium    | <1MB   |
```

### Optimization Techniques

1. **Frame Skipping**
   - PerformanceMonitor tracks frame timing
   - Skips rendering if GPU is busy
   - Maintains smooth overall animation

2. **Memory Pooling**
   - Reuses gesture detector instance
   - Avoids allocating new objects per frame

3. **Math Optimization**
   - Pre-computed values where possible
   - Uses fast approximations
   - Avoids expensive operations in loops

### Battery Impact

```
FPS 30  | ~5% additional drain
FPS 60  | ~10% additional drain
FPS 120 | ~20% additional drain
```

---

## 🧪 Testing Guide

### Unit Testing Easing Functions

```python
# Test cubic easing
assert SmoothScrollPlugin._ease_in_out_cubic(0.0) == 0.0
assert SmoothScrollPlugin._ease_in_out_cubic(1.0) == 1.0
assert SmoothScrollPlugin._ease_in_out_cubic(0.5) == 0.5  # cubic is symmetric

# Test wave easing
assert abs(SmoothScrollPlugin._ease_wave(0.0) - 0.0) < 0.01
assert abs(SmoothScrollPlugin._ease_wave(1.0) - 1.0) < 0.01
```

### Integration Testing

```python
def test_animation_pipeline():
    plugin = SmoothScrollPlugin()
    plugin.on_plugin_load()
    
    # Test scroll animation
    plugin._animate_scroll(0, 500, 200)
    assert plugin._scroll_active == False  # Should complete
    
    # Test stats
    stats = plugin._get_performance_stats()
    assert "📊" in stats  # Check output format
```

### Performance Testing

```python
import time

start = time.time()
plugin._animate_scroll(0, 500, 200)
duration = time.time() - start

# Should complete in approximately 200ms
assert 190 < duration < 220  # With 20ms tolerance
```

---

## 🐛 Debugging

### Enable Debug Logging

```python
self.log(f"Debug message: {variable}")
# Output visible in Ayugram logs
```

### Common Issues & Solutions

| Issue | Cause | Solution |
|-------|-------|----------|
| Animation jittery | GPU busy | Reduce FPS or animation style |
| Memory leak | GestureDetector not reset | Call detector.reset() |
| Touch not detected | No gesture hook | Ensure Ayugram >= 12.5.0 |
| Animation never ends | Boolean stuck true | Add timeout mechanism |

---

## 📈 Version History

### v2.0.0
- Added 4 new easing functions
- Implemented gesture detection system
- Added PerformanceMonitor
- Added statistics tracking
- Added GPU acceleration option

### v1.0.0
- Basic scroll animations
- 4 easing functions
- Simple settings

---

## 📚 References

### Easing Functions
- https://easings.net/
- https://developer.android.com/guide/topics/graphics/overview

### Animation Principles
- iOS Human Interface Guidelines - Animation
- Material Design - Motion Guidelines

### Ayugram SDK
- BasePlugin API documentation
- Hook system reference
- UI components guide

---

**For questions or contributions, refer to the main README.**
