# Detecting objects with pre-trained model (YOLO)

### There is some notes :
used test image in images folder<br/> 
1 ) input image (608, 608, 3)<br/> 
2 ) The input image goes through a CNN, resulting in a (19,19,5,85) dimensional output<br/> 
3) after flattening the last two dimensions, the output is a volume of shape (19, 19, 425) :<br/><ul>
      each cell in a 19x19 grid over the input image gives 425 numbers <br/> 
      425 = 5 x 85 because each cell contains predictions for 5 boxes, corresponding to 5 anchor boxes<br/> 
      85 = 5 + 80 where 5 is because  (pc,bx,by,bh,bw) has 5 numbers, and 80 is the number of classes to detect<br/> 
			</ul>
4 ) select only few boxes based on:<br/> <ul>
      score thresholding : throw away boxes that have detected a class with a score less than the threshold<br/> 
      non-max suppression : compute the IOU and avoid selecting overlapping boxes<br/> </ul>
