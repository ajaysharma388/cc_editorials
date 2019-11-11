Editorial: 💡 Stock Span

The span Si of the stock’s price on a given day i is defined as the maximum number of consecutive days just before the given day, for which the price of the stock on the current day is less than or equal to its price on the given day.
For example, if an array of 7 days prices is given as {100, 80, 60, 70, 60, 75, 85}, then the span values for corresponding 7 days are {1, 1, 1, 2, 1, 4, 6} 
For computing this problem we will use stack data structure. Time complexity of this method is O(N) where N is the size of stock price array.
In this method S[i] (stock span value) on day i can be easily computed if we know the closest day preceding i, such that the price is greater than on that day than the price on day i.

Function:

public static int[] StockSpanUsingStacks(int[] prices, Stack<Integer> stack) throws Exception {

        // span array stores the value of stock span for each day
        int[] span = new int[prices.length];

         // pushing the index of first day
        stack.push(0);

        // span for 1st day will always be 1
        span[0] = 1;

        // Iterating over the prices array
        for (int i = 1; i < prices.length; i++) {

           // poping days from stack when price of the i th day is greater than the price of day which is on top of stack
            while (stack.size() != 0 && prices[i] > prices[stack.top()]) {
                stack.pop();
            }

            if (stack.size() == 0) {

             // then all the previous prices are smaller than the price on the  ith day 
                span[i] = i + 1;
            } else {

              // the previous highest price will be on the top of the stack 
                span[i] = i - stack.top();
            }

              // pushing the index of the price array which is the number of day in stack
            stack.push(i);
        }
        return span;

    }