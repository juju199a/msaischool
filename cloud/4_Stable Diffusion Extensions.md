1. Canny
    - Hugging Face
    - search "ControlNet-v1-1"
    - Files and versions > control_v11p_sd15_canny.pth
    - Copy download link
    - cd stable~/extensions/sd-webui-controlnet/models
    - wget https://huggingface.co/lllyasviel/ControlNet-v1-1/resolve/main/control_v11p_sd15_canny.pth
    - accelerate ~
    - ControlNet Unit
    - (tick) Enable / (tick) Allow Preview
    - Control Type: Canny
    - Preprocessor: canny
    - 총알
    - Model: control_v11p_sd15_canny
    - Control Mode: Balanced
    - P: (An extremely delicate and beautiful work), (masterpiece), (best quality), 
        (beautiful), (one girl), (white T shirt), (mini skirts)
        delicate face, delicate figure, (realistic, photo-realistic), 4k

2. Lineart
    - wget https://huggingface.co/lllyasviel/ControlNet-v1-1/resolve/main/control_v11p_sd15_lineart.pth
    - 이미지 넣기
    - Lineart > linear_standard > 총알 > control_v11p_sd15_lineart
    - Generate

3. Depth
    - wget https://huggingface.co/lllyasviel/ControlNet-v1-1/resolve/main/control_v11f1p_sd15_depth.pth
    - 집 이미지 넣기
    - Depth > depth_midas > 총알 > control_v11f1p_sd15_depth
    - Generate

4. Reference
    - txt2img > Generate image
    - (액자) 클릭
    - img2img > Reference > reference_only
    - Generate

5. Scribble
    - wget https://huggingface.co/lllyasviel/ControlNet-v1-1/resolve/main/control_v11p_sd15_scribble.pth
    - 낙서 이미지 넣기
    - Scribble > scribble_pidinet > 총알 > control_v11p_sd15_scribble

6. Shakker
    - https://www.shakker.ai/
    - AI 생성기
    - Search "flux.1" > Select > 즐겨찾기 > 모델 실행
    - Imange Number: 1 > standing pose > Generate
    - Upscale > Keep > Exit
    - Inpaint > red hair > Keep > Exit
    - Remove BG > Keep > Exit
    - Face Swapper > Upload Image > Swwap Face

7. Openpose
    - wget https://huggingface.co/lllyasviel/ControlNet-v1-1/resolve/main/control_v11p_sd15_openpose.pth

8. OpenPose Editor
    - Extensions > Available > Load from > 3D Ppenpose Edtor tab > Install > Apply and quit
    - 포즈 이미지 넣기
    - OpenPose > openpose_full > 총알 > control_v11p_sd15_openpose
    - 3D Openpose > Setting > Show Preivew
    - File > Detect From Image 
    - Preview 재생 > Save pose.png
    - txt2img
    - pose.png 이미지 넣기 
    - OpenPose > Preprocessor: none > control_v11p_sd15_openpose

9. PoseMy
    - https://posemy.art/app/
    - Export > Export OpenPose without hands
    - Premade Scenes

10. ADetailer
    - Extensions > Install from URL   
    - https://github.com/Bing-su/adetailer.git
    - Install > Installed > Apply and quit
    - accelerate ~
    - txt2img > ADetailer
    - 1st > Enable this tab > face_yolov8n.pt > (Brad Pitt:1)
    - 2nd > Enable this tab > hand_yolov8n.pt > bad hands, missing fingers, fused fingers

11. Viggle (motion shorts)
    - https://viggle.ai/home
    - Try on Web
    - Templete > Select > Confirm
    - Upload Image
    - Background: Green
    - Create

12. Runway
    - https://runwayml.com/
    - Try Gen-2 in Runway
    - Generative Video
    - Drag an image
    - Motion Brush > Brush 1 > Select area > Horizontal and Vertical
    - Generate 4s

13. CapCut
    - https://www.capcut.com/ko-kr/?start_tab=video
    - 새 동영상 > 업로드 (2 files) > 미디어 드래그
    - 배경 > 복제 > 드래그
    - 캐릭터 > 스마트 도구 > 자동삭제
    - 내보내기 > 다운로드 > 내보내기

