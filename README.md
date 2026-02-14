# String-
import java.util.concurrent.Callable;

class OrderTask implements Callable<String> {

    private int orderId;

    public OrderTask(int orderId) {
        this.orderId = orderId;
    }

    @Override
    public String call() throws Exception {
        System.out.println("Processing Order: " + orderId + 
                           " by " + Thread.currentThread().getName());

        Thread.sleep(1000); // simulate delay

        if (orderId == 4) {
            throw new RuntimeException("Payment Failed for Order " + orderId);
        }

        return "Order " + orderId + " Completed";
    }
}
