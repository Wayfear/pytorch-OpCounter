# THOP: PyTorch-OpCounter

## Source
* Folk from: [THOP: PyTorch-OpCounter](https://github.com/Lyken17/pytorch-OpCounter)
* Fix some bug and support multiple input

## How to install 
* Using GitHub (always latest)
    
    `pip install --upgrade git+http://gitlab.bj.sensetime.com/kanxuan/THOP_PyTorchOpCounter.git`
    
## How to use 

* Core API

    ```
    def profile(model: nn.Module, input_sizes: List[Tuple[int]],
                custom_ops: Dict[nn.Module, Callable]={}, device: str="cuda")-> Tuple[int, int]:
        ...
        return flops, params
    ```

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
    
