# Super Selfish
A framework for self supervised learning on images.

Currently supports:
### Patch-based
- ExemplarNet https://arxiv.org/abs/1406.6909
- RotateNet https://arxiv.org/abs/1803.07728 
  (No Context Free Network for performance reasons)
- Jigsaw Puzzle https://arxiv.org/abs/1603.09246
### Predictive
- Denoising Autoencoder https://www.cs.toronto.edu/~larocheh/publications/icml-2008-denoising-autoencoders.pdf
- Context Autencoder https://arxiv.org/pdf/1604.07379.pdf 
- SplitBrain Autoencoder https://arxiv.org/pdf/1611.09842.pdf
### Generative
- BiGAN https://arxiv.org/pdf/1605.09782.pdf
### Contrastive
- Instance Discrimination https://arxiv.org/pdf/1805.01978.pdf (Memory Bank, Augmentation Task)
- Contrastive Predictive Coding (V2) https://arxiv.org/pdf/1905.09272.pdf (Batchwise, Future Prediction Task)
- Momentum Contrast (V2) https://arxiv.org/pdf/1911.05722.pdf https://arxiv.org/abs/2002.05709 (Qeue, Augmentation Task)
- BYOL (CL via BN) https://arxiv.org/pdf/2006.07733.pdf (No negatives, Augmentation task)

Training is as easy as:
```python

supervisor = RotateNetSupervisor(train_dataset).to(device)
#supervisor = RotateNetSupervisor(train_dataset).to(device)
#supervisor = ExemplarNetSupervisor(train_dataset).to(device)
#supervisor = JigsawNetSupervisor(train_dataset).to(device)
#supervisor = DenoiseNetSupervisor(train_dataset).to(device)
#supervisor = ContextNetSupervisor(train_dataset).to(device)
#supervisor = BiGanSupervisor(train_dataset).to(device)
#supervisor = SplitBrainNetSupervisor(train_dataset).to(device)
#supervisor = ContrastivePredictiveCodingSupervisor(train_dataset).to(device)
#supervisor = MomentumContrastSupervisor(train_dataset).to(device)
#supervisor = BYOLSupervisor(train_dataset).to(device)
# ...
# Start training
supervisor.supervise(lr=lr, epochs=epochs,
                     batch_size=batch_size, name="store/base_" + supervisor_name, pretrained=False)

```



# TODOs
- DataParallel
- Docs
- Visual testing
- CPC data augmentation
- Layer and instance norm (Shuffled batch norm for MoCo)
- Learning rate schedule
- Blur
- solarization