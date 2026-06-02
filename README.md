# Stable-diffusion-image-generator

A Flask web application that generates images from text prompts using Stable Diffusion (v1.4). Type a prompt in the browser, get a 512×512 AI-generated image, and download it — all from a clean, minimal UI.

---

## Features

- **Stable Diffusion v1.4** — powered by `CompVis/stable-diffusion-v1-4` via Hugging Face Diffusers
- **GPU/CPU support** — automatically uses CUDA if available, falls back to CPU
- **Flask web interface** — simple single-page UI to enter prompts and view results
- **Image download** — generated images can be downloaded directly from the browser

---

## Project Structure

```
.
├── app.py                  # Flask app — model loading, image generation, routes
├── index.html              # Frontend UI template (move to templates/ before running)
├── image.jpg               # Sample/placeholder image
├── generated_image.png     # Example output image
└── README.md
```

> **Note:** Before running, move `index.html` into a `templates/` folder — Flask's `render_template()` looks there by default.

---

## Requirements

- Python 3.8+
- PyTorch (with CUDA for GPU acceleration)
- Hugging Face Diffusers & Transformers
- Flask

Install dependencies:

```bash
pip install flask torch diffusers transformers accelerate
```

For GPU support, install the CUDA-compatible version of PyTorch from [pytorch.org](https://pytorch.org/get-started/locally/).

---

## Setup

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/stable-diffusion-image-generator.git
   cd stable-diffusion-image-generator
   ```

2. **Move the template into place**
   ```bash
   mkdir templates
   mv index.html templates/
   ```

3. **Create the static folder** (where generated images are saved)
   ```bash
   mkdir static
   ```

4. **Run the app**
   ```bash
   python app.py
   ```

5. Open your browser at `http://127.0.0.1:5000`

> The first run will download the Stable Diffusion model (~4GB) from Hugging Face automatically.

---

## Usage

1. Enter a descriptive text prompt (e.g. *"a futuristic city at sunset, cinematic lighting"*)
2. Click **Generate Image**
3. Wait for the model to generate (GPU: ~5–15s, CPU: several minutes)
4. View and **Download** the result

---

## Model Details

| Setting | Value |
|---|---|
| Model | `CompVis/stable-diffusion-v1-4` |
| Output size | 512 × 512 px |
| Device | CUDA (GPU) / CPU |
| Precision | `torch.autocast("cuda")` on GPU |
