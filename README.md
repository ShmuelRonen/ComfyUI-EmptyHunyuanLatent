# ComfyUI Hunyuan Latent Nodes

Custom nodes for ComfyUI to generate empty latent space compatible with Hunyuan models for both image and video generation.

![nodes](https://github.com/user-attachments/assets/6af9ce1a-86a0-4f22-a33a-8176591243ca)


For video
![video](https://github.com/user-attachments/assets/c98fef05-24f6-4388-b648-5c25cd91caef)

For Images
![image](https://github.com/user-attachments/assets/b7c244f2-0d31-4814-9c41-f950219251d8)


## Features

- Fixed aspect ratio selection from common formats (1:1, 16:9, 9:16, etc.)
- Support for both image and video latent generation
- All dimensions are automatically adjusted to be multiples of 16
- Maintains compatibility with Hunyuan model tensor format

## Available Nodes

### EmptyHunyuanLatentForImage
Creates an empty latent space for image generation with the following parameters:
- **resolution**: Dropdown selection of common aspect ratios and resolutions
- **batch_size**: Number of images to generate in parallel (default: 1)

### EmptyHunyuanLatentForVideo
Creates an empty latent space for video generation with the following parameters:
- **resolution**: Same resolution options as image node
- **frames**: Number of frames to generate (default: 16, range: 1-256)
- **batch_size**: Number of videos to generate in parallel (default: 1)

## Supported Resolutions

The nodes support various standard resolutions with their aspect ratios:
- Portrait formats:
  - 576x1024 (9:16)
  - 704x1408 (1:2)
  - 768x1344 (4:7)
  - And more...
- Square format:
  - 1024x1024 (1:1)
- Landscape formats:
  - 1024x576 (16:9)
  - 1344x704 (16:9)
  - 1408x704 (2:1)
  - And more...

## Installation

1. Create a custom_nodes directory in ComfyUI if it doesn't exist
```bash
cd ComfyUI/custom_nodes
```

2. Clone this repository:
```bash
git clone https://github.com/ShmuelRonen/ComfyUI-Hunyuan-Latent.git
```

3. Restart ComfyUI

The nodes will appear in the node menu under:
- `latent` for EmptyHunyuanLatentForImage
- `latent/video` for EmptyHunyuanLatentForVideo

## Usage

1. Right-click in the ComfyUI workspace
2. Navigate to:
   - `latent → EmptyHunyuanLatentForImage` for image generation
   - `latent/video → EmptyHunyuanLatentForVideo` for video generation
3. Select desired resolution from the dropdown
4. Connect to other nodes in your workflow

## Node Output Format

Both nodes output a latent dictionary with the key "samples" containing a torch tensor with the following dimensions:

- Image: `[batch_size, 4, 1, height//8, width//8]`
- Video: `[batch_size, 4, frames, height//8, width//8]`

## Requirements

- ComfyUI
- PyTorch
- Hunyuan model dependencies

## Latest Hunyuan models from HuggingFace

https://huggingface.co/Comfy-Org/HunyuanVideo_repackaged/tree/main/split_files/text_encoders

### I recomended this hunyuan_video_720_cfgdistill_fp8_e4m3fn model for fast operation:

https://drive.google.com/file/d/1BvGHjR4Mb60ZPx9tqzA1AabAwZc47ctx/view?usp=sharing

## License

MIT

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.
