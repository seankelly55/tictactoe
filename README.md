# tictactoe
Client server TicTacToe Game with additional death match rules

Prototype implementation using ReST

<a href="https://docs.google.com/document/d/1gCbw2i3LLnerep4s8OKk0YkZLuBFC4VmvacwqpfUoWE/"> Official Docs </a>

<b>APIs</b>
<br/>

<pre>

start
	Description: Initiates a new game
	Method: GET
	Inputs: 
	Response: string gameid
	Example: http://cs2.uco.edu/~gq011/tictactoe/?controller=api&method=start&boardsize=3

connect
	Description: Joins a player to a game and returns a player id
	Method: GET
	Inputs: string	gameid
	Response: string playerid
	Example: http://cs2.uco.edu/~gq011/tictactoe/?controller=api&method=connect&gameid=123ghv1234jb	

status
	Description: Get the status of the game
	Method: GET
	Inputs: string	gameid 
	Response: int 0 = game has not started yet
			  int 1 = player 1's turn
			  int 2 = player 2's turn
			  int 3 = player 1 is winner
			  int 4 = player 2 is winner
	Example: http://cs2.uco.edu/~gq011/tictactoe/?controller=api&method=status&gameid=123ghv1234jb	
	
mode
	Description: Get the mode of the game
	Method: GET
	Inputs: string	gameid 
	Response: string tictactoe|slide
	Example: http://cs2.uco.edu/~gq011/tictactoe/?controller=api&method=mode&gameid=123ghv1234jb	
	
move
	Description: place a move
	Method: POST
	Inputs: string	gameid
		string	playerid
		int	position
	Response: true
	Example: http://cs2.uco.edu/~gq011/tictactoe/?controller=api&method=move&gameid=123ghv1234jb&playerid=2131231&position=0	
	
grid
	Description: fetch the current game grid
	Method: POST
	Inputs: string	gameid
	Response: JSON array
	Example: http://cs2.uco.edu/~gq011/tictactoe/?controller=api&method=grid&gameid=123ghv1234jb	

The user who starts the game will be Player 1.
This allows a third party to delegate who is Player 1 and Player 2 to remove any randomness from the outcome.	
	
All responses use http code of 200, if an error occurs the response code is set to 400.
In the event of an error you may also get one of the following error messages as a response:

"Unknown Error"
"Database Error"
"Invalid Move/Command"
"You must provide a valid game ID"
"You cant join this game as it is already full"
"That game does not exist"
"You must provide a valid player ID"
"Player is not part of this game"
"Game not started"
"It is not your turn"
"Game is over"
</pre>
