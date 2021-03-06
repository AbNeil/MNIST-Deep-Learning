# MNIST-Deep-Learning  

# Numpy Only, without Tensorflow, Keras.... 3rd API

Deep Learning codes for MNIST with detailed explanation 

  ---------------------------------------------------------------------------------

  Copyright: (C) Daniel Lu, RasVector Technology.

  Email : dan59314@gmail.com
  
  linkedin : https://www.linkedin.com/in/daniel-lu-238910a4/
  
  Web :     http://www.rasvector.url.tw/
  
  YouTube : http://www.youtube.com/dan59314/playlist
  
  Instructables : https://goo.gl/EwRGYA
  
  
  GooglePlay : https://play.google.com/store/apps/developer?id=%EF%BC%A4aniel+Lu+%E5%91%82%E8%8A%B3%E5%85%83
  
  

  This software may be freely copied, modified, and redistributed
  provided that this copyright notice is preserved on all copies.
  The intellectual property rights of the algorithms used reside
  with the Daniel Lu, RasVector Technology.

  You may not distribute this software, in whole or in part, as
  part of any commercial product without the express consent of
  the author.

  There is no warranty or other guarantee of fitness of this
  software for any purpose. It is provided solely "as is".

  ---------------------------------------------------------------------------------
  版權宣告  (C) Daniel Lu, RasVector Technology.

  Email : dan59314@gmail.com
  
  linkedin : https://www.linkedin.com/in/daniel-lu-238910a4/
  
  Web :     http://www.rasvector.url.tw/
  
  YouTube : http://www.youtube.com/dan59314/playlist
  
  Instructables : https://goo.gl/EwRGYA
  
  
  GooglePlay : https://play.google.com/store/apps/developer?id=%EF%BC%A4aniel+Lu+%E5%91%82%E8%8A%B3%E5%85%83



  使用或修改軟體，請註明引用出處資訊如上。未經過作者明示同意，禁止使用在商業用途。
  
  
---------------------------------------------------------------------------------


## Example :  

  Train_NoConvLyr.py
  
  	Create and train a model for MNIST, then save the mode as a network file.
  
  Train_ConvLyr.py
  
    Same as above, but allow you to add a covolution layer    
  
  Load_And_Train.py
  
  	Load an saved network file(model) and keep training without restart all.
  
  Predict_Digits.py 
  
    Load traing data from MNIST data set, and randomlly predicit numbers insided.
  
  Predict_Digits_RealTime.py
  
    Capture image from camera, recognize digit(s) in realtime.    

[Recognizing One Digit Video](https://goo.gl/X8KAGz)

[![Recognizing One Digit](https://github.com/dan59314/MNIST-Deep-Learning/blob/master/images/Realtime_Predict.JPG)](https://goo.gl/X8KAGz?t=0s "One Digit Recognizing") 
	
[Recognizing Multiple Digits Video](https://youtu.be/FCE8azMDrMs)

[![Recognizing Multiple Digits](https://github.com/dan59314/MNIST-Deep-Learning/blob/master/images/Predict_MultiDigits.JPG)](https://youtu.be/FCE8azMDrMs?t=0s "One Digit Recognizing") 
        
	
	

  Train_Encoder_Decoder.py   
   
     Build Encoder, Decoder
	    
  Test_EnDeCoder.py   
     
     Encode MNIST digits to code, and decode it back to digits      
      
[AutoEncoder Digits Video](https://youtu.be/hXn95IGmmpI)

[![AutoEncoder Digits](https://github.com/dan59314/MNIST-Deep-Learning/blob/master/images/Update_3.png)](https://youtu.be/hXn95IGmmpI?t=0s "MNIST Encoder / Decoder") 
	
	
[AutoEncoder Denoise Video](https://youtu.be/C2Dz2TXs0Rc)

[![AutoEncoder Denoise](https://github.com/dan59314/MNIST-Deep-Learning/blob/master/images/vdoImg_11.png)](https://youtu.be/C2Dz2TXs0Rc?t=0s "MNIST Encoder / Decoder") 

[AutoEncoder Sharpen Video](https://goo.gl/ykXHqz)

[![AutoEncoder Sharpen](https://github.com/dan59314/MNIST-Deep-Learning/blob/master/images/vdoImg_3_0.png)](https://goo.gl/ykXHqz?t=0s "MNIST Sharpen Model") 

[MNIST GAN Video0](https://youtu.be/_j_7gE34HsY)

[MNIST GAN Video1](https://youtu.be/a3VB-xBb_IY)

[![MNIST GAN](https://github.com/dan59314/MNIST-Deep-Learning/blob/master/images/gan_01.jpg)](https://youtu.be/a3VB-xBb_IY?t=0s "MNIST GAN Model") 


------------------------------------------------------------------------------------
## What else you can do?

  1. Train your own hand-writing digits model.
  2. Train with input of other image set, like alphabet, patterns, signs.... etc
  3. Tell me if you feel these codes useful.
  
-----------------------------------------------------------------------------------
      
## Hints :
  
  ### Methods in RvNeuralNetwork class:
  		Set_DropOutMethod()
  		Show_LayersInfo()
  		Train()
  		Evaluate_Accuracy()
  		Predict_Digit()
  		...
          
  ### Ways to create network:    
    
      Create non-convolutionLayer network [ 780, 50, 10] :    
    		net = rn.RvNeuralNetwork([784,50,10])      
      
    	create convolutionLayer network [ 780, cnvLyr, 50, 10] :
    		lyrObjs.append( RvConvolutionLayer(
       	 	inputShape, # eg. [pxlW, pxlH, Channel]
      	  filterShape, # eg. [pxlW, pxlH, Channel, FilterNum], 
     	   	filterStride) )         
        
       	lyrObjs.append( rn.RvNeuralLayer([lyrObjs[-1].Get_NeuronNum), 50))
       
       	lyrObjs.append( rn.RvNeuralLayer( [50, 10])
       
      	net = rn.RvNeuralNetwork(lyrObjs)
      
      	net.Train(....)

  ### Build Encoder, Decoder:
      #### Train_Encoder_Decoder.py   # Build Encoder, Decoder
      
      encoder, decoder = net.Build_Encoder_Decoder(lstTrain, loop, stepNum, learnRate, lmbda, True, digitIdOnly)
	    
      #### Test_EnDeCoder.py   # Encode MNIST digits to code, and decode it back to digits      
      
      decoder = rn.RvNeuralEnDeCoder.Create_Network(fn1)  # Create Decoder
      
      encoder = rn.RvNeuralEnDeCoder.Create_Network(fn2)  # Create Encoder 
      
      code = encoder.Get_OutputValues(input)  # Encode input to code
      
      output = decoder.Get_OutputValues(code)  # Decode code to digit  
      
      
 ### Build Sharpen Model:
      #### Train_SharpenModel.py  # Build Sharpen Model
        
        .... encoder, decoder = endecoder.Build_Encoder_Decoder_AssignOutputY( \
            lstNew, loop, stepNum, learnRate, lmbda, initialWeights, digitIdOnly)
      
      #### Test_SharpenModel.py  # Test Denoise and sharpen 
 
        .....  rf.Test_EnDecoder(sharpenModel, lstTest, sampleNum, imgPath, noiseStrength)
 
 ### Train GAN Model:
      #### Train_GanModel.py  # Load Genererator, Discriminator, Encoder from file or build new ones
      
        ...    
        if LoadAndTrain:    
            generator, discriminator, encoder = Get_Models_FromFile(intialDiscriminator)
        else:
            generator, discriminator, encoder = Get_Models_New(lstTrain,intialDiscriminator)
        ...
	
------------------------------------------------------------------------------------      
## Test result

### Neural Network -> Accuracy

[784, 30, 10] -> 0.95

[784, 60, 10] -> 0.96

[784, 100, 10] -> 0.976

[784, 400, 10] -> 0.9779

3 Hidden Layers 

[784, 50, 50, 50, 10] -> 0.9735

### Convolution Layer -> Accuracy

[784, ConvLyr, 50, 10] -> 0.9801 ... tested 20 epochs

### Encoder / Decoder -> Accuracy

[784, 256, 128, 10, 128, 256, 784 ] -> 0.9312 ... tested 10 epochs

[784, 400, 20, 400, 784] -> 0.9526 ... tested 5 epochs

----------------------------------------------------------------------------------

<img src="https://github.com/dan59314/MNIST-Deep-Learning/blob/master/images/Spyder01.jpg" width="480">

<img src="https://github.com/dan59314/MNIST-Deep-Learning/blob/master/images/Spyder02.jpg" width="480">

<img src="https://github.com/dan59314/MNIST-Deep-Learning/blob/master/images/train03.jpg" width="480">

<img src="https://github.com/dan59314/MNIST-Deep-Learning/blob/master/images/Note01.jpg" width="480">

<img src="https://github.com/dan59314/MNIST-Deep-Learning/blob/master/images/Note02.jpg" width="480">

<img src="https://github.com/dan59314/MNIST-Deep-Learning/blob/master/images/Note03.jpg" width="480">

AutoEncoder
<img src="https://github.com/dan59314/MNIST-Deep-Learning/blob/master/images/Update_3.png" width="480">

<img src="https://github.com/dan59314/MNIST-Deep-Learning/blob/master/images/AutoEncode01.JPG" width="480">

<img src="https://github.com/dan59314/MNIST-Deep-Learning/blob/master/images/CNN01.png" width="480">

------------------------------------------------------------------------------------
## Misc. Projects of 3D, Multimedia, Arduino Iot, CAD/CAM, Free Tools

[GitHub: https://github.com/dan59314](https://github.com/dan59314)

[Email : dan59314@gmail.com](dan59314@gmail.com)

[linkedin : https://www.linkedin.com/in/daniel-lu-238910a4/](https://www.linkedin.com/in/daniel-lu-238910a4/)

[Web : http://www.rasvector.url.tw/](http://www.rasvector.url.tw/)

[YouTube : http://www.youtube.com/dan59314/playlist](http://www.youtube.com/dan59314/playlist)

[Free Tools : http://www.rasvector.url.tw/hot_91270.html](http://www.rasvector.url.tw/hot_91270.html)


[Instructables : https://www.instructables.com/member/Daniel%20Lu/instructables/](https://www.instructables.com/member/Daniel%20Lu/instructables/)
[![Instructables ](https://github.com/dan59314/Pulse-Sensor-Arduino/blob/master/Instructables01.JPG)](https://www.instructables.com/member/Daniel%20Lu/instructables/ "Instructables") 
