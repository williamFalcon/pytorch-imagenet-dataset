# Imagenet dataset for Pytorch.   

### Prereqs.   

1. Download the imagenet data at this [URL](http://image-net.org/download-images).
 - (The imageNet Fall 2011 release link).    

2. This download will take 3-5 days.   
3. Unzip.    


### Format the validation set.    

We want both the train and val to be in this format:   
```    
train/
  n01443537/
    images/
      n02058221_0.JPEG
  ...
```   

To format val dataset:   
```    
python build_folder_tree.py -split_path /path/to/imagenet-folder/val     
```   


## Dataloader    

Train    
```python   

train_path = '/path/to/imagenet-folder/train'
transform = transforms.Compose(
    [transforms.ToTensor()]
)
imagenet_data = torchvision.datasets.ImageFolder(train_path, transform=transform)
data_loader = torch.utils.data.DataLoader(
    imagenet_data,
    batch_size=64,
    shuffle=True,
    num_workers=0
)
return data_loader
```
