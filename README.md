# Verilog implementation of a pre-trained 28x28 pixel handwritten single digit recognition neural network   
Hardware implementation of a pre-trained neural network circuit with 3 layers that is able to recognize handwritten single digits based on 28x28 input pixel map.


# __File Descriptions (.sv):__  

tb_neuralnetwork.sv: testbench for neural_network.sv  

neural_network.sv: "main" top-level module  

layer.sv: module that implements the behaviour of a layer in the NN  

neuron.sv: module that implements the behaviour of a neuron in the NN  

register.sv: module for neuron (gets the data at the index specified by the counter)  

multiplier.sv: module for neuron (multiplies the weight and input values together)  

adder.sv: module for neuron (adds the results of multiplier.sv)  

ReLu.sv: adds the bias term when to the output of adder.sv when the counter reaches the end of the weight and data files, and then applies ReLu activation if needed    

counter.sv: counter that starts at 0 and increments by 1 up on every positive clock edge, until the output reaches the value of the parameter #COUNTER_END  

# __File Descriptions (.mem):__  

w1_1-w1_10: weight values for the first layer in the neural network (in 32 bit hexadecimal format)  
w2_1-w2_10: weight values for the second layer in the neural network (in 32 bit hexadecimal format)  
data_in: data values (in 32 bit hexadecimal format)  
b1: bias values for the neurons in the first layer (in 32 bit hexadecimal format)  
b2: bias values for the neurons in the second layer (in 32 bit hexadecimal format)  

# __Hierarchy of Files:__  

Simulation Sources:  

tb_neuralnetwork.sv X 1  

Design Sources:  

neural_network.sv X 1  
- layer.sv X 2  
  - neuron.sv x 10  
    - register.sv X 2   
    - multiplier.sv X 1  
    - adder.sv X 1  
    - ReLu.sv X 1  
  - counter.sv X 1  


# __Block diagram:__  

See BlockDiagram.png.

# __How to use this:__  

Step 1: Resize the canvas in paint to 28x28 pixels and draw any digit in between 0-9. Then invert the color, and then save as a png file.  

![step1](https://user-images.githubusercontent.com/126916558/226153939-a270a304-ffdd-441f-9ab8-3864d5d8588b.PNG)  

![4_marko](https://user-images.githubusercontent.com/126916558/226153957-6ccf1e24-eeb7-4f53-a865-bc0ab9c67455.png)  

Step 2: Convert the image to a .csv file of pixel values in a 1D array, by using the Convert Image to... .ipynb file in the repo.

![image](https://user-images.githubusercontent.com/126916558/226154252-f089e756-2f3c-4040-ad4d-10e4ba2af39d.png)

Step 3: Use the code in File2.ipynb to convert the (Your Number)_prenormalized.csv to (Your Number).csv.

Step 4: Use the code in File1.ipynb to convert the (Your Number)_prenormalized.csv to (Your Number)_fixed.csv and (Your Number)_hex.csv.





