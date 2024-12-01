public class Counter {
   
   private static synchronized void print(String message) {
       long time = System.currentTimeMillis();
       time = time % 10000;
       System.out.printf("[%04d]: %s%n", time, message);
   }
   
   static class CountUpThread extends Thread {
       public void run() {
           for(int i = 0; i <= 20; i++) {
               print("thread 1 counting up: " + i);
               try {
                   Thread.sleep(200);
               } catch(InterruptedException e) {
                   e.printStackTrace();
               }
           }
       }
   }
   
   static class CountDownThread extends Thread {
       public void run() {
           for(int i = 20; i >= 0; i--) {
               print("thread 2 counting down: " + i);
               try {
                   Thread.sleep(200);
               } catch(InterruptedException e) {
                   e.printStackTrace();
               }
           }
       }
   }
   
   public static void main(String[] args) {
       print("starting concurrent counter program...");
       
       new CountUpThread().start();
       new CountDownThread().start();
       
       for(int i = 0; i < 5; i++) {
           try {
               Thread.sleep(500);
               print("main thread active--");
           } catch(InterruptedException e) {
               e.printStackTrace();
           }
       }
       
       print("main thread finished.");
   }
}
