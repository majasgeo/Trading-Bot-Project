# 📋 OPUS 4 TECHNICAL SPECIFICATIONS
## Complete Reference Document

### 🔥 DIVERGENCE FOR MANY INDICATORS v.4 - COMPLETE ORIGINAL CODE

```pinescript
// This source code is subject to the terms of the Mozilla Public License 2.0 at https://mozilla.org/MPL/2.0/
// © LonesomeTheBlue

//@version=4
study("Divergence for Many Indicators v4", overlay = true, max_bars_back = 1000, max_lines_count = 400, max_labels_count = 400)
prd = input(defval = 5, title = "Pivot Period", minval = 1, maxval = 50)
source = input(defval = "Close", title = "Source for Pivot Points", options = ["Close", "High/Low"])
searchdiv = input(defval = "Regular", title = "Divergence Type", options = ["Regular", "Hidden", "Regular/Hidden"])
showindis = input(defval = "Full", title = "Show Indicator Names", options = ["Full", "First Letter", "Don't Show"])
showlimit = input(1, title="Minimum Number of Divergence", minval = 1, maxval = 11)
maxpp = input(defval = 10, title = "Maximum Pivot Points to Check", minval = 1, maxval = 20)
maxbars = input(defval = 100, title = "Maximum Bars to Check", minval = 30, maxval = 200)
shownum = input(defval = true, title = "Show Divergence Number")
showlast = input(defval = false, title = "Show Only Last Divergence")
dontconfirm = input(defval = false, title = "Don't Wait for Confirmation")
showlines = input(defval = true, title = "Show Divergence Lines")
showpivot = input(defval = false, title = "Show Pivot Points")
calcmacd = input(defval = true, title = "MACD")
calcmacda = input(defval = true, title = "MACD Histogram")
calcrsi = input(defval = true, title = "RSI")
calcstoc = input(defval = true, title = "Stochastic")
calccci = input(defval = true, title = "CCI")
calcmom = input(defval = true, title = "Momentum")
calcobv = input(defval = true, title = "OBV")
calcvwmacd = input(true, title = "VWmacd")
calccmf = input(true, title = "Chaikin Money Flow")
calcmfi = input(true, title = "Money Flow Index")
calcext = input(false, title = "Check External Indicator")
externalindi = input(defval = close, title = "External Indicator")
pos_reg_div_col = input(defval = color.yellow, title = "Positive Regular Divergence")
neg_reg_div_col = input(defval = color.navy, title = "Negative Regular Divergence")
pos_hid_div_col = input(defval = color.lime, title = "Positive Hidden Divergence")
neg_hid_div_col = input(defval = color.red, title = "Negative Hidden Divergence")
pos_div_text_col = input(defval = color.black, title = "Positive Divergence Text Color")
neg_div_text_col = input(defval = color.white, title = "Negative Divergence Text Color")
reg_div_l_style_ = input(defval = "Solid", title = "Regular Divergence Line Style", options = ["Solid", "Dashed", "Dotted"])
hid_div_l_style_ = input(defval = "Dashed", title = "Hdden Divergence Line Style", options = ["Solid", "Dashed", "Dotted"])
reg_div_l_width = input(defval = 2, title = "Regular Divergence Line Width", minval = 1, maxval = 5)
hid_div_l_width = input(defval = 1, title = "Hidden Divergence Line Width", minval = 1, maxval = 5)
showmas = input(defval = false, title = "Show MAs 50 & 200", inline = "ma12")
cma1col = input(defval = color.lime, title = "", inline = "ma12")
cma2col = input(defval = color.red, title = "", inline = "ma12")

plot(showmas ? sma(close, 50) : na, color = showmas ? cma1col : na)
plot(showmas ? sma(close, 200) : na, color = showmas ? cma2col: na)

// set line styles
var reg_div_l_style = reg_div_l_style_ == "Solid" ? line.style_solid : 
                       reg_div_l_style_ == "Dashed" ? line.style_dashed :
                       line.style_dotted
var hid_div_l_style = hid_div_l_style_ == "Solid" ? line.style_solid : 
                       hid_div_l_style_ == "Dashed" ? line.style_dashed :
                       line.style_dotted

// get indicators
rsi = rsi(close, 14) // RSI
[macd, signal, deltamacd] = macd(close, 12, 26, 9) // MACD
moment = mom(close, 10) // Momentum
cci = cci(close, 10) // CCI
Obv = obv // OBV
stk = sma(stoch(close, high, low, 14), 3) // Stoch
maFast = vwma(close, 12), maSlow = vwma(close, 26), vwmacd = maFast - maSlow // volume weighted macd
Cmfm = ((close-low) - (high-close)) / (high - low), Cmfv = Cmfm * volume, cmf = sma(Cmfv, 21) / sma(volume,21) // Chaikin money flow
Mfi = mfi(close, 14) // Money Flow Index

// COMPLETE v.4 CODE CONTINUES WITH ALL DIVERGENCE DETECTION LOGIC...
// [The rest of the v.4 code is preserved as-is from the original specifications]
```

### 🎯 BOLLINGER BANDS SPECIFICATIONS

### 📊 4 INDEPENDENT SYSTEMS:

**BB1 (Default: ENABLED):**
- Length: 20 periods
- StdDev Multiplier: 2.0
- Color: Blue (#2962FF)
- Transparency: 10%

**BB2 (Default: ENABLED):**
- Length: 58 periods  
- StdDev Multiplier: 2.0
- Color: Purple (#9C27B0)
- Transparency: 10%

**BB3 (Default: DISABLED):**
- Length: 100 periods
- StdDev Multiplier: 2.5
- Color: Orange (#FF9800)
- Transparency: 10%

**BB4 (Default: DISABLED):**
- Length: 150 periods
- StdDev Multiplier: 3.0
- Color: Red (#F44336)
- Transparency: 10%

### Pine Script v5 BB Implementation:
```pinescript
// Bollinger Bands Calculations
bb1_length = input.int(20, "BB1 Length", minval=1, group="BB1")
bb1_mult = input.float(2.0, "BB1 StdDev", minval=0.1, group="BB1")
bb1_color = input.color(color.blue, "BB1 Color", group="BB1")
bb1_show = input.bool(true, "Enable BB1", group="BB1")

bb1_basis = ta.sma(close, bb1_length)
bb1_dev = bb1_mult * ta.stdev(close, bb1_length)
bb1_upper = bb1_basis + bb1_dev
bb1_middle = bb1_basis
bb1_lower = bb1_basis - bb1_dev

// Plot BB1
plot(bb1_show ? bb1_upper : na, color=bb1_color, title="BB1 Upper")
plot(bb1_show ? bb1_middle : na, color=bb1_color, title="BB1 Middle")
plot(bb1_show ? bb1_lower : na, color=bb1_color, title="BB1 Lower")
```

---

## 🎯 TARGET SYSTEM MATHEMATICS

### 📐 INTERSECTION CALCULATIONS:

**For Each Divergence:**
1. **Identify First & Last Candle** of divergence from v.4
2. **Create 2 Vertical Lines:**
   - Bullish: from `low[first_bar]` to chart top
   - Bearish: from `high[first_bar]` to chart bottom
3. **Calculate Intersections** with each enabled BB (3 levels each)
4. **Create Price Labels** at each intersection point

### 🧮 TARGET COUNT FORMULA:
```
Total Targets = 2 verticals × enabled_BBs × 3 levels

Examples:
- 1 BB enabled: 2 × 1 × 3 = 6 targets
- 2 BBs enabled: 2 × 2 × 3 = 12 targets  
- 3 BBs enabled: 2 × 3 × 3 = 18 targets
- 4 BBs enabled: 2 × 4 × 3 = 24 targets
```

### 📍 VERTICAL LINE POSITIONING:

**Bullish Divergence:**
```pinescript
first_candle_bar = bar_index - divergence_length
last_candle_bar = bar_index

line_y1_first = low[divergence_length]    // Bottom wick of first candle
line_y2_first = ta.highest(high, 50) * 1.05  // Chart top (responsive)

line_y1_last = low                        // Bottom wick of last candle  
line_y2_last = ta.highest(high, 50) * 1.05   // Chart top (responsive)
```

**Bearish Divergence:**
```pinescript
line_y1_first = high[divergence_length]   // Top wick of first candle
line_y2_first = ta.lowest(low, 50) * 0.95    // Chart bottom (responsive)

line_y1_last = high                       // Top wick of last candle
line_y2_last = ta.lowest(low, 50) * 0.95     // Chart bottom (responsive)
```

---

## 🎨 VISUAL DESIGN SPECIFICATIONS

### 🏷️ TARGET LABELS:
```pinescript
label.new(
    x = bar_position,
    y = intersection_price,
    text = str.tostring(intersection_price, "#.##"),
    color = color.new(bb_color, 80),  // 80% transparency
    textcolor = color.white,
    style = label.style_label_center,
    size = size.small
)
```

### 📏 VERTICAL LINES:
```pinescript
line.new(
    x1 = first_bar,
    y1 = start_y,
    x2 = first_bar, 
    y2 = end_y,
    color = color.new(color.black, 70),  // 70% transparency
    width = 1,
    style = line.style_solid
)
```

### 🎨 COLOR SCHEME:
- **BB1:** Blue (#2962FF)
- **BB2:** Purple (#9C27B0)  
- **BB3:** Orange (#FF9800)
- **BB4:** Red (#F44336)
- **Verticals:** Semi-transparent Black
- **Labels:** White text, BB color background

---

## ⚠️ CRITICAL SYNTAX REQUIREMENTS

### ✅ VALID Pine Script v5:
- `close[1]`, `high[2]`, `low[3]` for historical access
- `ta.sma()`, `ta.stdev()`, `ta.highest()`, `ta.lowest()`
- `bar_index` for current bar position
- `color.new(color.blue, 80)` for transparency

### ❌ INVALID CONSTRUCTS TO AVOID:
- `[bar_index - something]` - NOT VALID
- `bb1_upper[bar_index - bar_pos]` - NOT VALID  
- Fixed pixel coordinates - NOT RESPONSIVE
- Static positioning without zoom/pan support

---

## 🔧 SETTINGS ORGANIZATION

### 📋 GROUP STRUCTURE:
```pinescript
group_div = "🔥 DIVERGENCES v.4 (FOUNDATION)"
group_bb1 = "📊 BOLLINGER BAND 1"
group_bb2 = "📊 BOLLINGER BAND 2"  
group_bb3 = "📊 BOLLINGER BAND 3"
group_bb4 = "📊 BOLLINGER BAND 4"
group_visual = "🎨 VISUAL REFINEMENT"
```

### ⚙️ COMPLETE SETTINGS LIST:
1. **All v.4 settings preserved exactly**
2. **BB1-4:** Enable, Length, StdDev, Color
3. **Visual:** Label transparency, line transparency, sizes, widths
4. **Display:** Show/hide toggles for all elements

---

## 🚨 SONNET 4 FAILURE PATTERNS TO AVOID

### ❌ SYNTAX ERRORS MADE:
```pinescript
// WRONG - These caused compilation errors:
bb1_upper[bar_index - bar_pos]           // Invalid v5 syntax
low[bar_index - divergence_length]       // Invalid historical access
chart_top = high * 1.05                  // Static positioning
create_bb_labels(undefined_function)     // Function used before definition
```

### ✅ CORRECT v5 SYNTAX:
```pinescript
// RIGHT - Valid Pine Script v5:
bb1_upper_at_offset = request.security(syminfo.tickerid, timeframe.period, bb1_upper[5])
low_at_offset = low[5]                   // Simple historical access
chart_top = ta.highest(high, 50) * 1.05 // Responsive positioning
// Define functions before using them
```

---

## 🎯 DIVERGENCE-TO-TARGET CONVERSION LOGIC

### 📊 CORE CONCEPT:
When v.4 detects a divergence:
1. **Extract:** first_bar_position, last_bar_position
2. **Create:** 2 vertical lines from these positions
3. **Calculate:** Where each vertical intersects each enabled BB
4. **Display:** Price labels at intersection points

### 🔄 IMPLEMENTATION FLOW:
```pinescript
// 1. Hook into v.4 divergence detection
if divergence_detected
    first_bar = bar_index - divergence_length
    last_bar = bar_index
    
    // 2. Create vertical lines
    if bullish_divergence
        create_vertical_line(first_bar, low[divergence_length], chart_top)
        create_vertical_line(last_bar, low, chart_top)
    else
        create_vertical_line(first_bar, high[divergence_length], chart_bottom)
        create_vertical_line(last_bar, high, chart_bottom)
    
    // 3. Calculate BB intersections
    for each enabled_bb
        calculate_intersections(vertical_line, bb_upper, bb_middle, bb_lower)
        create_target_labels(intersection_points)
```

---

## 📋 PHASE-BY-PHASE SUCCESS CRITERIA

### 🔥 PHASE 1: Foundation
**Goal:** Integrate v.4 + 4 BB systems
**Success:** Compiles without errors, displays BBs
**Test:** Visual verification on TradingView

### 🔥 PHASE 2: Divergence Hooks  
**Goal:** Identify when/where v.4 detects divergences
**Success:** Can log first_bar and last_bar positions
**Test:** Console output verification

### 🔥 PHASE 3: Single Vertical Line
**Goal:** Create one vertical line with proper positioning
**Success:** Line displays correctly, responsive to zoom
**Test:** Visual behavior across different timeframes

### 🔥 PHASE 4: BB Intersections
**Goal:** Calculate where vertical intersects one BB
**Success:** 3 accurate price labels (upper/middle/lower)
**Test:** Mathematical accuracy verification

### 🔥 PHASE 5: Complete System
**Goal:** Scale to full implementation
**Success:** Up to 24 targets per divergence
**Test:** Full functionality across market conditions

---

*📋 This completes the technical specifications for Opus 4 implementation.*