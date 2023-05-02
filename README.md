Download Link: https://assignmentchef.com/product/solved-coen20-lab6-tetris-and-gyroscopes
<br>



<em>Topics: Bit manipulation, shift and bitwise instructions, bit-banding.            </em>

Tetris is a tile-matching puzzle game, originally designed and programmed by Russian game designer Alexey Pajitnov in which a random sequence of shapes fall down the playing field. The objective of the game is to manipulate these shapes, by moving each one sideways and/or rotating by quarter-turns, so that they form a solid horizontal line with no gaps. When such a line is formed, it disappears and any blocks above it fall down to fill the space. The game ends when the stack of shapes reaches the top of the playing field and no new shapes are able to enter.

Internally, the program stores the layout of each shape as a 16-bit variable that holds an array of up to 4×4 bits.  Shapes are square arrays of 2×2, 3×3 or 4×4. For example, a 3×3 shape would occupy the shaded bits indicated below:




15         14         13         12         11         10          9           8           7           6           5           4           3           2           1           0

<table width="625">

 <tbody>

  <tr>

   <td width="40">col 3</td>

   <td width="39">col 2</td>

   <td width="39">col 1</td>

   <td width="39">col 0</td>

   <td width="39">col 3</td>

   <td width="39">col 2</td>

   <td width="39">col 1</td>

   <td width="39">col 0</td>

   <td width="39">col 3</td>

   <td width="39">col 2</td>

   <td width="39">col 1</td>

   <td width="39">col 0</td>

   <td width="39">col 3</td>

   <td width="39">col 2</td>

   <td width="39">col 1</td>

   <td width="40">col 0</td>

  </tr>

  <tr>

   <td width="40"> </td>

   <td colspan="2" width="78">row 3</td>

   <td width="39"> </td>

   <td width="39"> </td>

   <td colspan="2" width="78">row 2</td>

   <td width="39"> </td>

   <td width="39"> </td>

   <td colspan="2" width="78">row1</td>

   <td width="39"> </td>

   <td width="39"> </td>

   <td colspan="2" width="78">row 0</td>

   <td width="40"> </td>

  </tr>

  <tr>

   <td width="40"> </td>

   <td colspan="2" width="78"> </td>

   <td width="39"> </td>

   <td width="39"> </td>

   <td colspan="2" width="78"> </td>

   <td width="39"> </td>

   <td width="39"> </td>

   <td colspan="2" width="78"> </td>

   <td width="39"> </td>

   <td width="39"> </td>

   <td colspan="2" width="78"> </td>

   <td width="40"> </td>

  </tr>

 </tbody>

</table>

Your task is to implement the following two assembly language functions to store and retrieve individual bits within the array. You are to provide two solutions: The first version must be implemented without using bit-banding or loops. The second version must be implemented using bit-banding.

<strong>BOOL GetBit(uint16_t *bits, uint32_t row, uint32_t col) ; </strong>

<strong>void PutBit(BOOL value, uint16_t *bits, uint32_t row, uint32_t col) ; </strong>

<strong> </strong>

<strong><em>Parameter Description </em></strong>bits The memory address of the 16-bit variable. row A number in the range 0-3 specifying a row. col A number in the range 0-3 specifying a column. value The value (0 or 1) of the bit to be stored.




Test your functions using the C main program that can be downloaded <a href="http://www.cse.scu.edu/~dlewis/book3/labs/Lab6eMain.c">here</a><a href="http://www.cse.scu.edu/~dlewis/book3/labs/Lab6eMain.c">.</a> Your score is displayed at the bottom of the screen. Each shape placed on the field earns 1 point. Filling all the columns of a row so that it disappears earns 100 bonus points. The program uses the blue push button and the onboard gyroscope to control the game:

<ol>

 <li>Push the blue push button to rotate the current shape clockwise 90 degrees.</li>

 <li>Tilt the board left or right to move the current shape left or right.</li>

 <li>Quickly tilt the board towards you to immediately drop the current shape to the bottom.</li>

</ol>





