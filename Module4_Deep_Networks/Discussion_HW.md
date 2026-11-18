Some of the most innovative uses of deep neural networks (DNNs) are the ones where the model acts as a second set of eyes for experts instead of replacing them. Medical imaging is a strong example. In a large study, Google Health's deep learning systemcut flase positives by 5.7% and false negative by 9.4% compared with radiologists in US breast cancer screening(Mckinney et al., 2020).

I'm currently using DNNs on a group project called SecondLook. Radiologists read mammograms, and some cancer cases gets missed. SecondLook give patients an independent AI check that flags whether a scan may be worth a second look by a radiologist. The model is a convolutional neural network: a MobileNetV2 backbone pretrained on ImageNet (Sandler et al., 2018), then fine-tuned in two phases on grayscale mammograms. We use focal loss and class weighting because postivie cases are rare. A missed cancer costs far more than an extra review, so we set the decision threshold to guarantee a minimum sensitivity instead of maximizing accuracy. We also show patients a confidence tier rather than a raw probability.

My biggest lesson so far is that in high-stake fields, the hardest decisions are often not about the network's architecture. They're sometimes about how its output is calibrated, how it's communicated, and keeping it in its role as support for clinicians, not a replacement for them.

References

- McKinney, S. M., et al. (2020). International evaluation of an AI system for breast cancer screening. Nature, 577, 89–94.
- Sandler, M., et al. (2018). MobileNetV2: Inverted residuals and linear bottlenecks. CVPR.
