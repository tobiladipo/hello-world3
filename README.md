package itcs1213_1;

import java.util.Random;
public class Game_crap {
	 static Random random = new Random();

	    public static boolean play(int gameNum) {

	        int die1 = random.nextInt(6) + 1;
	        int die2 = random.nextInt(6) + 1;
	        int roll = 1;
	        int total = die1 + die2;
	        if (gameNum <= 10)
	            System.out.println("Round " + gameNum + " Roll " + roll + " -- " +
	                    "Die1: " + die1 + " , Die2: " + die2 + " -- Total: " + (die1 + die2));

	        if (total == 7 || total == 11) return true;

	        if (total == 2 || total == 12 || total == 3) return false;

	        int points = total;
	        do {
	            roll++;
	            die1 = random.nextInt(6) + 1;
	            die2 = random.nextInt(6) + 1;
	            total = die1+die2;
	            if (gameNum <= 10)
	                System.out.println("Round " + gameNum + " Roll " + roll + " -- " +
	                        "Die1: " + die1 + " , Die2: " + die2 + " -- Total: " + (die1 + die2));


	        } while (total != points && total != 7);
	        if (total == points) return true;
	        else return false;

	    }

	    public static void main(String[] args) {


	        int wins = 0, losses = 0;
	        final int TOTAL_GAMES = 100000;
	        for (int game=1; game<=TOTAL_GAMES;game++){

	            boolean outcome = play(game);
	            if(outcome){
	                wins++;
	                if(game<=10) System.out.println("WIN!"); // if you win!

	            }
	            else {
	                losses++;
	                if(game<=10) System.out.println("LOSS!"); // if you lose 
	            }
	        }

	        System.out.println("OVERALL:");
	        System.out.printf("%d win(s), %d loss(es)\n",wins,losses);

	    }
	}
