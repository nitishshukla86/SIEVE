# SIEVE: Preserving Cross-Image Evidence via Depth-Aware Token Compression

SIEVE is a training-free method that compresses the visual tokens of a multi-image prompt to a fixed
budget. It pools each image before the decoder, then reduces the tokens in attention-scored stages
inside the decoder, giving every image an equal share and merging each removed token into its most
similar survivor from the same image. The number of stages follows the image count,
S(N) = clip(N, 2, 4), and a closed-form schedule makes the depth-averaged token count meet the budget.

[![Paper](https://img.shields.io/badge/Paper-arXiv%202610.00000-b31b1b?logo=arxiv&logoColor=white)](https://arxiv.org/abs/2610.00000)
[![Project page](https://img.shields.io/badge/Project-Page-2a78d6?logo=githubpages&logoColor=white)](https://nitishshukla86.github.io/SIEVE/)

<img src="figures/teaser.png" width="100%">

**Overview of SIEVE.** (a) On a three-image question, LLaVA-OneVision-7B keeps 6.4% of its visual
tokens and still answers correctly. Each image is pooled before the decoder, then reduced in
S(N) = 3 attention-scored stages that keep an equal share per image and merge every removed token
into its most similar survivor; on the right, each cell is tinted by the final token that absorbed
it. (b) At a 12.5% budget SIEVE is best on every multi-image benchmark, relative to the uncompressed
model (dashed ring = 100). (c) One component at a time at 6.25%, mean over five benchmarks.
(d) On COCO, attention to the queried object peaks in the second half of every backbone, so
selection is spread over depth rather than taken once.

| | |
|---|---|
| **Retained visual tokens at each merging stage**, LLaVA-OneVision-7B keeping 6.25% of the visual tokens; darkened cells are no longer represented as separate tokens. | **Accuracy vs. estimated prefill compute** on LLaVA-OneVision at budgets of 1/16, 1/8 and 1/4 (five-benchmark average). SIEVE is the most accurate at every compute level and, at the two larger budgets, exceeds the uncompressed model (dashed line). |
| <img src="figures/qualitative.png" width="100%"> | <img src="figures/flops.png" width="100%"> |

## Code

The code will be released soon.

## Citation

```bibtex
@article{shukla2026sieve,
  title   = {{SIEVE}: Preserving Cross-Image Evidence via Depth-Aware Token Compression},
  author  = {Shukla, Nitish and Jandial, Surgan and Bui, Nhat-Tan and Ross, Arun},
  journal = {arXiv preprint arXiv:2610.00000},
  year    = {2026}
}
```
