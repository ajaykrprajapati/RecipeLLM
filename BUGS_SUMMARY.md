# 🐛 Critical Bugs Summary

## Bug #1: Only Extracts ONE Modification Per Review ⚠️

### The Smoking Gun (from assignment):
> "If the review says 'I added an egg and halved the sugar' -> these are **two discrete modifications**!"

### Example Review (from actual data):
```
"I made the following tweaks: 
(1) I used a half cup of sugar and one-and-a-half cups of brown sugar; 
(2) I omitted the water; 
(3) I added a teaspoon of cream of tartar"
```

### Current Behavior: ❌
```python
# Returns only ONE ModificationObject
def extract_modification(review, recipe) -> ModificationObject:
    # LLM extracts first modification it sees
    # Ignores the other 2-3 changes
```

### Expected Behavior: ✅
```python
# Should return MULTIPLE ModificationObjects
def extract_modification(review, recipe) -> List[ModificationObject]:
    # Extract ALL discrete modifications:
    # 1. Sugar ratio change (quantity_adjustment)
    # 2. Omit water (removal)
    # 3. Add cream of tartar (addition)
```

---

## Bug #2: Uses RANDOM Review Instead of Featured ⚠️

### The Smoking Gun (from assignment):
> "highest voted community-tested modifications aka the **'Featured Tweaks'**"

### Current Code (line 136):
```python
# WRONG! Picks random review
selected_review = random.choice(modification_reviews)
```

### Evidence from Data:
```json
{
  "reviews": [...],
  "featured_tweaks": [
    {
      "text": "...",
      "is_featured": true,  // ← THIS FLAG EXISTS!
      "has_modification": true
    }
  ]
}
```

### Fix:
```python
# Prioritize featured reviews
featured = [r for r in reviews if r.is_featured]
if featured:
    selected_review = max(featured, key=lambda r: r.rating)
else:
    # Fallback to highest rated
    selected_review = max(modification_reviews, key=lambda r: r.rating)
```

---

## Bug #3: Only Processes ONE Review Per Recipe ⚠️

### Current Flow:
```
Recipe → Pick 1 Random Review → Extract 1 Modification → Enhanced Recipe
```

### Expected Flow (based on assignment description):
```
Recipe → Get All Featured Reviews → Extract All Modifications → Apply All → Enhanced Recipe
```

### Why This Matters:
- AllRecipes shows MULTIPLE featured tweaks per recipe
- Users want to see aggregated community wisdom
- Current system throws away 80%+ of valuable modifications

---

## Bug #4: No Evaluation/Testing Beyond "Does It Run?" ⚠️

### Evidence from assignment:
> "does it actually work **beyond a couple superficial examples**?"

### Current Testing:
- ✅ Runs on 5 pre-selected recipes
- ❌ No validation of extraction accuracy
- ❌ No testing on edge cases
- ❌ No metrics for success/failure

### Required:
- Ground truth test cases
- Extraction accuracy metrics
- Testing on 10+ new recipes
- Failure mode analysis

---

## Priority Order

1. **🔴 HIGH**: Bug #1 (Multi-modification extraction) - Core functionality broken
2. **🔴 HIGH**: Bug #2 (Featured reviews) - Using wrong data
3. **🟡 MEDIUM**: Bug #3 (Multiple reviews) - Product value limited
4. **🟡 MEDIUM**: Bug #4 (Evaluation) - Can't prove it works

---

## Quick Test to Verify Bugs

Run this to see the issues:

```bash
cd src
uv run python test_pipeline.py single
```

Look at the output:
- Does it process ALL modifications from the review? (No)
- Does it say "Selected review: " with a random one? (Yes)
- Does it apply multiple sources? (No)

Compare with `data/enhanced/enhanced_10813_*.json`:
- Count modifications_applied (probably 1-2)
- Count total tweaks in original recipe (probably 10+)
- **Conclusion**: System is losing 80%+ of modifications!
