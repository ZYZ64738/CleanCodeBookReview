# Listing 3-5
`Employee and Factory`

```java
public abstract class Employee {
  public abstract boolean isPayday();
  public abstract Money calculatePay();
  public abstract void deliverPay(Money pay);
}
-----------------
public interface EmployeeFactory {
  public Employee makeEmployee(EmployeeRecord r) throws InvalidEmployeeType;
}
-----------------
public class EmployeeFactoryImpl implements EmployeeFactory {
  public Employee makeEmployee(EmployeeRecord r) throws InvalidEmployeeType {
    switch (r.type) {
    case COMMISSIONED:
      return new CommissionedEmployee(r);
    case HOURLY:
      return new HourlyEmployee(r);
    case SALARIED:
      return new SalariedEmploye(r);
    default:
      throw new InvalidEmployeeType(r.type);
    }
  }
}
```

