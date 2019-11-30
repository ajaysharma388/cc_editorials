Editorial: 💡 Is Armstrong Number

Algorithm

Take input of number.
Calculate the number od digits of the number in a variable say , cnt.
Exract digit one by one from the number(using % 10).
Raised it to the power of number of digits and add it to sum.
After the loop check if the sum is equal to the original number.
If yes, print true
otherwise, print false.
Code


public static void printAllArmstrongs(int ll,int ul){

       for(int i=ll;i<=ul;i++) {

           int digits=numberOfDigits(i);
           boolean ans=isArmstrong(i,digits);
           if(ans)
               System.out.println(i);
       }
}

public static boolean isArmstrong(int num,int nod){

        int sum=0;

        int temp=num;

        while(num!=0){

            int rem=num%10;

            int p=1;
            for(int i=1;i<=nod;i++)
                p=p*rem;
            sum+=p;

            num/=10;
        }
        if(sum==temp)
            return true;
        else
            return false;
}

public static int numberOfDigits(int num){

        int count=0;
        while(num!=0){
          num=num/10;
          count++;

        }
        return count;
}