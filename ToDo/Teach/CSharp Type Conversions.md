```C#
double amount = 10.59;
int age = 0;
string ageStr = "50";

age = (int)amount;
age = int.Parse(ageStr);
bool IsSuccess = int.TryParse(ageStr, out age);

string myNewString = string.Format("", age, amount, ageStr);
```