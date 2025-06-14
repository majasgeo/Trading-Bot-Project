# 🎯 OPUS 4 PROMPT SEQUENCE
## Step by Step Instructions

### 📋 INITIAL CHAT SETUP

**Send ALL of these prompts in order. Do NOT skip any step.**

---

## 🔥 PROMPT 1: CAPABILITY ASSESSMENT

```
CRITICAL SELF-ASSESSMENT REQUIRED:

Before starting this Pine Script project, I need an HONEST evaluation of your capabilities:

1. **Pine Script v5 Expertise Check:**
   - Do you know correct syntax for historical data access? (e.g., close[1], close[2])
   - Can you avoid invalid [bar_index - something] constructs?
   - Can you implement coordinate geometry calculations in Pine Script?
   - Can you create responsive positioning that scales with zoom/pan?

2. **Complex Logic Understanding:**
   - Do you understand "divergence-to-target conversion" concept?
   - Can you connect divergence detection with intersection calculations?
   - Can you calculate where vertical lines intersect Bollinger Bands?

3. **Track Record Awareness:**
   Another Claude (Sonnet 4) FAILED CATASTROPHICALLY on this project:
   - 2 completely wrong implementations
   - Multiple syntax errors
   - False verification claims ("✅ VERIFIED" without testing)
   - 0% working code after extensive attempts

**INSTRUCTION:** IF you are NOT 90%+ confident you can do this CORRECTLY, DECLARE IT NOW.
Don't attempt if you lack solid Pine Script v5 knowledge.

Answer ONLY: "READY" or "NOT READY" with brief explanation.
```

---

## 🔥 PROMPT 2: PROJECT SPECIFICATIONS (ONLY IF "READY")

```
PROJECT SPECIFICATIONS - READ CAREFULLY:

**OBJECTIVE:** Divergence MultiIndicator Double BBands MINIMAL

**CORE STRUCTURE:**
- FORBIDDEN to change "Divergence for Many Indicators v.4"
- Must preserve ALL v.4 elements untouched
- 4 independent Bollinger Bands systems
- Universal timeframe compatibility

**MAIN FUNCTION (4 STEPS):**

Step 1: v.4 Divergence Detection (UNTOUCHED)
- 11 indicators: MACD, MACD Histogram, RSI, Stochastic, CCI, Momentum, OBV, VW MACD, CMF, MFI, External
- All v.4 functions preserved 100%

Step 2: Smart Vertical Lines Creation
- **FOR EACH DIVERGENCE** detected by v.4:
- 2 vertical lines: first candle + last candle of divergence
- BULLISH: from bottom wick → chart top
- BEARISH: from top wick → chart bottom

Step 3: Intersection Calculation
- Each vertical intersects ALL enabled BB bands
- 3 intersections per BB (upper, middle, lower)

Step 4: Target Price Labels
- At intersections: label with price only (e.g., "67,450.25")
- Semi-transparent background matching BB color

**MATHEMATICS:**
- 1 BB enabled: 6 targets (2 verticals × 3 levels)
- 2 BBs enabled: 12 targets
- 3 BBs enabled: 18 targets
- 4 BBs enabled: 24 targets

**RESPONSIVENESS:**
- 100% Native TradingView coordinates
- Elastic behavior - scales with zoom/pan
- NO static positioning
- NO [bar_index - something] syntax

**QUESTION:** Do you understand EXACTLY what needs to be done?
Answer "UNDERSTOOD" or "NEED CLARIFICATION".
```

---

## 🔥 PROMPT 3: IMPLEMENTATION APPROACH (ONLY IF "UNDERSTOOD")

```
IMPLEMENTATION STRATEGY:

**STEP-BY-STEP APPROACH:**

**Phase 1:** Foundation Only
- Copy v.4 code 100% as-is
- Add only the 4 BB systems
- CMF calculation: manual (ta.cmf doesn't exist)
- TEST first - must run without errors

**Phase 2:** Divergence Hook
- Find WHERE exactly v.4 detects divergences
- Identify: first candle position, last candle position
- ONLY identification - no targets yet

**Phase 3:** Single Vertical Line (Test)
- Create ONE vertical line for testing
- Correct Pine Script v5 syntax for positioning
- TEST - must display correctly

**Phase 4:** BB Intersection (Test)
- Calculate intersections of ONE vertical with ONE BB
- 3 target labels only
- TEST - must appear at correct positions

**Phase 5:** Complete System
- Extend to all BBs and 2 verticals
- Full target mathematics

**CRITICAL REQUIREMENTS:**
1. Each phase must run without syntax errors
2. IF you get stuck at any phase, STOP and declare it
3. NO false verification claims
4. Use only VALID Pine Script v5 syntax

**QUESTION:** Ready for Phase 1? Answer "START PHASE 1" or "NEED MORE INFO".
```

---

## 🔥 PROMPT 4: QUALITY CONTROL

```
VERIFICATION PROTOCOL:

After each phase:

**SYNTAX CHECK:**
- All parentheses balanced?
- All functions defined before use?
- Using ONLY valid v5 syntax?
- NO [bar_index - something] constructs?

**LOGIC CHECK:**
- Do vertical lines connect to actual divergences?
- Are intersections calculated correctly?
- Do targets appear at correct positions?

**RESPONSIVENESS CHECK:**
- Using native TradingView coordinates?
- All elements scale with zoom/pan?
- NO static positioning?

**SELF-ASSESSMENT QUESTIONS:**
1. "Am I 100% sure about the syntax?"
2. "Have I checked the logic step-by-step?"
3. "Will this run without errors on TradingView?"

**HONESTY REQUIREMENT:**
IF the answer to ANY question is "no" or "not sure":
- STOP immediately
- DECLARE the uncertainty
- DON'T continue with false confidence

Do you understand the verification process? Answer "VERIFICATION UNDERSTOOD".
```

---

## 🔥 PROMPT 5: FINAL COMMITMENT

```
FINAL WARNING - READ CAREFULLY:

Another Claude failed on this project with:
- False confidence claims
- Syntax errors it didn't detect
- Logic that didn't work
- False "✅ VERIFIED" statements

**COMMITMENT REQUIRED:**

I commit that I will:
□ Only do what I know for certain
□ Stop if I get stuck
□ NOT make false verification claims
□ Be honest about any uncertainty
□ Admit failure if necessary

**FINAL QUESTION:**
Are you ready to take this responsibility with COMPLETE HONESTY?

Answer: "I COMMIT TO HONEST IMPLEMENTATION" or "I CANNOT GUARANTEE SUCCESS".

If you answer the second, it will be RESPECTED and COMMENDABLE.
If you answer the first, you will be judged by STRICT criteria.

What do you choose?
```

---

## 📋 USAGE INSTRUCTIONS

### 🎯 FOR MAXIMUM SUCCESS:

1. **Copy each prompt EXACTLY** - don't modify
2. **Wait for clear answers** before proceeding to next prompt
3. **Stop if Opus 4 shows ANY uncertainty**
4. **Demand honesty over confidence**

### ✅ SUCCESS INDICATORS:
- Opus 4 answers "READY" with confidence
- Clear understanding demonstrated at each step
- Honest self-assessment throughout process
- Willingness to admit limitations if they exist

### 🚨 RED FLAGS TO WATCH FOR:
- Overconfidence without demonstration
- Rushing through prompts
- Generic answers without specifics
- Any hint of false verification

---

## 🎯 EXPECTED OUTCOME

**IF Opus 4 is truly ready:** Professional, working Pine Script indicator
**IF Opus 4 is honest about limitations:** Respectful acknowledgment and alternative suggestions

**Both outcomes are VALUABLE.**

The goal is HONEST ASSESSMENT and QUALITY IMPLEMENTATION, not false promises.

---

*Ready to transfer to Opus 4. Good luck!* 🚀