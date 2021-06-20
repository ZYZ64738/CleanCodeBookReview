# Listing 3-4
`Payroll.java`

```java
public Money calculatePay(Employee e)
throws InvalidEmployeeType {
  switch (e.type) {
  case COMMISSIONED:
    return calculateCommissionedPay(e);
  case HOURLY:
    return calculateHourlyPay(e);
  case SALARIED:
    return calculateSalariedPay(e);
  default:
    throw new InvalidEmployeeType(e.type);
  }
```

