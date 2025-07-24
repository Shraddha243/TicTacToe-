# TicTacToe-
# only core java concept based Tictactoe game
package tictactoe;


public class Tictactoe {
	static String[][] board = new String[3][3];

    public Tictactoe() {
        for (int i = 0; i < 3; i++) {
            for (int j = 0; j < 3; j++) {
                board[i][j] = " ";
            }
        }
    }

    public static void displayBoard() {
    	System.out.println("-------------");
        for (int i = 0; i < 3; i++) {
            for (int j = 0; j < 3; j++) {
                System.out.print("| " + board[i][j] + " ");
            }
            System.out.println("|");
            System.out.println("-------------");
        }
    }

    public static boolean checkrowwin() {
        for (int i = 0; i < 3; i++) {
            if (!board[i][0].equals(" ") &&
                board[i][0].equals(board[i][1]) &&
                board[i][1].equals(board[i][2])) {
                return true;
            }
        }
        return false;
    }

    public static boolean checkcolwin() {
        for (int j = 0; j < 3; j++) {
            if (!board[0][j].equals(" ") &&
                board[0][j].equals(board[1][j]) &&
                board[1][j].equals(board[2][j])) {
                return true;
            }
        }
        return false;
    }

    public static boolean checkdiagonalwin() {
        if (!board[0][0].equals(" ") &&
            board[0][0].equals(board[1][1]) &&
            board[1][1].equals(board[2][2])) {
            return true;
        }

        if (!board[0][2].equals(" ") &&
            board[0][2].equals(board[1][1]) &&
            board[1][1].equals(board[2][0])) {
            return true;
        }

        return false;
    }
}
package tictactoe;

import java.util.Scanner;

public class HumanPlayer {
	String name;
    String symbol;
    Scanner sc = new Scanner(System.in);

    public HumanPlayer(String name, String symbol) {
        this.name = name;
        this.symbol = symbol;
    }

    public void makeMove() {
        int row, col;

        while (true) {
            System.out.println("Enter the row and col (0, 1, 2): ");
            row = sc.nextInt();
            col = sc.nextInt();

            if (row >= 0 && row < 3 && col >= 0 && col < 3) {
                if (Tictactoe.board[row][col].equals(" ")) {
                    Tictactoe.board[row][col] = symbol;
                    break;
                } else {
                    System.out.println("Cell already taken! Try again.");
                }
            } else {
                System.out.println("Invalid position! Try again.");
            }
        }
    }
}
package tictactoe;


public class LaunchGame {
public static void main(String[] args) {
	
	 Tictactoe t = new Tictactoe();
     HumanPlayer p1 = new HumanPlayer("Bob", "X");
     HumanPlayer p2 = new HumanPlayer("Priya", "O");
    //AIplayer p3=new  AIplayer("TAI","O");
    		
     HumanPlayer cp = p1;

     while (true) {
         System.out.println(cp.name + "'s turn:");
         cp.makeMove();
         Tictactoe.displayBoard();

         if (Tictactoe.checkrowwin() || Tictactoe.checkcolwin() || Tictactoe.checkdiagonalwin()) {
             System.out.println(cp.name + " has won!");
             break;
         }

         // Switch player
         cp = (cp == p1) ? p2 : p1;
     }
 }
}
        
     
	//t.dispBoard();
	//t.placemark(0, 0, 'x');
	//t.placemark(1, 1, 'x');
	//t.placemark(2, 2, 'x');
	
	//t.dispBoard();
	//System.out.println(t.checkrowwin());
	//System.out.println(t.checkcolwin());
	//System.out.println(t.checkdiagwin());


