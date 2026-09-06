# Implementation Checklist (4 Hour Plan)

## ⏰ Hour 1: Fix Core Extraction Bug

### Task 1.1: Update Models for Multi-Modification Support (10 min)
- [ ] Open `src/llm_pipeline/models.py`
- [ ] Verify `ModificationObject` can handle being in a list
- [ ] No changes likely needed (Pydantic handles lists well)

### Task 1.2: Update Prompts (15 min)
- [ ] Open `src/llm_pipeline/prompts.py`
- [ ] Update `SYSTEM_PROMPT` to explicitly say:
  ```
  "Extract ALL discrete modifications from the review as a JSON array.
  Each modification should be a separate object.
  Example: 'I added an egg and halved sugar' = 2 modifications"
  ```
- [ ] Update expected output format to be an array:
  ```json
  [
    {
      "modification_type": "...",
      "reasoning": "...",
      "edits": [...]
    },
    {
      "modification_type": "...",
      "reasoning": "...",
      "edits": [...]
    }
  ]
  ```

### Task 1.3: Update Tweak Extractor (20 min)
- [ ] Open `src/llm_pipeline/tweak_extractor.py`
- [ ] Change `extract_modification()` return type:
  ```python
  def extract_modification(
      self, review: Review, recipe: Recipe
  ) -> Optional[List[ModificationObject]]:  # Changed!
  ```
- [ ] Update JSON parsing to handle array:
  ```python
  modifications_data = json.loads(raw_output)
  if isinstance(modifications_data, dict):
      modifications_data = [modifications_data]  # Handle single mod
  modifications = [ModificationObject(**m) for m in modifications_data]
  ```
- [ ] Update `extract_single_modification()` to return list

### Task 1.4: Quick Test (15 min)
- [ ] Create a test script with a multi-modification review
- [ ] Verify it extracts ALL modifications
- [ ] Fix any issues

---

## ⏰ Hour 2: Fix Selection Logic & Multiple Reviews

### Task 2.1: Add Featured Review Prioritization (20 min)
- [ ] Update `extract_single_modification()` to:
  ```python
  # Prioritize featured reviews
  featured_reviews = [r for r in reviews if getattr(r, 'is_featured', False)]
  
  if featured_reviews:
      # Sort by rating, pick highest
      selected_review = max(featured_reviews, key=lambda r: r.rating or 0)
  else:
      # Fallback to highest rated modification
      mod_reviews = [r for r in reviews if r.has_modification]
      selected_review = max(mod_reviews, key=lambda r: r.rating or 0)
  ```
- [ ] Add `is_featured` field to `Review` model if missing

### Task 2.2: Update Pipeline for Multiple Reviews (30 min)
- [ ] Open `src/llm_pipeline/pipeline.py`
- [ ] Create new method `process_multiple_reviews()`:
  ```python
  def process_multiple_reviews(
      self, reviews: List[Review], recipe: Recipe, max_reviews: int = 5
  ) -> List[Tuple[ModificationObject, Review]]:
      """Extract modifications from top N featured reviews."""
      # Get featured reviews
      # Extract modifications from each
      # Return all modification-review pairs
  ```
- [ ] Update `process_single_recipe()` to use this method
- [ ] Update `RecipeModifier.apply_modifications_batch()` to apply all

### Task 2.3: Update Enhanced Recipe Structure (10 min)
- [ ] Verify `modifications_applied` can handle multiple sources
- [ ] Already a List[ModificationApplied], should be fine
- [ ] Test the flow

---

## ⏰ Hour 3: Build Evaluation Framework

### Task 3.1: Create Ground Truth Test Cases (25 min)
- [ ] Create `tests/test_extraction_accuracy.py`
- [ ] Add 5-10 reviews with manually labeled expected modifications
- [ ] Example:
  ```python
  TEST_CASES = [
      {
          "review": "I added an egg and halved the sugar",
          "expected_modifications": [
              {"type": "addition", "ingredient": "egg"},
              {"type": "quantity_adjustment", "ingredient": "sugar"}
          ],
          "expected_count": 2
      }
  ]
  ```

### Task 3.2: Build Evaluation Metrics (20 min)
- [ ] Create `src/evaluation/metrics.py`
- [ ] Implement:
  ```python
  def calculate_extraction_accuracy(
      extracted: List[ModificationObject],
      expected: List[dict]
  ) -> dict:
      """
      Returns:
      - precision: % of extracted mods that are correct
      - recall: % of expected mods that were found
      - f1: harmonic mean
      """
  ```

### Task 3.3: Run Evaluation (15 min)
- [ ] Test against ground truth cases
- [ ] Document accuracy before/after fixes
- [ ] Identify failure modes

---

## ⏰ Hour 4: Testing, Documentation & Video Prep

### Task 4.1: Extended Testing (20 min)
- [ ] Test on all 6 existing recipes
- [ ] Compare before/after results
- [ ] Document:
  - # modifications extracted (before vs after)
  - # reviews processed (before vs after)
  - Success rate

### Task 4.2: Write Documentation (30 min)
- [ ] Create `SOLUTION.md` with:
  - **Problem Analysis**: What was broken and how you found it
  - **Solution Approach**: What you fixed and why
  - **Technical Decisions**: Key choices and trade-offs
  - **Results**: Before/after metrics
  - **Future Improvements**: What's next
- [ ] Be specific with code examples and data

### Task 4.3: Video Preparation (10 min)
- [ ] Outline 3 key demo points:
  1. Show the bug (single mod extraction)
  2. Show the fix (multiple mods extracted)
  3. Show results (metrics improvement)
- [ ] Prepare screen recording setup
- [ ] Have key files open and ready

---

## Quick Commands Reference

```bash
# Setup environment
cd /Users/ajayprajapati/Documents/code/casper/ai-eng-assignment
source .venv/bin/activate

# Test single recipe
cd src
uv run python test_pipeline.py single

# Test all recipes
uv run python test_pipeline.py all

# Run evaluation (after creating it)
uv run python -m pytest tests/test_extraction_accuracy.py -v

# Check output
cat data/enhanced/enhanced_10813_*.json | jq '.modifications_applied | length'
```

---

## Success Criteria Checklist

### Functionality
- [ ] Extracts ALL modifications from a single review (not just one)
- [ ] Prioritizes featured reviews over random ones
- [ ] Processes multiple reviews per recipe (not just one)
- [ ] Has evaluation framework with metrics

### Code Quality
- [ ] Changes are clean and well-documented
- [ ] Type hints are correct
- [ ] Logging shows what's happening
- [ ] No breaking changes to existing valid functionality

### Documentation
- [ ] Clear problem diagnosis
- [ ] Explained solution approach
- [ ] Technical decisions justified
- [ ] Results quantified with metrics
- [ ] Future improvements identified

### Presentation
- [ ] 5-7 minute video recorded
- [ ] Shows problem, solution, results
- [ ] Clear and well-paced
- [ ] Demonstrates technical understanding

---

## Common Pitfalls to Avoid

1. **Don't over-engineer**: 4 hours is tight, focus on core bugs
2. **Don't skip evaluation**: They explicitly ask "does it work beyond examples?"
3. **Don't just fix without documenting**: Your thinking process matters
4. **Don't forget the agent trajectory**: Save this Claude conversation!
5. **Don't make UI**: Assignment says "before making a fancy UI..."

---

## Files to Commit

```
✅ src/llm_pipeline/tweak_extractor.py (modified)
✅ src/llm_pipeline/prompts.py (modified)
✅ src/llm_pipeline/pipeline.py (modified)
✅ src/llm_pipeline/models.py (possibly modified)
✅ src/evaluation/metrics.py (new)
✅ tests/test_extraction_accuracy.py (new)
✅ data/enhanced/* (new results)
✅ SOLUTION.md (new)
✅ AGENT_TRAJECTORY.md (this conversation)
✅ README.md (updated with findings)
```

Good luck! Start with Hour 1 and work systematically. 🚀
