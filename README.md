# 🖼️ Image Search
Congratulations! You’ve completed the simulator course. Now it’s time to test your knowledge with a new task — independently.
Once finished, submit your work for review. You’ll receive feedback within 24 hours. You may need to revise and resubmit the project several times — that’s perfectly normal. The project is complete once the reviewer approves all revisions.

## 📘 Project Description
You work at a photo hosting service for professional photographers called “With Sense”. Users upload their photos along with detailed descriptions — location, camera model, etc. A unique feature of the service: descriptions can be added by other users, not just the uploader.
For example, this photo:

*A hiker poses for a picture in front of stunning mountains and clouds.*

The goal of your department’s experiment is to develop a reference image search for photographers. Users enter a scene description, like:

*A man is crossing a mountain pass on a metal bridge.*

The service then returns several matching or similar photos.
To justify the experiment, you need to present a Proof of Concept (PoC) — a working demo that shows the project is feasible.
Your task: build a demo version of a text-to-image search engine.

## 🧠 Model Requirements
Choose the best model that can:
- Generate vector representations for both images and text
- Output a score from 0 to 1 indicating how well the text matches the image

This model will be the foundation for the prototype shown to company leadership.

## ⚖️ Legal Restrictions
In some countries where “With Sense” operates, it’s illegal to process or display content involving children under 16 without parental consent. This includes text, images, video, and audio.
Your PoC must not include such content. If a query leads to restricted content, your system must display a disclaimer:

*This image is unavailable in your country in compliance with local laws.*

Since your PoC can’t implement this functionality directly, you must filter out problematic content during training. During testing, if a query contains restricted terms, your function must return the disclaimer.

## 📂 Dataset Description
- train_dataset.csv: contains image filenames, description IDs, and text descriptions

  - Each image may have up to 5 descriptions

  - Description ID format: <image_filename>#<description_number>

- train_images/: folder with training images

- CrowdAnnotations.tsv: crowd-sourced relevance scores

  - Columns: image filename, description ID, % agreement, # agree, # disagree

- ExpertAnnotations.tsv: expert relevance scores

  - Columns: image filename, description ID, scores from 3 experts (1–4 scale)

    - 1: completely irrelevant

    - 2: partially relevant

    - 3: mostly relevant

    - 4: fully relevant

- test_queries.csv: test queries with description ID, text, and relevant image

- test_images/: folder with test images

## 🛠️ Project Instructions
### Step 1: Load and Explore the Data
- Download and inspect all files
- Clean and correct the data if needed

### Step 2: Prepare Data for Training
- Create a list of restricted keywords based on legal guidelines
- Remove training pairs that contain these keywords
- Vectorize text using one of:
  - TF-IDF
  - BERT
  - Word2Vec

- Vectorize images using ResNet50 from Keras or PyTorch

- Describe the resulting vector pairs (dimensions, structure)

### Step 3: Train the Model
- Build a model that takes a concatenated vector (image + text) and predicts expert score
- Choose a metric to evaluate model accuracy
- Train multiple models and tune hyperparameters:
  - Linear regression
  - Fully connected neural networks

### Step 4: Test and Demonstrate
- Test the best model on the test set
- Write a function that:
  - Takes a text query
  - Vectorizes it
  - Returns the image with the highest relevance score
  - Displays a disclaimer if the query contains restricted content

- Test the function with various queries and observe results

### Step 5: Final Analysis
- Describe the best-performing model
- Discuss common errors in matching text to image
- Evaluate the practical feasibility of the image search service

## 📝 Formatting Guidelines
- Use Jupyter Notebook
- Code in code cells, explanations in markdown cells
- Apply formatting and headings
Due to resource limits in Yandex.Practicum’s JupyterHub, use Kaggle, Google Colab, DeepNote, Yandex Data Sphere, or local setup.

## ✅ Evaluation Criteria
Reviewers will assess:

- Whether all steps are followed
- Data preparation quality
- Text and image vectorization methods
- Model types and hyperparameters
- Code duplication
- Quality of conclusions
- Project structure and code cleanliness

Everything you need is in the course notes and cheat sheets.

Good luck! 🚀
