1. Create Azure Machine Learning
    - 이름: 5b0430-ml5
    - 지역: Korea Central

2. Create Compute Instance
    - Start Machine Learning Studio
    - 컴퓨팅 이름: b043-sd-vm5 (영문으로 시작해야 함)
    - 가상 머신 유형: GPU
    - VM 크기: Standard_NC4as_T4_v3
    - SSH: SSH 액세스 사용
    - SSH 공개 키 원본: Generate new key pair
    - 키 쌍 이름: 5b043sdvm5
    - 프라이빗 키 다운로드 및 컴퓨팅 만들기
    - (오래 걸림)

3. Connect VM & 
    - ssh -i 5b043sdvm5.pem azureuser@1.1.1.1 -p 50000
    - conda --version
    
4. Download Stable Diffusion & Models
    - git clone https://github.com/AUTOMATIC1111/stable-diffusion-webui.git

5. Download Hugging Face Models
    - cd stable-diffusion-webui
    - cd models
    - Profile > Settings > Access Tokens > Read > sdvm > 키 값 저장
    - curl -H "Authorization: Bearer <Token Key>" https://huggingface.co/runwayml/stable-diffusion-v1-5/resolve/main/v1-5-pruned-emaonly.ckpt --location --output v1-5-pruned-emaonly.ckpt
    - curl -H "Authorization: Bearer <Token Key>" https://huggingface.co/stabilityai/stable-diffusion-xl-base-1.0/resolve/main/sd_xl_base_1.0.safetensors --location --output sd_xl_base_1.0.safetensors
    - curl -H "Authorization: Bearer <Token Key>" https://huggingface.co/stabilityai/stable-diffusion-xl-refiner-1.0/resolve/main/sd_xl_refiner_1.0.safetensors --location --output sd_xl_refiner_1.0.safetensors

6. Create an environment
    - cd /home/azureuser/stable-diffusion-webui
    - conda create --name sdwebui python=3.10 -y
    - conda activate sdwebui
    - conda env list
    
7. Install Stable Diffusion Library
    - pip install -r requirements_versions.txt
    - conda install pytorch torchvision torchaudio pytorch-cuda=12.4 -c pytorch -c nvidia
    - git config --global --add safe.directory '*'
    - conda install xformers -c xformers/label/dev
    - pip install civitdl
    - conda update --all
    - conda install pytorch torchvision torchaudio pytorch-cuda=12.4 -c pytorch -c nvidia
    - accelerate launch --mixed_precision=bf16 --num_cpu_threads_per_process=4 launch.py --share --enable-insecure-extension-access --xformers --no-half-vae --gradio-auth b043:1111

8. Connect Stable Diffusion 
    - Running on public URL: https://~.gradio.live

9. Download Output
    - zip -r output.zip .
    - scp -i ~pem -p 50000 azureuser@1.1.1.1:/home/azureuser/stable-diffusion-webui/outputs/txt2img-images/2024-06-09/output.zip .















