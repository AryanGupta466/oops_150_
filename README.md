import java.util.*;
public class Main{
	public static Stack<Integer> in = new Stack<Integer>();
		public static Stack<Integer> out = new Stack<Integer>();
	
		public static void Enqueue(int Items)
		{
		
			while(in.isEmpty()==false)
			{
				out.push(in.pop());
			}
				in.push(Items);
			while(!out.isEmpty())
			{
				in.push(out.pop());
			}
			
		}
			public static int dequeue()
		{
			int x = in.pop();
			return x;
		}
		public static void main(String[] strings)
		{
			Scanner sc = new Scanner(System.in);
			int size = sc. nextInt();
			for(int i =0;i<size;i++)
			{
				Enqueue(i);
		}
                     for(int i =0;i<size;i++)
					 {
						 System.out.print(dequeue()+" ");
					 }





		}
}
// Dequeue efficient queue using stack

import java.util.*;
public class Main {
    public static void main(String args[]) {
        Scanner sc = new Scanner(System.in);
        int N = sc.nextInt();
        int [][] array = new int[N][N];
        for(int i=0; i<N; i++){
            for(int j=0; j<N; j++){
            	array[i][j] = sc.nextInt();
            }
        }
        int index = -1;
        for(int i=0; i<N; i++){
            for(int j=0; j<N; j++){
                if(array[i][j] == 1){
                    index = j;
                    break;
                }
            }
            if(index >= 0){
                break;
            }
		}
		int countingfgfrg = -1;
		for(int i=0; i<N; i++){
			int t = -1;
			for(int j=0; j<N; j++){
				if(array[i][j] == 1){
					t = j;
				}
			}
			if(t < 0){
				countingfgfrg = i;
				break;
			}
		}
		if(index == countingfgfrg){
			System.out.print(countingfgfrg);
			return;
		}
		System.out.print("No Celebrity");
    }
}

// Kartik Bhaiya And The Celebrity Problem



import java.util.*;
public class Main {

	public static void main(String args[])  {
		// Your Code Here
		Scanner sc = new Scanner(System.in);
		int s = sc.nextInt();
		int[] numbers = new int[s];
		for(int i =0;i<s;i++)
		{
			numbers[i] = sc.nextInt();
		}
		span(numbers);
	

	}
	public static void span(int[] numbers)
	{
		Stack<Integer> st = new Stack<Integer>();
		int[] array = new int[numbers.length];
		for(int i=0;i<numbers.length;i++)
		{
			while(!st.isEmpty() && numbers[i]>numbers[st.peek()])
			{
               st.pop();
			}
			if(st.isEmpty())
			{
                array[i] = i+1;
			}
			else
			{
				array[i] = i-st.peek();
			}
			st.push(i);
		}
		for(int j =0;j<array.length;j++)
		{
			System.out.print(array[j]+" ");
		}
		System.out.print("END");
	}

}

// Stock Span


import java.util.*;
public class Main {
    public static void main(String args[]) {
      		Scanner SC=new Scanner(System.in);
				int n=SC.nextInt();
				int q=SC.nextInt();
				
				Stack<Integer> stack1=new Stack<>();
				Stack<Integer> stack2=new Stack<>();
				Stack<Integer> stack3=new Stack<>();
				for(int i=0;i<n;i++)
				{
					stack1.push(SC.nextInt());
				}
				ArrayList<Integer> prime=SOE(10000);

				 for(int i = 0 ; i < q; i++)
				    {
				       // if(stack1.empty())
				         //   break;
				        int cur = prime.get(i);
				        while(!stack1.empty())
				        {
				            int element = stack1.peek();
				            stack1.pop();
				            if(element%cur == 0)
				            {
				                stack2.push(element);
				            }
				            else
				            {
				                stack3.push(element);
				            }
				        }
				        while(!stack2.empty())
				        {
				        	
				            System.out.println(stack2.peek());
				            stack2.pop();
				        }
				       
				        stack1=stack3;
				        while(!stack3.empty())
				            stack3=new Stack<>();
				        
				    }
				    while(!stack1.empty())
				    {
				        System.out.println(stack1.peek());
				        stack1.pop();
				    }
				
				

			}
			
			public static ArrayList<Integer> SOE(int n)
			{
				ArrayList<Integer> list=new ArrayList<>();
				boolean[] primes= new boolean[n+1];
				Arrays.fill(primes, true);
				primes[0]=false;
				primes[1]=false;
				
				for(int table=2;(table *table)<=n; table++)
				{
					if(primes[table]==false)
					{
						continue;
					}
					
					for(int multi=2;(table*multi)<=n;multi++)
					{
						primes[table*multi]=false;
					}
				}
				
				for(int i=2;i<=n;i++)
				{
					if(primes[i])
						list.add(i);
				}
				return list;
				
			}

}


// Playing with cards (In stack)


import java.util.*;
public class Main {
    static Scanner s = new Scanner(System.in);
	public static void main(String args[]) throws Exception {
		// Your Code Here
	
	
	    int q = s.nextInt();
        Main obj = new Main();
        StacksUsingArrays stack = obj.new StacksUsingArrays();
    	Calculate(stack, q);
	}

	public static void Calculate(StacksUsingArrays stack, int q) throws Exception {
	//	Scanner sc=new Scanner(System.in);
	///	int count=0;
		for(int i=0;i<q;i++){
			int a=s.nextInt();
			int b=0;
			if(a==2){
			 b=s.nextInt();
			}
			if(a==2){
				stack.push(b);
			}
			else if( !stack.isEmpty() && a==1){
				System.out.println(stack.pop());
				//count++;
			}
			else if(a==1 && stack.isEmpty()){
					System.out.println("No Code");
			}
		}
		//if(count==0){
		///	System.out.println("No Code");
		//}
 
       //Write Your Code Here
       /* Donot initialize another Scanner use the static scanner already declared*/
	}

	private class StacksUsingArrays {
		private int[] data;
		private int tos;

		public static final int DEFAULT_CAPACITY = 10;

		public StacksUsingArrays() throws Exception {
			// TODO Auto-generated constructor stub
			this(DEFAULT_CAPACITY);
		}

		public StacksUsingArrays(int capacity) throws Exception {
			if (capacity <= 0) {
				System.out.println("Invalid Capacity");
			}
			this.data = new int[capacity];
			this.tos = -1;
		}

		public int size() {
			return this.tos + 1;
		}

		public boolean isEmpty() {
			if (this.size() == 0) {
				return true;
			} else {
				return false;
			}
		}

		public void push(int item) throws Exception {
			if (this.size() == this.data.length) {
			    
			    int[] temp = new int[2 * data.length];
			    for(int i = 0;i < data.length;i++){
			        temp[i] = data[i];
			    }
			    
			    data = temp;
			}
			this.tos++;
			this.data[this.tos] = item;
		}

		public int pop() throws Exception {
			if (this.size() == 0) {
				throw new Exception("Stack is Empty");
			}
			int retVal = this.data[this.tos];
			this.data[this.tos] = 0;
			this.tos--;
			return retVal;
		}

		public int top() throws Exception {
			if (this.size() == 0) {
				throw new Exception("Stack is Empty");
			}
			int retVal = this.data[this.tos];
			return retVal;
		}

		public void display() throws Exception {
			if (this.size() == 0) {
				throw new Exception("Stack is Empty");
			}
			for (int i = this.tos; i >= 0; i--) {
				System.out.println(this.data[i]);
			}

		}

	}

}

// Kartik Sir and Coding
 


import java.util.*;
public class Main {

	public static void main(String[] args) throws Exception {
		// TODO Auto-generated method stub
		Scanner s = new Scanner(System.in);
		String str = s.next();
		Main mainobj = new Main();
		StacksUsingArrays stack = mainobj.new StacksUsingArrays(1000);
		if (isBalanced(str, stack)) {
			System.out.println("Yes");
		} else {
			System.out.println("No");
		}

	}

	public static boolean isBalanced(String str, StacksUsingArrays stack) throws Exception {
              
			  for(int i=0;i<str.length();i++)
			  {
				  if(str.charAt(i)=='{' || str.charAt(i)=='('|| str.charAt(i)=='[')
				  {
					  stack.push(str.charAt(i));
				  }
				  else if(str.charAt(i)=='}' && !stack.isEmpty() && stack.peek()=='}')
				  {
                       stack.pop();
				  }
				   else if(str.charAt(i) == ')' && !stack.isEmpty() && stack.peek() == '(')
				   {
                      stack.pop();
				   }
              
            else if(str.charAt(i) == ']' && !stack.isEmpty() && stack.peek() == '[')
			{
                     stack.pop();
			}
             else{
				 return false;
			 } 
        
			  }
			  return true;
		
	}

	private class StacksUsingArrays {
		private int[] data;
		private int tos;

		public static final int DEFAULT_CAPACITY = 10;

		public StacksUsingArrays() throws Exception {
			// TODO Auto-generated constructor stub
			this(DEFAULT_CAPACITY);
		}

		public StacksUsingArrays(int capacity) throws Exception {
			if (capacity <= 0) {
				System.out.println("Invalid Capacity");
			}
			this.data = new int[capacity];
			this.tos = -1;
		}

		public int size() {
			return this.tos + 1;
		}

		public boolean isEmpty() {
			if (this.size() == 0) {
				return true;
			} else {
				return false;
			}
		}

		public void push(int item) throws Exception {
			if (this.size() == this.data.length) {
				throw new Exception("Stack is Full");
			}
			this.tos++;
			this.data[this.tos] = item;
		}

		public int pop() throws Exception {
			if (this.size() == 0) {
				throw new Exception("Stack is Empty");
			}
			int retVal = this.data[this.tos];
			this.data[this.tos] = 0;
			this.tos--;
			return retVal;
		}

		public int peek() throws Exception {
			if (this.size() == 0) {
				throw new Exception("Stack is Empty");
			}
			int retVal = this.data[this.tos];
			return retVal;
		}

		public void display() throws Exception {
			if (this.size() == 0) {
				throw new Exception("Stack is Empty");
			}
			for (int i = this.tos; i >= 0; i--) {
				System.out.println(this.data[i]);
			}

		}

	}

}

//  Balanced Parenthesis



import java.util.*;

public class Main {

	protected int size;

	protected int front;
	protected int[] data;

	public Main() {
		this.size = 0;
		this.front = 0;
		this.data = new int[5];
	}

	public Main(int cap) {
		this.size = 0;
		this.front = 0;
		this.data = new int[cap];
	}

	public int size() {
		return size;
	}

	public boolean isEmpty() {
		return (size == 0);
	}

	public void enQueue(int item) throws Exception {
		if (this.size() == this.data.length) {
			int[] oa = this.data;
			int[] na = new int[oa.length * 2];
			for (int i = 0; i < this.size(); i++) {
				int idx = (i + front) % oa.length;
				na[i] = oa[idx];
			}

			this.data = na;
			this.front = 0;
		}

		// if (this.size == this.data.length) {
		// throw new Exception("Main is full");
		// }

		this.data[(front + size) % this.data.length] = item;
		size++;

	}

	public int deQueue() throws Exception {
		if (this.size == 0) {
			throw new Exception("Main is empty");

		}

		int rv = this.data[front];
		front = (front + 1) % this.data.length;
		size--;

		return rv;

	}

	public int getFront() throws Exception {
		if (this.size == 0) {
			throw new Exception("Main is empty");
		}

		int rv = this.data[front];

		return rv;
	}

	public void display() {
		System.out.println();
		for (int i = 0; i < size; i++) {
			int idx = (i + front) % this.data.length;
			System.out.print(this.data[idx] + " ");
		}
        System.out.print("END");
	}

	
    public static int ImpofTime(Main q,int[] orig_order) throws Exception{ 
			int count=0;
			for(int i=0;i<orig_order.length;i++){
				if(orig_order[i]==q.getFront()){
						count++;
						q.deQueue();
				}
				else{
					while(orig_order[i]!=q.getFront()){
						int a=q.getFront();
						q.enQueue(a);
						q.deQueue();
						count++;
					}
					count++;
					q.deQueue();
				}
			}
	return count;
	
    } 


	static Scanner scn = new Scanner(System.in);

	public static void main(String[] args) throws Exception {

		Main q = new Main();

		int n = scn.nextInt();
		int[] process = new int[n];
		for (int i = 0; i < n; i++) {
			q.enQueue(scn.nextInt());
		}
		
		for(int i = 0;i < n;i++){
		
		    process[i] = scn.nextInt();
		}
		
		

		System.out.print(ImpofTime(q,process));
	
	}

}

// Importance of Time



import java.util.*;

public class Main {
	public static void main(String[] args) {

		Scanner scn = new Scanner(System.in);

		int t = scn.nextInt();

		while (t > 0) {
			int n = scn.nextInt();
			int[] arr = new int[n];

			for (int i = 0; i < arr.length; i++)
				arr[i] = scn.nextInt();

			nextLarger(arr);

			t--;
		}

	}

	// Function to print Next Greater Element for each element of the array
	public static void nextLarger(int[] arr) {

// Write Code here
                    Stack<Integer> st = new Stack<Integer>();
                    int[] num = new int[arr.length];
                    for(int i=0;i<arr.length;i++)
                    {
                        while(!st.isEmpty() && arr[i]> arr[st.peek()] )
                        {
                             
                                int ii = st.pop();
                                num[ii] = arr[i];

                        }
                        st.push(i);
                       
                    }
                     while(!st.isEmpty())
                        {
                            int x = st.pop();
                            num[x] = -1;
                        }
                    for(int i=0;i<num.length;i++)
                    {
                        System.out.println(arr[i]+","+num[i]);
                    }
                 

	}
}

// Next Greater Element


import java.util.*;
public class Main {
    public static void main (String args[]) {
            Scanner SCN=new Scanner(System.in);
            int n=SCN.nextInt();
            int arraya[]=new int[n];
            for(int i=0;i<n;i++){
                arraya[i]=SCN.nextInt();
            }
            Stack<Integer>llll=new Stack<>();
            int area=0;
            for(int i=0;i<n;i++){
                while(!llll.isEmpty() && arraya[i]<arraya[llll.peek()]){
                    int k=arraya[llll.pop()];
                    int r=i;
                    if(llll.isEmpty()){
                            area=Math.max(area,k*r);
                    }
                    else{
                        int l=llll.peek();
                        area=Math.max(area,k*(r-l-1));
                    }
                }
                llll.push(i);
            }
            int r=arraya.length;
            while(!llll.isEmpty()){
                    int k=arraya[llll.pop()];
                   // int r=i;
                    if(llll.isEmpty()){
                            area=Math.max(area,k*r);
                    }
                    else{
                        int l=llll.peek();
                        area=Math.max(area,k*(r-l-1));
                    }
                }
                System.out.println(area);
    }
}


// Recycling



import java.util.*;
class Main
{
    // Find the next greater element for every array element
    public static void findNextGreaterElements(int[] input)
    {
        // base case
        if (input == null) {
            return;
        }
 
        // do for each element
        for (int i = 0; i < input.length; i++)
        {
            // keep track of the next greater element for element `input[i]`
            int next = -1;
 
            // process elements on the right of element `input[i]`
            for (int j = i + 1; j < input.length; j++)
            {
                // break the inner loop at the first larger element on the
                // right of element `input[i]`
                if (input[j] > input[i])
                {
                    next = input[j];
                    break;
                }
            }
 
            System.out.print(next +" ");
        }
    }
 
    public static void main(String[] args)
    { 
		Scanner sc=new Scanner(System.in);
		int n=sc.nextInt();
        int[] input = new int[n];
		for(int i=0;i<n;i++){
			input[i]=sc.nextInt();
		}
        findNextGreaterElements(input);
    }
}

// Find the greater element

import java.util.*;
public class Main {
    public static void main(String args[]) {
			Scanner scn=new Scanner(System.in);
			int a=scn.nextInt();
			String array[]=new String [a];
			for(int i=0;i<a;i++){
				array[i]=scn.next();;;;;;;;;;
			}
			
		//	int arr1[]=new int[a+1];
		
			for(int i=0;i<a;i++){
				int count=1;
				String g=array[i];
					Stack<Integer>ll=new Stack<>();
					int arr1[]=new int[g.length()+1];
				for(int j=0;j<arr1.length;j++){
						if(j==g.length()||g.charAt(j)=='I'){
							arr1[j]=count++;
						//	count++;
							while(!ll.isEmpty() && g.charAt(ll.peek())=='D'){
								arr1[ll.pop()]=count++;
							//	count++;
							}
						}
						else{
							ll.push(j);
						}
				}
				while(!ll.isEmpty()){
				arr1[ll.pop()]=count++;
				}
				String k="";
				for( int z=0;z<arr1.length;z++){
					k+=arr1[z];
				}
				System.out.println(k);
				
			}
    }
}
 

// Form minimum number from given Sequence


import java.util.*;
public class Main {

	public static void main(String args[]) throws Exception {
		// Your Code Here
		Scanner s = new Scanner(System.in);
		int N=s.nextInt();
		Main mainobj = new Main();
		StacksUsingArrays obj = mainobj.new StacksUsingArrays(N);
		//StacksUsingArrays helper=mainobj.new StacksUsingArrays(N);
		for(int i=1;i<=N;i++){
			obj.push(s.nextInt());
		}
		obj.reverseStack(obj);
		obj.display();

	}

	private class StacksUsingArrays {
		private int[] data;
		private int tos;

		public static final int DEFAULT_CAPACITY = 10;

		public StacksUsingArrays() throws Exception {
			// TODO Auto-generated constructor stub
			this(DEFAULT_CAPACITY);
		}

		public StacksUsingArrays(int capacity) throws Exception {
			if (capacity <= 0) {
				System.out.println("Invalid Capacity");
			}
			this.data = new int[capacity];
			this.tos = -1;
		}

		public int size() {
			return this.tos + 1;
		}

		public boolean isEmpty() {
			if (this.size() == 0) {
				return true;
			} else {
				return false;
			}
		}

		public void reverseStack(StacksUsingArrays st) throws Exception {
			   
                if(st.isEmpty())
				{
					return;
				}
			   int x = st.pop();
			   reverseStack(st);
			   Insert(st,x);






		}
		public  void Insert(StacksUsingArrays st,int it) throws Exception
		{
              if(st.isEmpty())
			  {
				  st.push(it);
				  return;
			  }

			int y = st.pop();
			Insert(st,it);
			st.push(y);
		}

		public void push(int item) throws Exception {
			if (this.size() == this.data.length) {
				throw new Exception("Stack is Full");
			}
			this.tos++;
			this.data[this.tos] = item;
		}

		public int pop() throws Exception {
			if (this.size() == 0) {
				throw new Exception("Stack is Empty");
			}
			int retVal = this.data[this.tos];
			this.data[this.tos] = 0;
			this.tos--;
			return retVal;
		}

		public int top() throws Exception {
			if (this.size() == 0) {
				throw new Exception("Stack is Empty");
			}
			int retVal = this.data[this.tos];
			return retVal;
		}

		public void display() throws Exception {
			if (this.size() == 0) {
				throw new Exception("Stack is Empty");
			}
			for (int i = this.tos; i >= 0; i--) {
				System.out.println(this.data[i]);
			}
			
		}

	}

}

// REVERSE A STACK USING RECURSION


import java.util.*;
public class Main {
    public static void main (String args[]) {
		Scanner sc=new Scanner(System.in);
		int t=sc.nextInt();
		while(t-->0){
			int n=sc.nextInt();
			int arr[]=new int[n];
			for(int i=0;i<n;i++){
				arr[i]=sc.nextInt();
			}
				int count=0;
				int count1=0;
				int a=0;
			for(int i=0;i<n;i++){
			
				if(arr[i]==1){
					count++;
				}
				else if(arr[i]==0){
					count1++;
				}
				if(count1>count){
					a=1;
					System.out.println("Invalid");
					break;
				}
			}
			if(a==0)
			System.out.println("Valid");
		}

    }
}

//The Queue Game

import java.util.*;
public class Main {
    public static void main(String args[]) {
      Scanner your_name=new Scanner(System.in);
      int tokens=your_name.nextInt();
      while(tokens-->0){
          int lenter=your_name.nextInt();
          int kerpenter=your_name.nextInt();
          int stack_holder[]=new int[lenter];
          for(int i=0;i<lenter;i++){
              stack_holder[i]=your_name.nextInt();
          }
          int begining_89=0;
          int termination_89=0;
          int begin_78=0;
          int counter_55=0;
         List<Integer> koloisdt_89=new ArrayList<>();
          while(termination_89<stack_holder.length){
                counter_55++;
                if(counter_55==kerpenter){
                    while(begining_89<=termination_89){
                        if(stack_holder[begining_89]<0){
                            koloisdt_89.add(stack_holder[begining_89]);
                            begin_78++;
                            begining_89=begin_78;
                            counter_55--;
                            break;
                        }
                        else { 
                            if((begining_89-begin_78)==(kerpenter-1)){
                            koloisdt_89.add(0);
                            begin_78+=1;
                            begining_89=begin_78;
                            counter_55--;
                           }
                            
                        }
                        begining_89++;
                    }
                }
                termination_89++;

                }
                for(int i=0;i<koloisdt_89.size();i++)
                    System.out.print(koloisdt_89.get(i)+" ");
                System.out.println("");;;;;;;;;;;;;;;;;;;;;;;;;
				;;;;;;;;;;;;;;;;;;;;;;;;;
          }
      }
    }

// First negative integer in every window of size k


import java.util.*;
public class Main {
	
	public static void reccur_settter(String[] setter_56 , String upper_89,int cold_couter,String store_fiven){

	   int s=store_fiven.length();
            if(cold_couter == s)
            {
            System.out.println(upper_89);
                return;
			}
            if(store_fiven.charAt(cold_couter)!='0')
            {
                  int num=store_fiven.charAt(cold_couter)-'0';
                  String ch=setter_56[num];
                 reccur_settter(setter_56,upper_89+ch,cold_couter+1,store_fiven);
            }
           if(cold_couter<s-1)
           {
              int num2=store_fiven.charAt(cold_couter)-'0';
               int num3=store_fiven.charAt(cold_couter+1)-'0';
               int num4=(num2*10)+(num3);
               if(num4<=26)
               {
                    String ch1=setter_56[num4];
                   reccur_settter(setter_56,upper_89+ch1,cold_couter+2,store_fiven);
               }
           }
	}
     
    public static void main(String args[]) {
        Scanner taker_89=new Scanner(System.in);
        int lenth=taker_89.nextInt();
        String setter_56[]={" ","A","B","C","D","E","F","G","H","I","J","K","L","M","N","O","P","Q","R","S","T","U","V","W","X","Y","Z"};
		String temp="";;;;;;;;;;;;;;;;
		;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;;
		temp+=lenth;;;;;;;;;;;;;;;;;;;;;;
		;;;;;;;;;;;;;;;;;;;;
		reccur_settter(setter_56,"",0,temp);
    }        
}

// Mapped Strings


import java.util.*;
public class Main {
    public static void main (String args[]) {
		Scanner sc=new Scanner(System.in);
			Stack<Integer>s1=new Stack<Integer>();
			Stack<Integer>s2=new Stack<Integer>();
			int x=sc.nextInt();
			String []arr=new String[x];
			for(int i=0;i<x;i++){
				arr[i]=sc.next();
			}
			for(int i=0;i<x;i++){
				String a=arr[i];
				if(a.equals("push")){
					int n=sc.nextInt();
					if(s1.isEmpty()){
						s1.push(n);
						s2.push(n);
					}
					else{
						s1.push(n);
					s2.push(Math.min(n,s2.peek()));
					}
					
					

				}
				else if(a.equals("pop")){
					if(s1.isEmpty()){
						continue;
					}
					s1.pop();
					s2.pop();
				}
				else if(a.equals("getMin")){
				//	if(s2.isEmpty()){
				///		continue;
			//		}
					System.out.print(s2.peek()+" ");
					//int z=s2.pop();
				}
				else if(a.equals("top")){
					//if(s1.isEmpty()){
					//	continue;
					//}
					System.out.print(s1.peek()+" ");
				}
			}

    }
}

// Min stack

import java.util.*;
public class Main {
    public static void main (String args[]) {
        Scanner SC=new Scanner(System.in);
        String a=SC.next();
        ArrayList<String>listing=new ArrayList<>();
        permutation(a,"",listing);
        Collections.sort(listing);
        for(int i=listing.size()-1;i>=0;i--){
            System.out.print(listing.get(i)+" ");
        }

    }
     public static void permutation(String p,String up, ArrayList<String> listing){
        if(p.isEmpty()){
            listing.add(up);
                 return;
        }
        char a=p.charAt(0);
       if((int)(a)>=65 && (int)(a)<=90){
           permutation(p.substring(1),up+a,listing);
           permutation(p.substring(1),up+(char)(a+32),listing);
       }
       else if((int)(a)>90 && (int) (a)<=122){
            permutation(p.substring(1),up+a,listing);
           permutation(p.substring(1),up+(char)(a-32),listing);
       }
       else{
           permutation(p.substring(1),up+a,listing);
       }
       
        }
        
    }

// New Permutation

import java.util.*;
public class Main{
    static int count=0;
    public static void main(String[]args){
        Scanner scn=new Scanner(System.in);
        int n=scn.nextInt();
        List<Integer>list=new ArrayList<>();
        int arrays[]=new int[n];
        for(int i=0;i<arrays.length;i++){
            arrays[i]=i;
        }
        boolean[]a=new boolean[n];

      //  System.out.println(2);
        permutation(n,list,arrays,a);
        System.out.println(count);
    }
   public static void permutation(int n,List<Integer>list,int arrays[],boolean[]a){
        if(list.size()==arrays.length){
            for(int i=0;i<list.size();i++){
                    if(list.get(i)==i)
                    return;
            }
            count++;
            return;

        }
        for(int j=0;j<arrays.length;j++){
            if(!a[j]){
                a[j]=true;
                list.add(arrays[j]);
                permutation(n,list,arrays,a);
                list.remove(list.size()-1);
                a[j]=false;
            }
        }
    }
}

// Girlfriends Derangements

import java.util.*;
public class Main {

	public static void main(String[] args) throws Exception {
		// TODO Auto-generated method stub
		Scanner s = new Scanner(System.in);
		
		int n = s.nextInt();
		int[] arr = new int[n];
		
		for(int i = 0;i < n;i++)
		    arr[i] = s.nextInt();
		    
    		Main mainobj = new Main();
    		StacksUsingArrays stack = mainobj.new StacksUsingArrays(1000);
    		System.out.println(hist(arr, stack));
		}
	

	public static long hist(int[] arr, StacksUsingArrays stack) throws Exception {

	      // Stack<Integer>ll=new Stack<>();
            long area=0;
            for(int i=0;i<arr.length;i++){
                while(!stack.isEmpty() && arr[i]<arr[stack.top()]){
                    int k=arr[stack.pop()];
                    int r=i;
                    if(stack.isEmpty()){
                            area=Math.max(area,(long)k*r);
                    }
                    else{
                        int l=stack.top();
                        area=Math.max(area,(long)k*(r-l-1));
                    }
                }
                stack.push(i);
            }
            int r=arr.length;
            while(!stack.isEmpty()){
                    int k=arr[stack.pop()];
                   // int r=i;
                    if(stack.isEmpty()){
                            area=Math.max(area,(long)k*r);
                    }
                    else{
                        int l=stack.top();
                        area=Math.max(area,(long)k*(r-l-1));
                    }
                }
				return area;
              //  System.out.println(area);
	    
	}

	private class StacksUsingArrays {
		private int[] data;
		private int tos;

		public static final int DEFAULT_CAPACITY = 10;

		public StacksUsingArrays() throws Exception {
			// TODO Auto-generated constructor stub
			this(DEFAULT_CAPACITY);
		}

		public StacksUsingArrays(int capacity) throws Exception {
			if (capacity <= 0) {
				System.out.println("Invalid Capacity");
			}
			this.data = new int[capacity];
			this.tos = -1;
		}

		public int size() {
			return this.tos + 1;
		}

		public boolean isEmpty() {
			if (this.size() == 0) {
				return true;
			} else {
				return false;
			}
		}

		public void push(int item) throws Exception {
			if (this.size() == this.data.length) {
				throw new Exception("Stack is Full");
			}
			this.tos++;
			this.data[this.tos] = item;
		}

		public int pop() throws Exception {
			if (this.size() == 0) {
				throw new Exception("Stack is Empty");
			}
			int retVal = this.data[this.tos];
			this.data[this.tos] = 0;
			this.tos--;
			return retVal;
		}

		public int top() throws Exception {
			if (this.size() == 0) {
				throw new Exception("Stack is Empty");
			}
			int retVal = this.data[this.tos];
			return retVal;
		}

		public void display() throws Exception {
			if (this.size() == 0) {
				throw new Exception("Stack is Empty");
			}
			for (int i = this.tos; i >= 0; i--) {
				System.out.println(this.data[i]);
			}

		}

	}

}

// HISTOGRAM


import java.util.*;
public class Main {
    static int hi=0;
    public static void main(String[] args){
        Scanner scn=new Scanner(System.in);
        int n=scn.nextInt();
        int SUM=0;
        int board[][]=new int[n][n];
        for(int i=0;i<board.length;i++){
            for(int j=0;j<board.length;j++){
                board[i][j]=scn.nextInt();

                if(board[i][j]==1)
                SUM+=1;
            }
        }
       funkyChessBoard(board,0,0,0);
     //  System.out.println(hi);
       System.out.println(SUM-hi);


    }
    //static int hi=0;
    public static void funkyChessBoard(int[][]board,int count,int row,int col){
        //3int hi=0;
        if(row<0||row>=board[0].length||col<0||col>=board[0].length||board[row][col]==0){
        return ;
        }
        board[row][col]=0;
        hi=Math.max(hi,count+1);
       
        funkyChessBoard(board, count+1, row+1, col+2);
        funkyChessBoard(board, count+1, row+2, col+1);
        funkyChessBoard(board, count+1, row-2, col+1);
        funkyChessBoard(board, count+1, row-1, col+2);
        funkyChessBoard(board, count+1, row-2, col-1);
        funkyChessBoard(board, count+1, row-1, col+2);
        funkyChessBoard(board, count+1, row+1, col-2);
        funkyChessBoard(board, count+1, row+2, col-1);
        board[row][col]=1;
       // return high;
    }
    
}

// Funky Chess Board

import java.util.*;
public class Main {
    public static void main (String args[]) {

        Scanner sc=new Scanner(System.in);
        int N=sc.nextInt();
        int M=sc.nextInt();
        int U=sc.nextInt();

        char board_problem[][]=new char[N][M];

        char copy_ingf[][]=new char[N][M];

        for(int i=0;i<N;i++)
        {
            String s=sc.next();

            for(int j=0;j<M;j++)
            {
                board_problem[i][j]=s.charAt(j);;
            }
        }
        String [] arr=new String[U];

        for(int i=0;i<U;i++)
            arr[i]=sc.next();
        
        for(int i=0;i<N;i++)
        {
            for(int j=0;j<M;j++)
            {
                copy_ingf[i][j] = board_problem[i][j];
            }
        }
        ArrayList<String> ll=new ArrayList<>();
        for(int w=0;w<U;w++)
        {
            String word="";
            word+=arr[w];

            for(int i=0;i<board_problem.length;i++)
		    {
			    for(int j=0;j<board_problem[0].length;j++) {
				
				 // if we remove then it also run but complexity will be high ,here we search first char of word and then send.
					
					if(Word_Search(board_problem,i,j,word,0)){

                        ll.add(word);
                    }
			    }
		    }
            for(int i=0;i<N;i++)
            {
                for(int j=0;j<M;j++)
                {
                    board_problem[i][j]=copy_ingf[i][j];
                }
            }
        }
        Collections.sort(ll);

        for(int i=0;i<ll.size();i++)
            System.out.print(ll.get(i)+" ");

        // for(int i=0;i<N;i++)
        // {
        //     for(int j=0;j<M;j++)
        //     {
        //         System.out.print(board_problem[i][j]);
        //     }
        //     System.out.println();
        // }
    }
    public static boolean Word_Search(char[][] maze,int cr,int cc,String word,int idx)
		{
			if(idx==word.length()) {
				return true;
			}
			if(cr<0 || cc<0 || cr>=maze.length || cc>=maze[0].length || maze[cr][cc]!=word.charAt(idx)) {
				return false;
			}
			
			int [] r= {-1,1,0,0};
			int [] c= {0,0,-1,1};
			
			maze[cr][cc]='*';           
			boolean ans=false;
			
			for(int i=0;i<c.length;i++) {
				
				ans=Word_Search(maze,cr+r[i],cc+c[i],word,idx+1);
				
				if(ans) {
					
					return ans;
				}
			}
			maze[cr][cc]=word.charAt(idx); // this is because jab call laga hoga then idx par wahi char hoga (word ke idx index par).
			return false;
		}

}

// Search Word in Monu Bhaiya's Board





import java.util.*;
public class Main {
	public static String [] keypad={ " ", ".+@$", "abc", "def", "ghi", "jkl" , "mno", "pqrs" , "tuv", "wxyz" };
    public static void main(String args[]) {

		Scanner sc=new Scanner(System.in);
		String str=sc.next();
		PrintKeyCombination(str,"");
    }
	public static void PrintKeyCombination(String str,String combination)
	{
		if(str.length()==0)
		{
			System.out.println(combination+" ");
			return ;
		}
		char curr=str.charAt(0);
		String map=keypad[curr-'0'];

		for(int i=0;i<map.length();i++)
			PrintKeyCombination(str.substring(1), combination+map.charAt(i));
	}
}


// Smart Keypad - I



















 


