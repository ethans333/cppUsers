# cppUsers 🤖
Create user classes and save their information to a text file.

## The ```User``` class and its corresponding functions:

```cpp
class User {
    private:
        int salary;

    public:
        string firstName, lastName;
        int age;
        char gender;
        void canDrink();
        void adjustSalary(int newSalary);

        User(string _firstName, string _lastName, int _age, char _gender, int _salary) {
            firstName = _firstName;
            lastName = _lastName;
            age = _age;
            gender = _gender;
            salary = _salary;
            cout << "User '" << firstName << "' has been created!" << endl;
        }
};

void User::canDrink() {
    if (age >= 21) {
        cout << "Grab A Miller!" << endl;
    } else {
        cout << "No Beer!" << endl;
    }
}

void User::adjustSalary(int newSalary) {
    salary = newSalary;
    cout << firstName << "'s salary was adjusted to " << newSalary << "." << endl;
}
```

## The ```Main``` function.
```cpp
int main() {
    User ethan("Ethan", "Stein", 21, 'M', 15000);
    User tod("Tod", "Smith", 29, 'M', 20000);
    User miley("Miley", "Doe", 23, 'F', 16000);

    User users[] = {ethan, tod, miley};

    ethan.canDrink();
    ethan.adjustSalary(39000);

    ofstream UserFile("./users.txt");

    for (int i = 0; i < sizeof(users)/sizeof(users[0]); i++) {
        User currentUser = users[i];
        UserFile << "First: " << currentUser.firstName + "\n" <<
         "Last: " << currentUser.lastName + "\n" << 
         "Age: " << currentUser.age << "\n\n";
    }

    UserFile.close();

    return 0;
}
```
Initialize ```User``` objects. Append them to a list. Test ```User``` class's functions.
Iterate over object list, appending object's parameters to a text file.
