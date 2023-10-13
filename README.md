Aim: Demonstrate round robin using threads.
Code:
import java.io.*; 
class job implements Runnable
{
 int process_id,no_of_instr,time_quantum;
 Thread t;
 job(int pid,int instr,int tq)
{ 
 process_id=pid;
 no_of_instr=instr;
 time_quantum=tq;
 t=new Thread(this);
 t.start();
}
public void run()
{
 try 
 { 
 for(int i=1;i<=no_of_instr;i++)
 { 
   System.out.println("Executing instr no"+i+" of process_id");
   Thread.sleep(time_quantum);
 }
 System.out.println("job"+process_id+"is over");
}
catch(InterruptedException e)
   {
     System.out.println("The job has been interrupted...");
   }
 }
} 
class os
{
  public static void main(String args[])
  { 
     try
       {
         int process_id=100,time_quantum=100;
         BufferedReader br=new BufferedReader(new InputStreamReader(System.in));
         System.out.println("Enter a user process starting number:");
         process_id=Integer.parseInt(br.readLine());
         System.out.println("Enter a time quantum(in millis):");
         time_quantum=Integer.parseInt(br.readLine());
         job j1=new job(++process_id,10,time_quantum);
         job j2=new job(++process_id,8,time_quantum);
         job j3=new job(++process_id,6,time_quantum);
        }
        catch(Exception e)
        {
          System.out.println("some process falied to complete...");
          System.out.println("Plz contact system admin...");
        } 
     } 
}
