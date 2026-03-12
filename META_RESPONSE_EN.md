Dear Senior Area Chairs and Area Chair,

Thank you for the constructive meta-review and for recognizing the practical value of MM-ShiftKV. We fully agree that stronger theoretical support is needed, and we will integrate the following revisions in the camera-ready version.

1. **Gaussian modeling and heavy-tailed outliers** *(AC-1; KhwL-W1)*  
We will narrow the claim scope and clarify that Gaussian modeling is used only for the **pre-projection, statistically stable representation space**. We will add quantitative goodness-of-fit evidence (e.g., skewness/kurtosis and distribution-fit statistics) to support this approximation, and explicitly discuss tail deviations. We will further show how Variance Expansion improves coverage of projection-amplified tail dimensions, increasing Top-0.1% outlier hit rate from **12.4% to 89.7%** and reducing KL divergence by **88.3%**.

2. **Fixed hyperparameters across layers/architectures** *(AC-2; yHZB-W2, ogWP-W2, KhwL-W3)*  
We will clarify that unified \(\gamma=10\) is chosen for robustness across models/layers rather than per-case fitting. We will add cross-architecture profiling showing prefill-to-decode variance expansion consistently exceeds 10x (LLaVA/MHA: **13.2x**; Qwen/GQA: **22.8x**) and include ablations showing global \(\gamma\) avoids diversity collapse and outperforms layer-wise tuning (**0.688 vs. 0.662** on OCRBench).

3. **Limitations of prefill-stage proxies** *(AC-3; KhwL-W2)*  
We will add a dedicated limitations paragraph stating that uncalibrated prefill-only proxies can fail under large prompt-length shifts. We mitigate this with **Dynamic Base + Static Expansion** via per-batch \(\mu,\sigma\) updates. Across prompt lengths from **642 to 4,830** tokens, this substantially reduces distribution shift while preserving overall distribution shape.

Detailed experimental settings and full analyses are available in our rebuttal responses mapped above. We believe these revisions directly address the AC’s three requests and strengthen both the theoretical and empirical foundations of the paper.
