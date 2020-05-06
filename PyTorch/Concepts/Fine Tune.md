- Data Augmentation
  - Random Rotation
  - RandomResizedCrop
  - ToTensor
  - Normalize
  
- Learning Rate
  - 
- Learning Rate Annealing/Scheduling
  - Cyclic Learning Rate
  
- The Optimizer

- Unfreezing layers selectively
  - Names of layer
    ```
        for name, child in model.named_children():
            print(name)
        # It will print the names of the model components
        
        for name, child in model.named_children():
            if name in ['layer3', 'layer4']:
               print(name + ' is unfrozen')
               for param in child.parameters():
                   param.requires_grad = True
            else:
                print(name + ' is frozen')
                for param in child.parameters():
                    param.requires_grad = False
                    
        optimizer = torch.optim.SGD(filter(lambda p: p.requires_grad, model.parameters()), lr=0.0006, momentum=0.9)
    ```
- Weight Decay
  ```
  # similarly for SGD as well
  torch.optim.Adam(model.parameters(), lr=1e-4, weight_decay=1e-5)
  ```

### References
- https://medium.com/udacity-pytorch-challengers/ideas-on-how-to-fine-tune-a-pre-trained-model-in-pytorch-184c47185a20
- https://www.deeplearningwizard.com/deep_learning/boosting_models_pytorch/lr_scheduling/
