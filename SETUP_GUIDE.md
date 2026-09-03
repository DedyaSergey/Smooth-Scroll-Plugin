# 🚀 Complete Setup & Installation Guide

## GitHub Repository
📍 **https://github.com/DedyaSergey/Smooth-Scroll-Plugin**

---

## 📥 Installation Steps

### Step 1: Clone Repository
```bash
git clone https://github.com/DedyaSergey/Smooth-Scroll-Plugin.git
cd Smooth-Scroll-Plugin
```

### Step 2: Get the Plugin File
The plugin is located at: `src/SmoothScroll.plugin`

### Step 3: Install to Ayugram
1. **Locate Ayugram plugins folder:**
   - On Android: `/data/data/com.exteragram/files/plugin_bot/plugins/`
   - Or: `Ayugram → Settings → About → (tap version) → Plugin folder`

2. **Copy plugin file:**
   ```bash
   cp src/SmoothScroll.plugin /path/to/Ayugram/plugins/
   ```

3. **Restart Ayugram completely**
   - Force close the app
   - Reopen it

### Step 4: Enable Plugin
1. Open **Settings** → **Plugins**
2. Find **"Smooth Chat Scroll Pro"**
3. **Toggle ON** to enable
4. ✅ Plugin is now active!

---

## ⚙️ Settings (Click Settings Button Next to Plugin)

### Animation Settings
**🎨 Стиль анимаций (Animation Style)**
- Choose from 8 professional styles:
  - **Smooth** - Fastest, everyday use (200ms)
  - **Elastic** - Impressive, bouncy (350ms)
  - **Ease Out** - Professional deceleration (250ms)
  - **Bounce** - Fun, playful (400ms)
  - **Spring** - Controlled pulsing (300ms)
  - **Wave** - Sinusoidal smooth (280ms)
  - **Bezier** - Premium curves (200ms)
  - **Decelerate** - Progressive slowdown (220ms)

**⏱️ Скорость (Speed)**
- **Медленно** (Slow) - 350ms
- **Нормально** (Normal) - 250ms - ⭐ RECOMMENDED
- **Быстро** (Fast) - 150ms

### Gesture Settings
**👆 Анимации жестов (Gesture Animations)**
- ✓ ON - Enable swipe/gesture animations
- ✗ OFF - Disable for performance

**💨 Инерция прокрутки (Momentum Scrolling)**
- ✓ ON - Continue scrolling after release
- ✗ OFF - Stop immediately

### Performance Optimization
**⚙️ Оптимизация FPS (FPS Optimization)**
- ✓ ON - Limit FPS for battery saving
- ✗ OFF - Use unlimited FPS

**🎬 Максимальное количество FPS**
- **30 FPS (экономно)** - Battery saver, smooth enough
- **60 FPS (стандарт)** - Recommended balance ⭐
- **120 FPS (плавно)** - Maximum smoothness, more battery drain

**🚀 Аппаратное ускорение (GPU Acceleration)**
- ✓ ON - Use GPU for animations (recommended)
- ✗ OFF - CPU only (saves power)

### Chat Transitions
**📊 Плавный переход (Smooth Transition)**
- ✓ ON - Animate when switching chats
- ✗ OFF - Instant switch

**🎭 Стиль перехода (Transition Style)**
- **Fade (затухание)** - Fade in/out
- **Slide (скольжение)** - Slide animation
- **Scale (масштаб)** - Zoom effect

---

## 🎮 Quick Settings Profiles

### Profile 1: Recommended (Most Users)
```
Animation Style: Elastic or Wave
Speed: Нормально (250ms)
FPS: 60
Gestures: ✓ ON
GPU: ✓ ON
Transition: ✓ ON
Battery Impact: ~10%
Performance: ⭐⭐⭐⭐⭐
```
**Best For:** Balance of beauty and performance

### Profile 2: Maximum Performance
```
Animation Style: Smooth
Speed: Быстро (150ms)
FPS: 60
Gestures: ✗ OFF (optional)
GPU: ✓ ON
Transition: ✓ ON
Battery Impact: ~8%
Performance: ⭐⭐⭐⭐⭐
```
**Best For:** Power users, navigation-heavy usage

### Profile 3: Battery Saver
```
Animation Style: Smooth
Speed: Нормально (250ms)
FPS: 30
Gestures: ✗ OFF
GPU: ✗ OFF
Transition: ✓ ON
Battery Impact: ~4%
Performance: ⭐⭐⭐☆☆
```
**Best For:** Battery-conscious users

### Profile 4: Premium/Creative
```
Animation Style: Wave or Spring
Speed: Нормально (250ms)
FPS: 120 (if available)
Gestures: ✓ ON
GPU: ✓ ON
Transition: ✓ ON
Battery Impact: ~15%
Performance: ⭐⭐⭐⭐⭐
```
**Best For:** Content creators, showcasing animations

---

## 🎮 Testing Commands

After installation, test with these commands in any chat:

### `.scroll.test`
**Tests smooth scroll animation**
```
Send: .scroll.test
Result: Smooth scrolling animation demo
Duration: 200-250ms
```

### `.scroll.gesture`
**Tests gesture animations**
```
Send: .scroll.gesture
Result: Swipe left and right animations
Duration: 200-400ms
```

### `.scroll.stats`
**Shows performance statistics**
```
Send: .scroll.stats
Result:
  📊 Статистика производительности
  - Всего кадров: 1250
  - Пропущено: 25
  - Коэффициент рендера: 98.0%
  - Макс FPS: 60
  - Стиль анимации: Smooth
  - Длительность: 250ms
  - Жесты: Включены
  - Инерция: Включена
```

### `.scroll.info`
**Shows plugin information**
```
Send: .scroll.info
Result:
  🎨 Smooth Chat Scroll Pro v2.0
  - Версия: 2.0.0
  - 8 стилей анимаций
  - 6 типов жестов
  - Оптимизация производительности
  - Все команды и детали
```

---

## 🎯 Auto-Smoothing Features

The plugin **automatically applies** smooth scrolling when:

✅ You scroll through chats list
✅ You navigate between messages
✅ You use swipe gestures
✅ You switch between dialogs
✅ You open conversation list

**No manual activation needed** - just enable the plugin and enjoy!

---

## 🛠️ Customization Tips

### For Smooth Daily Browsing
1. Set Animation: **Smooth**
2. Set Speed: **Нормально (250ms)**
3. Set FPS: **60**
4. Enable Gestures: **ON**
5. Enable GPU: **ON**

### For Maximum Battery Life
1. Set Animation: **Smooth**
2. Set Speed: **Нормально (250ms)**
3. Set FPS: **30**
4. Enable Gestures: **OFF**
5. Enable GPU: **OFF**

### For Impressive Visuals
1. Set Animation: **Elastic** or **Wave**
2. Set Speed: **Нормально (250ms)**
3. Set FPS: **60**
4. Enable Gestures: **ON**
5. Enable GPU: **ON**

### For Fast Navigation
1. Set Animation: **Smooth**
2. Set Speed: **Быстро (150ms)**
3. Set FPS: **60**
4. Enable Gestures: **ON**
5. Enable GPU: **ON**

---

## 🐛 Troubleshooting

### Problem: Animations are laggy/choppy
**Solution:**
1. Open Plugin Settings
2. Set FPS: **30** (not 120)
3. Set Animation: **Smooth** (fastest style)
4. Set Speed: **Быстро (150ms)**
5. Test with `.scroll.test`

### Problem: Plugin doesn't appear in settings
**Solution:**
1. Verify file is at: `Ayugram/plugins/SmoothScroll.plugin`
2. **Force close** Ayugram completely
3. Reopen Ayugram
4. Check Settings → Plugins

### Problem: Battery drains too fast
**Solution:**
1. Enable: **Оптимизация FPS** (FPS Optimization)
2. Set FPS: **30 FPS (экономно)**
3. Disable: **Аппаратное ускорение** (GPU Acceleration)
4. Disable: **Анимации жестов** (if not using gestures)

### Problem: Gestures don't work
**Solution:**
1. Verify Ayugram version: **≥ 12.5.0**
2. Enable: **Анимации жестов** in settings
3. **Restart** Ayugram
4. Test with `.scroll.gesture`

### Problem: Settings don't save
**Solution:**
1. **Force close** Ayugram
2. Reopen
3. Settings should be restored
4. If not, disable and re-enable plugin

---

## 📊 Performance Monitoring

### How to Check Performance
```
1. Send: .scroll.stats
2. Look at: "Коэффициент рендера" (Render Rate)
3. Should be: > 90% (optimal)
   - > 95% = Excellent
   - 90-95% = Good
   - < 90% = Needs optimization
```

### If Render Rate is Low (< 90%)
```
1. Lower FPS: 60 → 30
2. Change to "Smooth" animation
3. Disable gestures if not using
4. Disable GPU acceleration
5. Test again with .scroll.stats
```

---

## 📚 More Information

For detailed information, see:
- **QUICK_START.md** - 1-minute setup
- **docs/README.md** - Complete manual
- **docs/TECHNICAL.md** - Developer guide
- **examples/USE_CASES.md** - Real-world examples
- **docs/FEATURES.txt** - Feature comparison

---

## ✨ Features at a Glance

**Animation Styles:** 8
**Gesture Types:** 6
**Settings:** 15+
**Commands:** 4
**Performance Profiles:** 5 presets
**FPS Options:** 3 (30/60/120)
**GPU Support:** Yes
**Battery Optimization:** Yes
**Auto-Apply:** Yes

---

## 🎉 You're All Set!

1. ✅ Plugin installed
2. ✅ Settings available in Plugin section
3. ✅ Auto-smoothing enabled
4. ✅ Ready to customize

**Enjoy smooth, beautiful animations!** 🚀

---

**Need help?** Check the other documentation files or use `.scroll.info` in any chat.
