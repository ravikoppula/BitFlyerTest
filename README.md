##### Logic in C#:
    
```
   class Program
    {
        static void Main(string[] args)
        {

            int blocksize = 1000000; //total bytes of blocksize		
            double answer500000bytes = 13.4376;
            double answer1byte = 0.00002687520;// (13.4376 / 500000)
            int blocks = 1;
            double answer = 0;
            int[] trnsctn = { 57247, 98732, 134928, 77275, 29240, 15440, 70820, 139603,             63718, 143807, 190457, 40572 };
            int sum = 0;
            for (int i = 0; i < trnsctn.Length; i++)
            {
                sum += trnsctn[i];
                if (sum == blocksize) { answer += (answer500000bytes * 2); blocks += 1; sum = 0; }
                else if (sum == 500000) { answer += answer500000bytes ; blocks += 1; sum = 0; }
                else if (sum > blocksize) { i = i - 1; sum = sum - trnsctn[i]; answer += sum * answer1byte; blocks += 1; sum = 0; }
                else { }
            }
            Console.WriteLine("blocks: " + blocks + ", maximum Rewards:" + answer);
            Console.ReadLine();
        }
    }
```

##### OUTPUT
``` 
	blocks: 2, maximum Rewards:23.581912992
```   
  
##### Explanation
``` 
As per note and hint in the given PDF file I write the code as above.
•	One block can contain 1000000bytes only and transactions can’t repeat.
•	In hint they said 500000byte block answer is 13.4376. So if it 1000000 then it is 13.4376*2. But exact 1000000bytes are not came by adding different transactions in that given 12. So, I divided 1byte result as 13.4376/500000. And created blocks less than or equal to 1000000. If it is less than 1000000 then I multiple that value with (13.4376/500000).
•	Based on the above point I got 2 blocks and answer as 23.581912992 
``` 

