# Rule: Dependency Injection (IoC)

Prefer dependency injection via constructors or method parameters over manual instantiation (`new Class()`) to promote loose coupling and easier testing.

## Bad
Manually instantiating a dependency inside a method.

```php
public function processOrder($orderId)
{
    $paymentGateway = new StripeGateway();
    $paymentGateway->charge($orderId);
}
```

## Good
Injecting the dependency through the constructor.

```php
protected $paymentGateway;

public function __construct(PaymentGatewayInterface $paymentGateway)
{
    $this->paymentGateway = $paymentGateway;
}

public function processOrder($orderId)
{
    $this->paymentGateway->charge($orderId);
}
```
