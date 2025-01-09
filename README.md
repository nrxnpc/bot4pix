# BOT4PIX Telegram Bot

This repository contains a Telegram bot powered by the **Flux**(or you can use any other you like) model and supports LoRA-based fine-tuning via [PEFT](https://github.com/huggingface/peft). The bot is written in Python and leverages [diffusers](https://github.com/huggingface/diffusers), [transformers](https://github.com/huggingface/transformers), [peft](https://github.com/huggingface/peft), and [python-telegram-bot](https://github.com/python-telegram-bot/python-telegram-bot).

Demo: [bot4pix](http:t.me/stablepixbot)

## Features

- **User Authentication**  
  Activate a code or send an access request to the admin.

- **Image Generation**  
  Uses the Flux model through [diffusers](https://github.com/huggingface/diffusers), with LoRA integration via [PEFT](https://github.com/huggingface/peft).

- **Settings**  
  Aspect ratio presets (1:1, 2:3, 3:2, 9:16, 16:9), output format (photo or file), generation parameters (steps, guidance scale), and LoRA scale.

- **Admin Panel**  
  Grant access codes, remove users, and broadcast messages (text, photo, video, audio).

- **Interactive Interface**  
  Telegram-based with buttons and menus.

---

## Installation

1. **Install & Setup**  
   1. **Clone the Repository**  
      ```bash
      git clone https://github.com/nrxnpc/bot4pix.git
      cd bot4pix
      ```
   2. **Create and Activate a Virtual Environment** (recommended)  
      - **Using Conda**:  
        ```bash
        conda create -n bot4pix python=3.9
        conda activate bot4pix
        ```  
      - **Using venv (pip)**:  
        ```bash
        python -m venv bot4pix
        source bot4pix/bin/activate 
        ```
   3. **Install Dependencies**  
      - **Using pip (in your virtual environment)**:  
        ```bash
        pip install --upgrade pip
        pip install numpy==1.24.4
        pip install torch==2.0.1+cu118 torchvision==0.15.2+cu118 --index-url https://download.pytorch.org/whl/cu118
        pip install transformers diffusers peft python-telegram-bot==13.15
        ```  
        *(Replace `cu118` with your CUDA version if necessary. If no GPU, use `+cpu`.)*  
      - **Using conda (with extra channels)**:  
        ```bash
        conda install -c conda-forge numpy==1.24.4
        conda install pytorch==2.0.1 torchvision==0.15.2 pytorch-cuda=11.8 -c pytorch -c nvidia
        pip install transformers diffusers peft python-telegram-bot==13.15
        ```
   4. **Configure the Telegram Bot Token and Admin ID**  
      - Open `bot.py` (or whichever file contains bot's code).
      - Replace:
        ```python
        TELEGRAM_TOKEN = 'YOUR_TELEGRAM_BOT_TOKEN'  # Replace with your token
        ADMIN_ID = YOUR_ADMIN_ID  # Replace with your ID
        ```
   5. **Specify Model Paths**  
      - `model_path` should point to the Flux model directory.
      - `lora_model_path` should point to LoRA files (e.g., `adapter_model.bin` + `adapter_config.json`).
   6. **Run the Bot**  
      ```bash
      python bot.py
      ```
      The bot will start and listen for incoming Telegram messages.

---

## Usage

- **Authentication**  
  Send `/start`. Choose “Activate code” or “Request access.” If you have a code, enter it; otherwise, the admin is notified.

- **Main Menu**  
  - **Generate**: Generate a new image.  
  - **Repeat**: Repeat the last generation.  
  - **Settings**: Adjust aspect ratio, format, steps, guidance scale, LoRA scale.  
  - **Info**: Quick usage instructions.

- **Admin Panel** (`/admin`)  
  - **Grant Access**: Generate an activation code.  
  - **Remove User**: Remove user by ID.  
  - **Send**: Broadcast messages (text, photo, video, audio).  
  - **Cancel**: Exit admin panel.

- **Settings**  
  - **Aspect Ratio**: 1:1, 2:3, 3:2, 9:16, 16:9.  
  - **Image Format**: photo or file.  
  - **Advanced**: guidance scale, steps, LoRA scale.

- **LoRA Scale**  
  - Adjust via Settings → Advanced → LoRA Scale.
  - Controls LoRA fine-tuning strength.
