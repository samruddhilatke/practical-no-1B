# practical-no-1B
---MESSAGE PASSING



package javaapplication8;
import java.util. Vector,

public class prac1b {
     public static void main(String args[]){ 
     Producer producer + new Producer(); 
     producer.start();
     new Consumer(producer).start();
    }
  }

class Producer extends Thread {
   static final int MAXQUEUE=5;
   private Vector<String> messages=new Vector<String>();
   
public void run(){
  try{
    while(true)
  {
     putMessage(); 
     sleep(1000);
 }catch( InterruptedException e){}
}
private synchronized void putMessage() throws InterruptedException { 
   while (messages.size()==MAXQUEUE) 
    wait();
   messages.addElement(new java.util.Date().toString()); 
   notify();
}

private synchronized String getMessage() throws InterruptedException{
  notify();
  while (message.isEmpty())
    wait();
  String message =(String) message.firstElements();
  message.removeElements(message);
  return message;
  }
}

   class Consumer extends Thread{
     Producer producer;
    Consumer (Producer p){
     producer=p;
    }
    public void run()
    try{
       while(true)
       {
         String message=producer.getMessage();
         System.out.println("got message ::"+ message);
         sleep(2000);
        }
      }catch(InterruptedException e) {}
     }
  }  
