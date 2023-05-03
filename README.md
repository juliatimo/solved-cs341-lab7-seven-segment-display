Download Link: https://assignmentchef.com/product/solved-cs341-lab7-seven-segment-display
<br>
In this lab, you will learn how to use a 7 segment display. We will write to it to display numbers using a decoder chip that simplifies our code. When done, your display should loop through digits 0-9. The starter code can be found on GitHub under Lab 7.

<strong> </strong>

<h1>Background Information</h1>




Seven Segment Displays are used in many consumer devices like calculators, clocks, watches, counters and microwave ovens. They are made out of LEDs and are low cost devices to display information. They come in a variety of colors and sizes. Some displays have a single digit and others have multiple digits.




Seven segment displays consist of 7 LEDs, called segments, arranged in the shape of an “8” and a dot on the right side of the digit that serves as a decimal point. Each segment is named with a letter A to G, and DP for the decimal point. For example, to display a number 7, the segments A, B and C must be lit up.




To make the matching of digits to segments easier, seven segment display chips come with a 4bit decoder which maps the digits in binary (e.g. 0 – 9 and some special characters) to the correct segments to display that number. Instead of lighting the groups of segments to form a digit, the user programs the 4-bit decoder to light up the digits as follows:




<table width="404">

 <tbody>

  <tr>

   <td colspan="4" width="256"><strong>                    Decoder Input    </strong></td>

   <td width="148"><strong> </strong></td>

  </tr>

  <tr>

   <td width="64"><strong>bit 3 </strong></td>

   <td width="64"><strong>bit 2 </strong></td>

   <td width="64"><strong>bit 1 </strong></td>

   <td width="64"><strong>bit 0 </strong></td>

   <td width="148"><strong>Display character </strong></td>

  </tr>

  <tr>

   <td width="64">LOW</td>

   <td width="64">LOW</td>

   <td width="64">LOW</td>

   <td width="64">LOW</td>

   <td width="148">0</td>

  </tr>

  <tr>

   <td width="64">LOW</td>

   <td width="64">LOW</td>

   <td width="64">LOW</td>

   <td width="64">HIGH</td>

   <td width="148">1</td>

  </tr>

  <tr>

   <td width="64">LOW</td>

   <td width="64">LOW</td>

   <td width="64">HIGH</td>

   <td width="64">LOW</td>

   <td width="148">2</td>

  </tr>

  <tr>

   <td width="64">LOW</td>

   <td width="64">LOW</td>

   <td width="64">HIGH</td>

   <td width="64">HIGH</td>

   <td width="148">3</td>

  </tr>

  <tr>

   <td width="64">LOW</td>

   <td width="64">HIGH</td>

   <td width="64">LOW</td>

   <td width="64">LOW</td>

   <td width="148">4</td>

  </tr>

  <tr>

   <td width="64">LOW</td>

   <td width="64">HIGH</td>

   <td width="64">LOW</td>

   <td width="64">HIGH</td>

   <td width="148">5</td>

  </tr>

  <tr>

   <td width="64">LOW</td>

   <td width="64">HIGH</td>

   <td width="64">HIGH</td>

   <td width="64">LOW</td>

   <td width="148">6</td>

  </tr>

  <tr>

   <td width="64">LOW</td>

   <td width="64">HIGH</td>

   <td width="64">HIGH</td>

   <td width="64">HIGH</td>

   <td width="148">7</td>

  </tr>

  <tr>

   <td width="64">HIGH</td>

   <td width="64">LOW</td>

   <td width="64">LOW</td>

   <td width="64">LOW</td>

   <td width="148">8</td>

  </tr>

  <tr>

   <td width="64">HIGH</td>

   <td width="64">LOW</td>

   <td width="64">LOW</td>

   <td width="64">HIGH</td>

   <td width="148">9</td>

  </tr>

  <tr>

   <td width="64">HIGH</td>

   <td width="64">LOW</td>

   <td width="64">HIGH</td>

   <td width="64">LOW</td>

   <td width="148">Special Character</td>

  </tr>

  <tr>

   <td width="64">HIGH</td>

   <td width="64">LOW</td>

   <td width="64">HIGH</td>

   <td width="64">HIGH</td>

   <td width="148">Special Character</td>

  </tr>

  <tr>

   <td width="64">HIGH</td>

   <td width="64">HIGH</td>

   <td width="64">LOW</td>

   <td width="64">LOW</td>

   <td width="148">Special Character</td>

  </tr>

  <tr>

   <td width="64">HIGH</td>

   <td width="64">HIGH</td>

   <td width="64">LOW</td>

   <td width="64">HIGH</td>

   <td width="148">Special Character</td>

  </tr>

  <tr>

   <td width="64">HIGH</td>

   <td width="64">HIGH</td>

   <td width="64">HIGH</td>

   <td width="64">LOW</td>

   <td width="148">Special Character</td>

  </tr>

  <tr>

   <td width="64">HIGH</td>

   <td width="64">HIGH</td>

   <td width="64">HIGH</td>

   <td width="64">HIGH</td>

   <td width="148">Special Character</td>

  </tr>

 </tbody>

</table>




In this lab we will make use of 4 digital pins for the decoder: pin 4 for bit 0, pin 5 for bit 1, pin 6 for bit 2, and pin 7 for bit 3.

<h1>The Circuit</h1>

<strong>Closeup </strong>




<h1>Program the Hardware</h1>

Program your 7 segment display so that it counts up from 0. When it gets to 9 it should loop back to 0 again. Make sure your 7 segment display is set to “cathode”. The default is anode which is incorrect.