# Complete Learning Plan: Recipe Enhancement Platform
## End-to-End Guide to Understanding This AI Engineering Project

---

## 📋 Project Overview

This is an **AI-powered Recipe Enhancement Platform** that:
- Scrapes recipes from AllRecipes.com
- Analyzes community reviews using Large Language Models (LLMs)
- Extracts recipe modifications/tweaks from reviews
- Applies those modifications to create enhanced recipes with full attribution

**Core Technologies:**
- Python 3.13+
- OpenAI API (GPT models)
- Web Scraping (BeautifulSoup)
- Data Validation (Pydantic)
- Package Management (uv)
- Fuzzy String Matching
- LLM Pipelines & Prompt Engineering

---

## 🎯 Prerequisites Assessment

### Basic Prerequisites (Must Have)
- ✅ Basic programming knowledge (variables, functions, loops)
- ✅ Command line/terminal basics
- ✅ Text editor or IDE (VS Code recommended)
- ✅ Git basics

### Skills You'll Build (Will Learn)
- Python intermediate/advanced concepts
- Working with APIs (especially OpenAI)
- LLM integration and prompt engineering
- Data processing and validation
- Web scraping techniques
- Building production-ready code

---

## 📚 Learning Path - 6 Week Plan

### **WEEK 1: Python Fundamentals & Environment Setup**

#### Topics to Cover:
1. **Python Basics Refresher**
   - Data types (strings, lists, dictionaries)
   - Functions and modules
   - Error handling (try/except)
   - File I/O operations

2. **Modern Python Package Management**
   - Understanding `uv` (the fast package manager)
   - Virtual environments
   - Managing dependencies with `pyproject.toml`

3. **Working with JSON in Python**
   - Reading/writing JSON files
   - Serialization and deserialization
   - Nested JSON structures

#### Learning Resources:

**YouTube Videos:**
- [Corey Schafer - Python Programming](https://www.youtube.com/@coreyms) - Best Python teacher on YouTube
- [Tech With Tim - Python Projects](https://www.youtube.com/@TechWithTim) - Practical Python builds
- [Programming with Mosh - Python Tutorial](https://www.youtube.com/@programmingwithmosh) - Great for beginners

**Documentation & Tutorials:**
- [Real Python - JSON in Python](https://realpython.com/python-json/) - Comprehensive JSON guide
- [DataCamp - Python JSON Tutorial](https://www.datacamp.com/tutorial/json-data-python) - Interactive learning
- [uv Package Manager Guide](https://realpython.com/python-uv/) - Complete uv tutorial
- [Python uv Official Docs](https://pydevtools.com/handbook/explanation/uv-complete-guide/) - In-depth guide

**Practice:**
- Install `uv` and set up a virtual environment
- Create a simple Python script that reads/writes JSON
- Practice with the `json` module

---

### **WEEK 2: Web Scraping & Data Extraction**

#### Topics to Cover:
1. **HTML/CSS Basics** (just enough to understand structure)
   - HTML tags and attributes
   - CSS selectors
   - DOM structure

2. **Web Scraping with BeautifulSoup**
   - Making HTTP requests
   - Parsing HTML
   - Navigating the DOM tree
   - Extracting specific data

3. **Best Practices**
   - Respecting robots.txt
   - Rate limiting
   - Error handling

#### Learning Resources:

**YouTube Videos:**
- [BeautifulSoup Web Scraping Tutorial 2026](https://www.youtube.com/watch?v=ztxIxbRyPJI) - Step-by-step scraping guide
- Search for "Python Web Scraping 2026" on YouTube for latest tutorials

**Documentation & Tutorials:**
- [ScrapingBee - Python Web Scraping 101](https://www.scrapingbee.com/blog/web-scraping-101-with-python/) - Comprehensive 2026 guide
- [DEV Community - BeautifulSoup Tutorial](https://dev.to/agenthustler/beautifulsoup-web-scraping-tutorial-in-2026-from-basics-to-advanced-techniques-pop) - From basics to advanced
- [GeeksforGeeks - BeautifulSoup](https://www.geeksforgeeks.org/python/implementing-web-scraping-python-beautiful-soup/) - Step-by-step guide

**Practice:**
- Scrape a simple website (like quotes.toscrape.com)
- Extract recipe data from a single AllRecipes page
- Handle pagination and multiple pages

---

### **WEEK 3: Data Validation with Pydantic**

#### Topics to Cover:
1. **Type Hints in Python**
   - Basic type annotations
   - Optional types
   - List and Dict type hints

2. **Pydantic Models**
   - Creating data models
   - Automatic validation
   - Data coercion
   - Custom validators

3. **Structured Data**
   - Nested models
   - Validation errors
   - Serialization

#### Learning Resources:

**YouTube Videos:**
- [Pydantic Complete Data Validation Course](https://www.youtube.com/watch?v=M81pfi64eeM) - Used by FastAPI
- Search for "Pydantic tutorial 2026" for latest content

**Documentation & Tutorials:**
- [Real Python - Pydantic Tutorial](https://realpython.com/python-pydantic/) - Comprehensive guide
- [KDnuggets - Pydantic Made Simple](https://www.kdnuggets.com/pydantic-tutorial-data-validation-in-python-made-simple) - Beginner-friendly
- [Pydantic Official Docs](https://pydantic.dev/docs/validation/latest/get-started/) - Official documentation
- [Medium - Pydantic V2 Tutorial](https://medium.com/@akashbaidya2/pydantic-v2-tutorial-mastering-data-validation-in-python-with-pydantic-v2-0a2dbbd3f5e7) - Mastering Pydantic V2

**Practice:**
- Create Pydantic models for Recipe, Review, and Modification
- Add custom validators
- Handle validation errors gracefully

---

### **WEEK 4: OpenAI API & LLM Integration**

#### Topics to Cover:
1. **Understanding Large Language Models**
   - What are LLMs?
   - Use cases and capabilities
   - Limitations and considerations

2. **OpenAI API Basics**
   - API keys and authentication
   - Making API calls
   - Understanding models (GPT-5, GPT-5-mini, etc.)
   - Pricing and rate limits

3. **JSON Mode & Structured Outputs**
   - Forcing JSON responses
   - Schema validation
   - Consistent output formatting

#### Learning Resources:

**YouTube Videos:**
- [How to Use OpenAI API with Python - 2026 Tutorial](https://www.youtube.com/watch?v=tREkBoLhLeU) - Latest tutorial
- Search for "OpenAI API Python 2026" for current content

**Documentation & Tutorials:**
- [OpenAI Official Docs - Structured Outputs](https://developers.openai.com/api/docs/guides/structured-outputs) - Essential reading
- [AskPython - OpenAI SDK Complete Guide](https://www.askpython.com/python/openai-python-sdk-developer-guide) - Developer guide 2026
- [Machine Learning Plus - OpenAI API Tutorial](https://machinelearningplus.com/gen-ai/openai-api-python-tutorial/) - Chat completions & streaming
- [Medium - Getting Structured Outputs](https://medium.com/@piyushsonawane10/getting-structured-outputs-from-openai-models-a-developers-guide-3090e8120785) - Developer's guide
- [Haystack - Structured Output Tutorial](https://haystack.deepset.ai/tutorials/28_structured_output_with_openai) - Practical examples

**Practice:**
- Get an OpenAI API key
- Make your first API call
- Use JSON mode to get structured responses
- Implement retry logic and error handling

---

### **WEEK 5: Prompt Engineering & LLM Pipelines**

#### Topics to Cover:
1. **Prompt Engineering Fundamentals**
   - Writing clear, specific prompts
   - Few-shot learning
   - System vs user messages
   - Temperature and parameters

2. **Advanced Prompting Techniques**
   - Structured prompts
   - Chain-of-thought reasoning
   - Iterative refinement
   - Handling edge cases

3. **Building LLM Pipelines**
   - Multi-step processing
   - Data flow design
   - Error handling strategies
   - Performance optimization

#### Learning Resources:

**YouTube Videos:**
- [Master LLM Prompt Engineering - 2026 Guide](https://www.youtube.com/watch?v=uTWvJIqsM_I) - Complete guide

**Documentation & Tutorials:**
- [Prompt Engineering Guide 2026](https://promptengineering.guide/) - Comprehensive reference
- [The AI Corner - 2026 Guide to Prompt Engineering](https://www.the-ai-corner.com/p/your-2026-guide-to-prompt-engineering) - How to get 10x more from AI
- [Medium - Prompt Engineering Series](https://medium.com/codetodeploy/prompt-engineering-2026-series-0-introduction-3e331e955433) - State of the art techniques
- [IBM - The 2026 Guide to Prompt Engineering](https://www.ibm.com/think/prompt-engineering) - Enterprise perspective

**Courses:**
- [Udemy - Master LLM Prompt Engineering](https://www.udemy.com/course/gen-ai-master-llm-prompt-engineering/) - Complete course

**Practice:**
- Create prompts for extracting recipe modifications
- Test different prompt structures
- Handle ambiguous inputs
- Build a simple 2-step LLM pipeline

---

### **WEEK 6: Fuzzy Matching, Debugging & Testing**

#### Topics to Cover:
1. **Fuzzy String Matching**
   - Levenshtein distance
   - FuzzyWuzzy/TheFuzz library
   - Matching ingredients in recipes
   - Handling variations

2. **Logging & Debugging**
   - Using Loguru for logging
   - Log levels and structured logging
   - Exception capture
   - Production debugging

3. **Testing & Evaluation**
   - Unit testing basics
   - LLM evaluation metrics
   - Quality assurance
   - Building test cases

#### Learning Resources:

**Fuzzy Matching:**
- [DataCamp - Fuzzy String Matching](https://www.datacamp.com/tutorial/fuzzy-string-python) - Complete tutorial
- [GeeksforGeeks - FuzzyWuzzy Library](https://www.geeksforgeeks.org/python/fuzzywuzzy-python-library/) - Library guide
- [Analytics Vidhya - Fuzzy Matching Guide](https://www.analyticsvidhya.com/blog/2021/07/fuzzy-string-matching-a-hands-on-guide/) - Hands-on guide
- [Medium - FuzzyWuzzy Comprehensive Guide](https://medium.com/@alphaiterations/fuzzy-matching-with-fuzzywuzzy-a-comprehensive-guide-04873f07de31) - Complete guide

**Logging & Debugging:**
- [Real Python - Loguru Tutorial](https://realpython.com/python-loguru/) - Simpler Python logging
- [Dash0 - Python Logging with Loguru](https://www.dash0.com/guides/python-logging-with-loguru) - Setup to production
- [DataCamp - Loguru Tutorial](https://www.datacamp.com/tutorial/loguru-python-logging-tutorial) - Zero configuration setup
- [Better Stack - Complete Guide to Loguru](https://betterstack.com/community/guides/logging/loguru/) - Comprehensive guide

**LLM Evaluation:**
- [Openlayer - LLM Evaluation Metrics Guide](https://www.openlayer.com/blog/llm-evaluation-metrics-complete-guide) - Complete guide March 2026
- [WeTest - 33 LLM Evaluation Metrics](https://www.wetest.net/blog/33-llm-evaluation-metrics-1235.html) - Performance, quality & cost
- [DeepEval - Top 5 Frameworks](https://deepeval.com/blog/top-5-llm-evaluation-frameworks) - Framework comparison
- [FutureAGI - Evaluating LLM Systems](https://futureagi.com/blog/evaluating-llm-systems-metrics-benchmarks-2026/) - Metrics and benchmarks

**Practice:**
- Implement fuzzy matching for ingredient names
- Add comprehensive logging to your code
- Create test cases for the pipeline
- Build evaluation metrics

---

## 🎓 Additional Learning Resources

### Best Python YouTube Channels (2026)

**For Beginners:**
- [Corey Schafer](https://www.youtube.com/@coreyms) - Best Python teacher on YouTube
- [Programming with Mosh](https://www.youtube.com/@programmingwithmosh) - Clear, professional content
- [freeCodeCamp](https://www.youtube.com/@freecodecamp) - Structured foundations
- [Bro Code](https://www.youtube.com/@BroCodez) - Fast, practical tutorials
- [CS Dojo](https://www.youtube.com/@CSDojo) - Great for newcomers

**For Intermediate/Advanced:**
- [Tech With Tim](https://www.youtube.com/@TechWithTim) - Build real projects
- [Sentdex](https://www.youtube.com/@sentdex) - Advanced topics, AI, and data science
- [ArjanCodes](https://www.youtube.com/@ArjanCodes) - Clean code and best practices

### Documentation & Official Resources

1. **Python Official Docs** - https://docs.python.org/3/
2. **OpenAI API Documentation** - https://developers.openai.com/docs
3. **Pydantic Documentation** - https://docs.pydantic.dev/
4. **BeautifulSoup Docs** - https://www.crummy.com/software/BeautifulSoup/bs4/doc/
5. **Loguru Documentation** - https://loguru.readthedocs.io/

### Interactive Learning Platforms

1. **Real Python** - https://realpython.com/ (Premium tutorials)
2. **DataCamp** - https://www.datacamp.com/ (Interactive courses)
3. **freeCodeCamp** - https://www.freecodecamp.org/ (Free courses)
4. **Kaggle Learn** - https://www.kaggle.com/learn (Free Python courses)

---

## 🚀 Project-Specific Learning Path

### Phase 1: Understanding the Codebase (Week 1-2)

**Goals:**
- Read and understand the existing code
- Identify the data flow
- Understand the problem domain

**Tasks:**
1. Read `README.md` and `ANALYSIS_AND_STRATEGY.md`
2. Explore the `src/` directory structure
3. Look at sample data in `data/` directory
4. Run the pipeline: `uv run python test_pipeline.py single`
5. Examine the output JSON files

**Key Files to Study:**
- `src/llm_pipeline/models.py` - Data structures (Pydantic models)
- `src/llm_pipeline/tweak_extractor.py` - LLM extraction logic
- `src/llm_pipeline/prompts.py` - Prompt templates
- `src/llm_pipeline/pipeline.py` - Main processing pipeline
- `src/scraper_v2.py` - Web scraping implementation

---

### Phase 2: Learning by Fixing (Week 3-4)

**Goals:**
- Understand the bugs in the system
- Learn by implementing fixes
- Build debugging skills

**Identified Issues to Fix:**

1. **Multi-Modification Extraction Bug**
   - Current: Only extracts ONE modification per review
   - Should: Extract ALL modifications (e.g., "added egg AND halved sugar" = 2 mods)
   - File: `src/llm_pipeline/tweak_extractor.py`
   - Learning: Prompt engineering, JSON arrays, Pydantic list validation

2. **Featured Review Selection Bug**
   - Current: Random selection of reviews
   - Should: Prioritize `is_featured: true` reviews
   - File: `src/llm_pipeline/tweak_extractor.py` line 136
   - Learning: Data filtering, sorting algorithms

3. **Single Review Processing**
   - Current: Only processes 1 review per recipe
   - Should: Process multiple featured modifications
   - File: `src/llm_pipeline/pipeline.py`
   - Learning: Iteration, aggregation, conflict resolution

4. **No Validation/Evaluation**
   - Current: No metrics to measure success
   - Should: Build evaluation framework
   - New files needed: `src/evaluation/`
   - Learning: Testing, metrics, quality assurance

---

### Phase 3: Building Evaluation (Week 5)

**Goals:**
- Understand how to evaluate LLM systems
- Build test cases
- Measure accuracy

**Tasks:**
1. Create ground truth test cases
2. Implement evaluation metrics:
   - Precision: Are extracted modifications correct?
   - Recall: Did we extract all modifications?
   - F1 Score: Harmonic mean of precision and recall
3. Test on new recipe data (beyond the 5 examples)
4. Document findings

**Key Concepts:**
- What is "good enough" for LLM outputs?
- How to handle ambiguous cases?
- When to prioritize precision vs recall?

---

### Phase 4: Scaling & Production (Week 6)

**Goals:**
- Make the system production-ready
- Handle edge cases
- Add proper error handling

**Tasks:**
1. Add comprehensive logging
2. Implement retry logic for API failures
3. Handle rate limits
4. Add input validation
5. Write documentation
6. Create a demo/video

---

## 📖 Deep Dive Topics

### Understanding This Project's Core Concepts

#### 1. **Why Fuzzy String Matching?**
Recipes have variations like:
- "1 cup butter" vs "1 c. butter"
- "all-purpose flour" vs "AP flour"
- "chocolate chips" vs "semi-sweet chocolate chips"

You need fuzzy matching to apply modifications to the right ingredients.

#### 2. **Why Pydantic?**
LLM outputs are unpredictable. Pydantic ensures:
- Type safety (strings are strings, not numbers)
- Required fields are present
- Data structure is correct
- Easy serialization to JSON

#### 3. **Why Structured Outputs?**
OpenAI's JSON mode ensures valid JSON, but Structured Outputs ensures:
- Schema compliance (exact fields you need)
- No hallucinated fields
- Consistent format every time

#### 4. **Why Evaluation Matters?**
Without evaluation, you don't know:
- If the system actually works
- How often it fails
- What types of inputs break it
- If changes improve or worsen performance

---

## 🎯 Learning Milestones & Checkpoints

### Week 1 Checkpoint:
✅ Can run the project locally  
✅ Understand JSON structure  
✅ Know how to use `uv`  
✅ Can read and modify Python code  

### Week 2 Checkpoint:
✅ Can scrape a website with BeautifulSoup  
✅ Understand HTML parsing  
✅ Can extract structured data from web pages  

### Week 3 Checkpoint:
✅ Can create Pydantic models  
✅ Understand data validation  
✅ Can handle validation errors  

### Week 4 Checkpoint:
✅ Have OpenAI API key and can make calls  
✅ Understand chat completions  
✅ Can use JSON mode  
✅ Can handle API errors  

### Week 5 Checkpoint:
✅ Can write effective prompts  
✅ Understand prompt engineering principles  
✅ Can build multi-step LLM workflows  

### Week 6 Checkpoint:
✅ Can implement fuzzy matching  
✅ Have comprehensive logging  
✅ Have built test cases  
✅ Can measure system performance  

---

## 💡 Tips for Success

### 1. **Learn by Doing**
- Don't just read - code along
- Break things and fix them
- Experiment with the code

### 2. **Read Error Messages**
- Python errors are helpful
- Stack traces tell you exactly where things broke
- Learn to debug systematically

### 3. **Use the Documentation**
- Don't memorize - learn to look things up
- Official docs are your best friend
- Read the "Getting Started" guides

### 4. **Ask Questions**
- Use ChatGPT/Claude for explanations
- Search Stack Overflow
- Read GitHub issues for similar problems

### 5. **Build Small, Test Often**
- Don't write 100 lines without testing
- Test each component independently
- Use print() statements liberally

### 6. **Version Control**
- Commit often with meaningful messages
- Create branches for experiments
- Don't be afraid to revert changes

---

## 🎬 Next Steps

### Immediate Actions (Today):
1. ✅ Install `uv`: `curl -LsSf https://astral.sh/uv/install.sh | sh`
2. ✅ Set up the project: `uv venv && source .venv/bin/activate`
3. ✅ Get OpenAI API key: https://platform.openai.com/api-keys
4. ✅ Run the pipeline: `cd src && uv run python test_pipeline.py single`
5. ✅ Read through this entire learning plan

### Week 1 Actions:
1. Watch Corey Schafer's Python tutorials
2. Complete the JSON tutorial on Real Python
3. Read the uv documentation
4. Set up your development environment properly
5. Study the existing codebase

### Long-term Goal:
By the end of 6 weeks, you should be able to:
- Understand every line of code in this project
- Fix all the identified bugs
- Build an evaluation framework
- Add new features independently
- Explain the system to others

---

## 📚 Bonus Resources

### Books (Optional but Recommended):
1. **"Python Crash Course"** by Eric Matthes - Great for beginners
2. **"Fluent Python"** by Luciano Ramalho - For intermediate learners
3. **"Building LLM Apps"** by Valentina Alto - For AI applications

### Communities:
1. **Reddit** - r/learnpython, r/Python, r/LocalLLaMA
2. **Discord** - Python Discord, OpenAI Developer Community
3. **Stack Overflow** - For specific questions

### Blogs to Follow:
1. **Real Python** - https://realpython.com/
2. **Full Stack Python** - https://www.fullstackpython.com/
3. **Towards Data Science** - https://towardsdatascience.com/

---

## 🏆 Success Metrics

By the end of this learning journey, you will have:

✅ **Technical Skills:**
- Python proficiency (intermediate level)
- API integration expertise
- LLM/AI application development
- Web scraping capabilities
- Data validation and processing

✅ **Project Understanding:**
- Complete understanding of the codebase
- Ability to explain design decisions
- Knowledge of the problem domain
- Understanding of trade-offs made

✅ **Deliverables:**
- Fixed all major bugs
- Built evaluation framework
- Added comprehensive tests
- Created documentation
- Made a demo video

✅ **Career Skills:**
- Working with legacy/autogenerated code
- Debugging complex systems
- Technical communication
- Building production-ready code

---

## 🎓 Final Thoughts

This project touches on many modern AI engineering concepts:
- LLM integration
- Prompt engineering
- Data processing pipelines
- Evaluation frameworks
- Production code quality

Take your time, be systematic, and remember:
**"The only way to learn programming is by doing it."**

Good luck on your learning journey! 🚀

---

## 📋 Sources & References

All resources mentioned in this guide were verified and updated for 2026. For the most current information, always check the official documentation for each tool and library.

**Last Updated:** September 5, 2026
