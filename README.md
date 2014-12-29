Tic-Tac-Toe-GUI
===============

import scala.swing._

var playerA = Array.fill(3,3)('?')
var playerB = Array.fill(3,3)('?')
	def checkWinner(bd:Array[Array[Char]]):Char = {
	var winner:Char = '?'                                                //Assuming that there is no winner
	for(ctr <- 0 until bd.length) {
//Checking for matches across each row
     if(bd(ctr)(0)!='?' && bd(ctr)(0) == bd(ctr)(1) && bd(ctr)(0) == bd(ctr)(2))
     winner = bd(ctr)(0)
//Checking for matches across each column
	if(bd(0)(ctr)!='?' && bd(0)(ctr) == bd(1)(ctr) && bd(0)(ctr) == bd(2)(ctr))
	winner = bd(0)(ctr)
	}
//Checking for matches across the two diagonals
	if(bd(0)(0)!='?' && bd(0)(0)==bd(1)(1) && bd(0)(0)==bd(2)(2))
	winner = bd(0)(0)
	if(bd(0)(2)!='?' && bd(0)(2)==bd(1)(1) && bd(0)(2)==bd(2)(0))
	winner = bd(0)(2)
	winner 
 //Return the winner char or '?'
}

val frame = new MainFrame {
  title = "TIC-TAC-TOE"
  var move = 0
  preferredSize = new Dimension(800,800)
  contents = new GridPanel(3,3) { 
  for ( i <- 0 to 2; j <- 0 to 2) { 
    contents += new Button ("-") { 
      action = Action("-")
      { 
       println("You selected location: "+i+ " "+j)
       if(text == "-")
        {
       if(move%2 == 0) 
	{
	text =  "X"
playerA(i)(j) ='1'
	} else{
	text =  "0"
playerB(i)(j) ='2'
	}
       move +=1 
       }
    else println("Can not make that move") 
    } 
}
}
}
}
frame.visible = true
var winner = '?'
while (winner == '?') {
val pA = checkWinner(playerA)
val pB = checkWinner(playerB)
if (pA !='?'){
 winner = pA
println("The winner is player " + pA)
}
if (pB !='?'){ 
winner = pB
println("The winner is player " +pB)
}
}


