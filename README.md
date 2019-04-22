# THOP: PyTorch-OpCounter

## How to install 
* Using GitHub (always latest)
    
    `pip install --upgrade git+https://github.com/Wayfear/pytorch-OpCounter.git`
    
## How to use 
* Suppport multiple input
* Basic usage 
    ```python
    from torchvision.models import resnet50
    from thop import profile
    model = resnet50()
    flops, params = profile(model, input_sizes=[(1, 3, 224,224)])
    ```    

* Define the rule for 3rd party module.
    
    ```python
    class YourModule(nn.Module):
        # your definition
    def count_your_model(model, x, y):
        # your rule here
    flops, params = profile(model, input_sizes=[(1, 3, 224,224)], 
                            custom_ops={YourModule: count_your_model})
    ```
    
