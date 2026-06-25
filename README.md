# Image Cryptography using Deep Learning

This project explores an experimental deep learning-based framework for image encryption and decryption, where neural networks learn key-conditioned transformations to securely map plaintext images into encrypted representations and reconstruct them back with the correct key. The work investigates the feasibility of learned cryptographic transformations and evaluates their robustness using reconstruction and security metrics.

## Features

- 🔐 Neural Network-based Encryption
- 🔑 Key-Dependent Security  
- 📊 Comprehensive Metrics (MSE, PSNR, SSIM)
- 🎨 Visual Analysis Tools
- 🚀 Easy to Use CLI
- 📈 Training Visualization

## Installation

```bash
pip install -r requirements.txt
```

## Quick Start

### 1. Run Demo (1 minute)
```bash
python demo.py
```

### 2. Train Model (15-30 minutes on GPU)
```bash
python train.py
```

### 3. Encrypt Your Image
```bash
python inference.py --mode encrypt --image photo.jpg --output encrypted/
```

### 4. Decrypt Image
```bash
python inference.py --mode decrypt \
  --image encrypted/photo_encrypted.png \
  --key encrypted/photo_key.npy \
  --output decrypted/
```

### 5. Full Pipeline with Visualization
```bash
python inference.py --mode both \
  --image photo.jpg \
  --output results/ \
  --visualize \
  --test-wrong-key
```

## Project Structure

```
image_cryptography_dl/
├── model.py              # Neural network architecture
├── train.py              # Training script
├── inference.py          # Encrypt/decrypt interface
├── demo.py              # Quick demonstration
├── requirements.txt      # Dependencies
└── README.md            # This file
```

## How It Works

The system uses two neural networks:

1. **Encryption Network**: Transforms image using a secret key
2. **Decryption Network**: Recovers original image with correct key

Both networks use encoder-decoder architecture with residual blocks and key-conditioned transformations.

**Security Intuition**:

The encryption process is conditioned on a secret key, ensuring that the output cipher image depends strongly on key variations. A small change in the key should result in significantly different encrypted outputs, while decryption with an incorrect key should fail to reconstruct the original image. This behavior is evaluated using PSNR, SSIM, and correlation analysis.

## Expected Results

After training:
- **Reconstruction PSNR**: > 30 dB
- **Encryption Correlation**: < 0.1  
- **Wrong Key PSNR**: < 15 dB

## Limitations

This framework is experimental and does not claim to replace standard cryptographic algorithms such as AES or RSA. The focus is on exploring learned transformations rather than formally proven security guarantees.

## Future Work

* Integration with traditional cryptographic primitives such as AES
* Analysis against adversarial and brute-force attacks
* Extension to video encryption
* Exploration of post-quantum secure learned encryption frameworks

## License

MIT License - See LICENSE file

## Disclaimer

This is an experimental/educational project. 
