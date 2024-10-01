1. Connect Machine Learning
    - ssh .\5b043sdvm.pem azureuser@1.1.1.1 -p 50000
    - cd stable-diffusion-webui
    - conda activate sdwebui
    - accelerate launch --mixed_precision=bf16 --num_cpu_threads_per_process=4 launch.py --share --enable-insecure-extension-access --xformers --no-half-vae --gradio-auth b043:1111
    - Running on public URL: https://~gradio.live

2. Select checkpint
    - sd_xl_base_1.0.safetensors: 실사화를 많이 시켰다.
    - Generation
    - Width: 1024
    - Height: 1024
    - Sampleing method: Euler a

3. Only Prompt
    - A sorceress
    - Emma Watson as a powerful mysterious sorceress, casting lightning magic, detailed clothing
    - Emma Watson as a powerful mysterious sorceress, casting lightning magic, detailed clothing, digital painting
        - digital painting: 색감과 표현이 매끈함
    - Emma Watson as a powerful mysterious sorceress, casting lightning magic, detailed clothing, digital painting, hyperrealistic, fantasy, Surrealist, full body
        - hyperrealistic, fantasy, Surrealist, full body : 초현실주의
    - Emma Watson as a powerful mysterious sorceress, casting lightning magic, detailed clothing, digital painting, hyperrealistic, fantasy, Surrealist, full body, by Stanley Artgerm Lau and Alphonse Mucha
        - by Stanley Artgerm Lau and Alphonse Mucha: 작가스타일
    - Emma Watson as a powerful mysterious sorceress, casting lightning magic, detailed clothing, digital painting, hyperrealistic, fantasy, Surrealist, full body, by Stanley Artgerm Lau and Alphonse Mucha, artstation
        - artstation: 일러스터 단체
    - Emma Watson as a powerful mysterious sorceress, casting lightning magic, detailed clothing, digital painting, hyperrealistic, fantasy, Surrealist, full body, by Stanley Artgerm Lau and Alphonse Mucha, artstation, highly detailed, sharp focus, sci-fi, stunningly beautiful, dystopian, iridescent gold
        - highly detailed, sharp focus, sci-fi, stunningly beautiful, dystopian, iridescent gold : 멋진 사진 + 옷

4. Prompt + Negative Prompt (NG)
    - portrait photo of a man without mustache

5. Prompt + Negative Prompt (OK)
    - Prompt: portrait photo of a man
    - Negative Prompt: mustache

6. Refiner
    - P: girl alone. photo, solo, incredibly absurd, hoodie, headphones, street, outdoor, rain
    - N: disfigured, ugly, bad, immature, carton, anime, painting, b&w
    - (액자) Send image and generation parameters to img2img tab
    - Just resize
    - Sample method: Euler a
    - Refiner > Checkpoint: sd_xl_refiner_1.0.safetensors
    - Width: 1024
    - Height: 1024
    - Denosing strength: 0.3 (0.2~0.3 정도가 좋다)

7. Sketch
    - img2img > Generation > Sketch
    - 스케치용빈화면 이미지를 끌어 놓는다.
    - Sketch

8. Outpainting (늘려준다)
    - (액자) Send image and generation parameters to img2img tab
    - Crop and resize
    - Script: Poor man's Outpainting
    - fill
    - left, right, up, down

7. Upscaling (해상도 복원)
    - Extras
    - Upscale 
    - Upscaler 1: R-ESRGAN 4x+

8. Inpainting
    - (팔레트) Send image and generation parameters to img2img inpaint tab
    - img2img > Generation > Inpaint
    - Just resize
    - Masked content: fill
    - Inpaint area: Only masked

9. Install Rembg
    - Extensions > Available > Load from
    - find "rembg" > stable-diffusion-webui-rembg
    - Install
    - Installed > stable=diffusion-webui-rembg 확인 > Apply and quit
    - Restart sdwebui

10. Rembg
    - (삼각자) Send image and generation parameters to extras tab
    - Remove background: u2net

11. CIVITAI (LoRA)
    - civitai.com > Profile > Acount Settings > API Keys > Add API Key > 이름 적기 > Key 복사 > 메모장
    - Filters > Year, LoRA, SDXL1.0
    - cd models/Lora/ 
    - civitdl 48473 . -k <API_Key>
    - cd ../..
    - accelerate ~
    - txt2img > Lora > Select 
    - P: <lora:MG_ip:1> girl alone. photo, solo, incredibly absurd, hoodie, headphones, street, outdoor, rain
    - N: disfigured, ugly, bad, immature, carton, anime, painting, b&w

12. HuggingFace (.safetensors Download)
    - LoRA 중에 safetensor가 아닌, diffuser 방식으로 배포되는 경우가 많다. 그런데, diffuser 방식은 WebUI 적용하는 절차가 복잡합니다.
    - Search "sdxl-wrong-lora" > Community
    - https://huggingface.co/~
    - Coy download link
    - wget https://huggingface.co/~
    - accelerate ~
    - txt2img > Lora

13. Install ControlNet
    - Extensions > Install from URL > https://github.com/Mikubill/sd-webui-controlnet
    - Installed > 확인 > Apply and quit
    - Search in HuggingFace > sd_control_collection
    - t2i-*canny*.safetensors > Copy download link
    - t2i-*openpose*.safetensors > Copy download link
    - cd /stable~/extensions/sd-webui-controlnet/models
    - wget https://~/t2i-*canny*.safetensors
    - wget https://~/t2i-*openpose*.safetensors
    - accelerate ~

14. Use ContrlNet
    - P: Emma Watson as a powerful mysterious sorceress, casting lightning magic, detailed clothing, digital painting, hyperrealistic, fantasy, Surrealist, full body, by Stanley Artgerm Lau and Alphonse Mucha, artstation, highly detailed, sharp focus, sci-fi, stunningly beautiful, dystopian, iridescent gold
    - Sampling method: Euler A
    - Width: 1024
    - Height: 1024
    - Seed: 3927690186
    - ControlNet Unit 0
    - 컨트롤넷 실습 사진.jpg (사람 움직임 넣기)
    - (tick) Enable / (tick) Low VRAM / (tick) Pixel Perfect / (tick) Allow Preview
    - Preprocessor (전처리기): openpose_full
    - 총알 (Run Preprocessor)
    - Model: t2i-adapter_diffusers_xl_openpose
    - Generate

15. Openpose 2 (보충)
    - https://app.posemy.art
    - Export > Export OpenPose with hands
    - ControlNet Unit에 이미지 넣기
    - (untick) Enable / (untick) Low VRAM / (untick) Pixel Perfect / (untick) Allow Preview
    - Contorl Type: OpenPose
    - Preprocessor (전처리기): openpose_full
    - Model: t2i-adapter_diffusers_xl_openpose

16. Canny (보충)
    - 사진 Drag & Drop
    - (tick) Enable / (tick) Low VRAM / (tick) Pixel Perfect / (tick) Allow Preview
    - Contorl Type: Canny
    - 총알 (Run Preprocessor)
    - Model: t2i-adapter_diffusers_xl_canny

17. Install Regional Prompter
    - Extensions > Available > Load from
    - find "Regional Prompter" > Install
    - Installed > 확인 > Apply and quit
    - accelerate ~

18. Regional Prompter (Rows)
    - Generation
    - Regional Prompter
    - Active
    - Attention
    - Main Splitting: Rows: 1,2,3,1
    - P: blue baseball cap, old man, blonde hair, blue eyes BREAK 
        pink shirt_lemon printed BREAK
        green jeans BREAK
        white sneakers

19. Regional Prompter (Columns)    
    - Attention
    - (tick) Use common prompt
    - Main Splitting: Columns
    - Divide Ratio: 1,1,1;1,1,2
    - Width: 1024 / Height: 1024
    - P: a witch, highly detailed face, half body, photo, with a bird, studio lighting, dramatic lighting BREAK
        highly detailed clothing, looking at you, mysterious, dramatic lighting BREAK
        (full moon:1.3) ADDCOL
        (beautiful fire magic: 1.2) ADDROW
        a blue bird ADDCOL
        a white dog
    -N: underage, immature, disfigured, deformed











