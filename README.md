# TIC---TAC---TOE-game

# code: 

def display_board(board):

    print(board[1]+'|'+board[2]+'|'+board[3])

    print('-----')

    print(board[4]+'|'+board[5]+'|'+board[6])

    print('-----')

    print(board[7]+'|'+board[8]+'|'+board[9])


def choice():

    choice =''

    while choice not in ['X','O']:

        choice =input('Please choose X or O:').upper()
        
        if choice not in['X','O']:
            print('oops try again!')
        else:
            if choice == 'X':
                return ('X', 'O')
            else:
                return ('O', 'X')

          
def replace(board,choice,position):

    board[position]=choice


import random

def goes_first():

    if random.randint(1,2)== 1:

        return'Player 1'

    else:

        return'Player 2'


def win(board,choice):

    return ((board[1]==board[2]==board[3]== choice ) or

           (board[4]==board[5]==board[6]== choice) or

            (board[7]==board[8]==board[9]== choice) or

            (board[1]==board[5]==board[9]== choice) or

            (board[3]==board[5]==board[7]== choice) or
            
             (board[1]==board[4]==board[7]==choice) or
            
           (board[2]==board[5]==board[8]==choice)or
            
            (board[3]==board[6]==board[9]==choice))


def space(board,position):

    return board[position]==' '


def full_board(board):

    for i in range(1,10):

        if space(board,i):

            return False

    return True


def ask_position(board):

    position='wrong'

    while position not in [1,2,3,4,5,6,7,8,9] or not space(board,position):

        position = int(input('Choose your position (1-9):'))

        return position


def replay_game():

    return ('Do you want to replay? yes or no?').lower().startswith('y')


print('HELLO FOLKS!')

print('WELCOME TO TIC TAC TOE GAME')


while True:

   
    the_board = [' ']*10

    player1_choice, player2_choice=choice()

    turn= goes_first()

    print(turn + 'will go first')

   
    ask=input('are you ready to play? yes or no:').lower()

    if ask[0]=='y':

        game=True

    else:

        game=False


    while game:

        if turn=='Player 1':

            display_board(the_board)

            position=ask_position(the_board)

            replace(the_board,player1_choice,position)

           
            if win(the_board,player1_choice):

                display_board(the_board)

                print('congratulations! player1 has won the game')

                game=False

            else:

                if full_board(the_board):

                    display_board(the_board)

                    print('DRAW!')

                    break

                else:

                    turn='Player 2'

        else:

            display_board(the_board)

            position=ask_position(the_board)

            replace(the_board,player2_choice,position)

           

            if win(the_board,player2_choice):

                display_board(the_board)

                print('congratulations! player2 has won the game')

                game=False

            else:

                if full_board(the_board):

                    display_board(the_board)

                    print('DRAW!')

                    break

                else:

                    turn='Player 1'
                    
def replay_game():

    return ('Do you want to replay? yes or no?').lower().startswith('y')


if not replay_game():
    break
    
