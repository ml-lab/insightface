# InsightFace
Face Recognition Project

### Experiments

Default image size is 112x96 if not specified, all face images are aligned.

In ResNet setting, \_v1 means original residual units.  \_v2 means pre-activation units.  \_v3 means BCBACB residual units.  LResNet means we use conv33+stride11 in its first convoluition layer instead of common conv77+stride22 to preserve high image resolution.   \_bo means using bottleneck residual units.   

In last several layers, some different options can be tried to determine how embedding layer looks like and it may affect the performance. The whole network architecture can be thought as {ConvLayers(->GlobalPool)->EmbeddingLayer->Softmax}. Embedding size is set to 512 expect for optionA, as embedding size in optionA is determined by the filter size of last convolution group.

- OptionA: Use the final global pooling layer(GP) output as embedding layer directly.
- OptionB: Use one FC layer after GP.
- OptionC: Use FC->BN after GP.
- OptionD: Use FC->BN->PRelu after GP.
- OptionE: Use Dropout->FC->BN after last conv layer.



- **Softmax on LFW**

|   Network/Dataset   |   VGG2@112x112   | WebFace | MS1M |  -   |  -   |
| :-----------------: | :--------------: | :-----: | :--: | :--: | :--: |
|  SE-LResNet50E_v3   | 0.99750+-0.00201 |    -    |  -   |      |      |
|   SE-ResNet50C_v1   | 0.99317+-0.00404 |         |      |      |      |
|   SE-ResNet50B_v1   | 0.99200+-0.00407 |         |      |      |      |
|   SE-ResNet50D_v1   | 0.99383+-0.00259 |         |      |      |      |
|   ResNet50D_v1      | 0.99350+-0.00293 |         |      |      |      |
|  SE-ResNet50A\_v1   | 0.99367+-0.00233 |         |      |      |      |
|  SE-ResNet50E\_v1   | 0.99267+-0.00343 |         |      |      |      |
|  SE-ResNet50F\_v1   | 0.99367+-0.00194 |         |      |      |      |
|  SE-LResNet50C_v1   | 0.99567+-0.00238 |         |      |      |      |
|  SE-LResNet50E_v1   | 0.99650+-0.00174 |    -    |  -   |      |      |
|  SE-LResNet50D_v3   | 0.99617+-0.00358 |    -    |  -   |      |      |
|  Inception-ResNet   |        -         |    -    |  -   |      |      |
| SE-Inception-ResNet |        -         |    -    |  -   |      |      |
|      MobileNet      |        -         |    -    |  -   |      |      |
|       ResNeXt       |        -         |    -    |  -   |      |      |
