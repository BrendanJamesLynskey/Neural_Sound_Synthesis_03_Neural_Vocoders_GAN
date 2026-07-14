# Neural Sound Synthesis · Part 3 — Neural Vocoders (GAN)

The third part of the [Neural Sound Synthesis](https://github.com/BrendanJamesLynskey/Neural_Sound_Synthesis) series. How a magnitude-only mel spectrogram is inverted back into a waveform: the classical Griffin–Lim iteration and why it falls short, and the adversarial vocoders that replaced it — MelGAN, Parallel WaveGAN, and HiFi-GAN — with their generators, discriminators, and losses built up from first principles.

### [Launch App](https://brendanjameslynskey.github.io/Neural_Sound_Synthesis_03_Neural_Vocoders_GAN/)

Part of the [DSP & Music](https://github.com/BrendanJamesLynskey/DSP_and_Music) collection.

---

## What's inside

| Section | Content |
|---------|---------|
| **The Vocoder Problem** | Inverting a mel spectrogram, why magnitude-only discards ~half the frame's information, and the phase-consistency constraint that makes it hard |
| **Griffin–Lim** | Alternating-projection phase recovery, spectral inconsistency, its three limits — with a **live Griffin–Lim A/B listener** on a real in-browser STFT |
| **Why GANs** | Feed-forward inversion, why MSE punishes correct-sounding audio, and what the discriminator's perceptual loss buys |
| **MelGAN & Parallel WaveGAN** | Feature-matching loss, window/multi-scale discriminators, and the multi-resolution STFT loss |
| **HiFi-GAN Generator** | Transposed-conv upsampling (×8·8·2·2 = 256) and multi-receptive-field fusion — with an **interactive generator + MRF schematic** |
| **MPD + MSD** | The Multi-Period Discriminator's prime-period reshape and the Multi-Scale Discriminator — with a **live MPD reshaper** |
| **The Objective** | LSGAN adversarial loss, feature matching, mel reconstruction, and the full weighted objective |
| **Beyond** | UnivNet, BigVGAN, diffusion vocoders, and a 2019→2022 timeline |

## Live demos (all synthesised in-browser, no audio files)

1. **Griffin–Lim vs original** — generates a sung vowel, computes its magnitude STFT, and runs a *real* iterative Griffin–Lim phase reconstruction (1–50 iterations). Play the original and the reconstruction back-to-back; few iterations sound phasey, many clean up, and the spectral-convergence error is shown live.
2. **Multi-Period Discriminator reshaper** — folds a quasi-periodic 1-D signal into a 2-D grid by period *p* ∈ {2,3,5,7,11}; when *p* matches the signal period the columns align into vertical bands, showing why HiFi-GAN uses several prime periods.
3. **HiFi-GAN generator + MRF schematic** — an interactive diagram of the upsampling generator and its multi-receptive-field fusion block; hover any stage for an explanation.

## Technology

Single-file HTML/CSS/JS · Web Audio API · HTML5 Canvas · real framed DFT / STFT / ISTFT · KaTeX · Palatino + Lucida Console · No external dependencies · No build step
