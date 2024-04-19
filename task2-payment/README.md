# Multiple Payment Processing Providers Handler

To handle multiple payment processing providers in a flexible and maintainable way, we can use the Factory Method design pattern. This pattern allows us to define an interface for creating objects but let subclasses decide which class to instantiate.

## Explanation

1. **Enum `PaymentProcessorType`**: Enum representing available payment processors: `Stripe`, `Braintree`, and `PayPal`.

2. **Interface `PaymentProcessor`**: Common interface for all payment processor classes, defining the `processPayment` method to handle payment processing asynchronously and return a `Promise<string>` representing the payment ID.

3. **Payment Processor Classes**:
    - `Stripe`: Simulates processing a payment through the Stripe API and returns a simulated Stripe payment ID after a delay.
    - `Braintree`: Simulates processing a payment through the Braintree API and returns a simulated Braintree payment ID after a delay.
    - `PayPal`: Simulates processing a payment through the PayPal API and returns a simulated PayPal payment ID after a delay.

4. **Order Processing Class `OrderProcessor`**:
    - Manages the order processing logic.
    - Creates an instance of the selected payment processor based on the provided `paymentProcessorType`.
    - Provides a method `processOrder` to process an order by delegating payment processing to the selected payment processor.

5. **Function `payOrder`**:
    - Simulation of the process of creating an `OrderProcessor` instance and processing an order.
    - Takes an `amount` and a `PaymentProcessorType` as input and returns a `Promise<string>` representing the payment ID after processing the order.
