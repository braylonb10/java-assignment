# java-assignment
This is my java review code assignment.

I made a number creator class that creates the numbers and values. Things included are the amount of random numbers to generate, the maximum random value, the maximum numerical value, and the minimum numerical value.

I created a user-defined method called 'generateNum' that generates the random numbers into an array.

I created my second user-defined method called numRange which creates the range of the numbers I want to be randomly generated (minimum and maximum values).

In my Main class, the code used in my NumberCreator class got called which allowed me to run my code.

Had to add my generator.generateNum so my array has values in it.

Added note, I separated my two classes so that the code is not too overcrowded on just one main class, and also to make the code easier to access in case I needed to make changes.




Code:




NumberCreator.java:
    
    import java.util.Random;

    public class NumberCreator {
    private int[] num;
    private int maxNum;

        public NumberCreator(int count, int maxNum){
            this.num = new int[count];
            this.maxNum = maxNum;
        }

        public void generateNum(){
            Random rand = new Random();
            for(int i = 0; i < num.length; i++){
                num[i] = rand.nextInt(maxNum) + 1;
            }
        }

        public int numRange(int [] arrayToProcess, int minVal, int maxVal){
            int number = 0;
            for(int i = 0; i < arrayToProcess.length; i++){
                if(arrayToProcess[i] >= minVal && arrayToProcess[i] <= maxVal){
                    number++;
                }
            }

            return number;
        }

        public int[] fetchArrayData(){
            return this.num;
        }
    }


Main.java:
    
    import java.util.Scanner;

    public class Main{
        public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

            System.out.println("Amount of random numbers to generate: ");
            int count = scanner.nextInt();

            System.out.println("Maximum random value: ");
            int maxNum = scanner.nextInt();


            NumberCreator generator = new NumberCreator(count, maxNum);
            generator.generateNum();


            System.out.println("Enter the minimum value: ");
            int minVal = scanner.nextInt();

            System.out.println("Enter maximum value");
            int maxVal = scanner.nextInt();

            int[] data = generator.fetchArrayData();
            int total = generator.numRange(data, minVal, maxVal);

            System.out.println("gSuccessfully generated " + count + " numbers.");
            System.out.println("Found " + total + " numbers between " + minVal + " and " + maxVal + ".");
        }
    }