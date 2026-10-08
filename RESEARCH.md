# AntiNude research roadmap

## Current state

The GitHub Pages site implements experimental metadata instructions, redundant LSB data, random stratified pixel perturbations, optional visible warning blocks, and a detached signed manifest. **None are proven to prevent unauthorized sexualized editing.** The signature supports file-integrity verification only when checked against a trusted reference key.

## Implemented evaluation lab

Open [lab.html](lab.html). Upload the protected input and AI-edited output to compute mean absolute RGB difference, mean squared error, PSNR, a thresholded changed-pixel percentage, and a difference heatmap. The tool operates locally and exports JSON. Pixel metrics are sensitive to alignment, crops, and regeneration, and cannot establish resistance to harmful edits.

## Next technical milestone: model-aware defense

1. Reproduce [PhotoGuard](https://github.com/MadryLab/photoguard) and [DiffusionGuard](https://github.com/choi403/DiffusionGuard) on a compatible, locally available open-weight diffusion editor. Review upstream licensing and model weights before integration.
2. Build an offline Python/PyTorch worker for perturbation optimization; never present random-noise output as an optimized defense.
3. Benchmark benign editing success, prohibited editing success using controlled authorized synthetic test data, visual quality, and robustness to JPEG, scaling, cropping, and denoising.
4. Compare multiple random seeds, prompts, models, and editing settings. Document failure cases, model transfer, and compute costs.
5. Investigate selective defenses inspired by TarPro, plus frequency-domain and amortized defenses (DCT-Shield, DiffVax).

A static GitHub Pages deployment cannot itself run the GPU-based optimization. Any future hosted inference must have explicit privacy and data-retention disclosures. Do not upload sensitive personal images to untrusted services.
