numeroReinas(N,S):-createTablero(N,Tablero),
    			   permutar(Tablero,S),
    			   tableroCorrecto(S).
				
				   createTablero(0,[]).

createTablero(X,[X|R]):-XMenos1 is X - 1,
						XMenos1 >= 0,
    					createTablero(XMenos1,R).
		
					permutar([],[]).

permutar(X,[C|Z]):-seleccionar(X,C,R),permutar(R,Z).
					
				   seleccionar([X|R],X,R).
				   seleccionar([C|R],X,[C|Y]):-seleccionar(R,X,Y).


					tableroCorrecto([]).
tableroCorrecto([C|R]):-not(amenaza(C,R)),
    				 tableroCorrecto(R).

					
					amenaza(X,Prof,[C|_]):- X is C + Prof;
    
    
					X is C - Prof;
    				X = C.

amenaza(X,Prof,[_|R]):- ProfMas1 is Prof +1,
    					amenaza(X,ProfMas1,R).
						amenaza(_,[]):-fail.
						amenaza(X,Y):- amenaza(X,1,Y).
