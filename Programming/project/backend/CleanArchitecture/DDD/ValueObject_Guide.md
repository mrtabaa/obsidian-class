# 📦 Value Object in Domain-Driven Design (DDD)

## ✅ What is a Value Object?

A **Value Object** in DDD is an object that:
- Has **no identity** (unlike an Entity)
- Is **immutable** once created
- Is compared **by value**, not by reference
- Encapsulates **validation and domain logic**

---

## ✅ When to Use Value Objects

Use a Value Object when:
- A piece of data has clear rules (e.g., email format)
- You want to **encapsulate validation**
- The object **doesn’t need an ID**
- The object’s **value defines equality**

---

## ✅ Base Class: `ValueObject.cs`

To avoid rewriting `Equals()` (useful for tests) and `GetHashCode()` for every value object, use this base class:

```csharp
using System.Collections.Generic;
using System.Linq;

public abstract class ValueObject
{
    protected abstract IEnumerable<object?> GetEqualityComponents();

    public override bool Equals(object? obj)
    {
        if (obj is null || obj.GetType() != GetType())
            return false;

        var other = (ValueObject)obj;
        return GetEqualityComponents().SequenceEqual(other.GetEqualityComponents());
    }

    public override int GetHashCode()
    {
        return GetEqualityComponents()
            .Aggregate(1, (current, obj) => current * 23 + (obj?.GetHashCode() ?? 0));
    }

    public static bool operator ==(ValueObject? left, ValueObject? right)
    {
        return Equals(left, right);
    }

    public static bool operator !=(ValueObject? left, ValueObject? right)
    {
        return !Equals(left, right);
    }
}
```

---

## ✅ Example: `Email` as a Value Object

```csharp
public class Email : ValueObject
{
    public string Value { get; }

    private Email(string value)
    {
        Value = value;
    }

    public static Email Create(string value)
    {
        if (string.IsNullOrWhiteSpace(value) || !Regex.IsMatch(value, @"^([\w\.\-]+)@([\w\-]+)((\.(\w){2,5})+)$"))
            throw new Exception("Invalid email");

        return new Email(value.Trim().ToLowerInvariant());
    }

    protected override IEnumerable<object?> GetEqualityComponents()
    {
        yield return Value;
    }

    public override string ToString() => Value;
}
```

---

## ✅ How to Use It in an Aggregate (e.g., AppUser)

```csharp
public class AppUser
{
    public Guid Id { get; private set; }
    public Email Email { get; private set; }

    public static AppUser Create(string name, string emailRaw, string password)
    {
        var email = Email.Create(emailRaw);

        return new AppUser
        {
            Id = Guid.NewGuid(),
            Email = email
        };
    }
}
```

To access the raw string:

```csharp
Console.WriteLine(user.Email.Value);
```

---

## ✅ Benefits of Using Value Objects

| Benefit                      | Description                                      |
|-----------------------------|--------------------------------------------------|
| 🔒 Encapsulated validation   | All rules live inside `Email.Create(...)`       |
| ✅ Immutable                 | Cannot change value after creation              |
| 🧪 Testable                  | Easy to test, compare, and debug                |
| 🧹 Clean code                | Avoids scattered string validation              |
| 🔁 Reusable                  | Use `Email` in multiple domain models           |
| 🤝 Value-based equality      | Two emails with same value are considered equal |

---

## ✅ When *Not* to Use a Value Object

- When the data **needs an identity**
- When the object **mutates** over time
- When comparing **by reference** is required

---

## 🧠 Final Notes

- Use `.Value` to expose the raw data (e.g., for saving to DB)
- Override `Equals()` and `GetHashCode()` (use a base class for DRY)
- Use value objects for clean, safe, and expressive domain modeling

---

## ✅ TL;DR

Value objects are small, immutable, rule-enforcing types that make your domain model **robust**, **safe**, and **expressive**.
