# coco_caption  
# 可以再python3下使用的caption evaluation  

- 这里是两个文件夹  

- **coco-caption-py3**
- 来源于https://github.com/entalent/coco-caption-py3，可以正常使用。  
- 但是需要注意pycocoevalcap中的eval.py 中的class COCOEvalCap: 与其他普遍使用的有一点小小的差异（是否传入参数tokenizer）  
- 因此可以访问https://github.com/tylin/coco-caption/blob/master/pycocoevalcap/eval.py来替换掉  
 

- coco_caption-yaya-python3
- 是我自己修改的，但是存在一个在使用过程中，一直在消耗内存的问题，因此不建议使用，后续若查找到问题所在，会继续更新  



