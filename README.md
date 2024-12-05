# Content-Aware-ViT-Optimization
This project explores the integration of seam carving, a content-aware image resizing technique, into the preprocessing pipeline of Vision Transformers (ViTs). Our objective is to optimize the resizing process, reducing computational overhead while preserving critical features, and improving classification accuracy on fine-grained datasets such as the Stanford Cars Dataset.

# Motivation
Vision Transformers rely on fixed-size input images (224x224), often resized using uniform methods like bilinear interpolation. While effective, these methods may lose important features, especially in images with rich textures or high detail. Seam carving adaptively resizes images by removing low-energy seams, preserving key content. We further optimize the seam carving algorithm by updating energy maps locally around seams, significantly reducing computation time. However, we observed its effectiveness varied depending on the type of image. This approach fails to bubble up or bubble left (depending on your definition of the energy map) the energy of the pixels, which is crucial in finding the first minimum energy pixel using which an optimal seam is calculated.

# ViT Training Configuration
- **Dataset**: Stanford Cars Dataset
- **Model Input Size**: 224x224
- **Learning Rate**: 0.0002
- **Number of Epochs**: 20
- **Train-Test Split**: 80% training, 20% testing
- **Evaluation Metric**: Accuracy

# Results
- The optimized seam carving approach significantly reduced processing time (from ~136s to ~8s for resizing).
- The method performed well for images with dispersed energy (e.g., multiple objects or textures) but struggled with concentrated energy regions.

### How to Run
1. Clone the repository:
   ```bash
   git clone https://github.com/JaivalBhup/Content-Aware-ViT-Optimization.git
   cd Content-Aware-ViT-Optimization
   pip install -r requirements.txt
   python -m notebook
   ```
# Contributors

- Samprith Kalakata (srk9068@nyu.edu) 
- Jaival Bhuptani (jnb9582@nyu.edu) 

# References
- Jubair, Mohammad Imrul. "Seam Carving as Feature Pooling in CNN." arXiv preprint arXiv:2409.06311 (2024).
- Shai Avidan and Ariel Shamir. 2007. Seam carving for content-aware image resizing. In ACM SIGGRAPH 2007 papers (SIGGRAPH '07). Association for Computing Machinery, New York, NY, USA, 10–es. https://doi.org/10.1145/1275808.1276390
- Farhana Sultana, A. Sufian, Paramartha Dutta. “Advancements in Image Classification using Convolutional Neural Network.” arXiv, 8 May 2019, https://arxiv.org/abs/1905.03288. Accessed 4 December 2024.
- Hongling Zheng, Li Shen, Anke Tang, Yong Luo, Han Hu, Bo Du, Dacheng Tao “Learn From Model Beyond Fine-Tuning: A Survey.” arXiv, 12 October 2023, https://arxiv.org/abs/2310.08184. Accessed 4 December 2024.
- Venkatesh Balavadhani Parthasarathy,, et al. “The Ultimate Guide to Fine-Tuning LLMs from Basics to Breakthroughs: An Exhaustive Review of Technologies, Research, Best Practices, Applied Research Challenges and Opportunities.” arxiv.org,October 2024, https://arxiv.org/pdf/2408.13296.
- Behnam Neyshabur, et al. “What is being transferred in transfer learning?” https://arxiv.org, 14 Jan 2021, https://arxiv.org/pdf/2008.11687.
- Shengjia Zhao, et al. “Learning Hierarchical Features from Generative Models.” https://arxiv.org, 9 Jun 2017, https://arxiv.org/pdf/1702.08396.
- Jason Yosinski, et al. “How transferable are features in deep neural networks?” arxiv.org, 6 Nov 2014, https://arxiv.org/pdf/1411.1792.
