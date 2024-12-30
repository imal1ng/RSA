# AES
## Lý thuyết 
```cpp
#include <iostream>
#include <vector>
#include <cmath>
#include <limits>

using namespace std;

bool Prime(int num) {
    if (num <= 1) return false;
    if (num <= 3) return true;
    if (num % 2 == 0 || num % 3 == 0) return false;
    for (int i = 5; i * i <= num; i += 6) {
        if (num % i == 0 || num % (i + 2) == 0) return false;
    }
    return true;
}

int getValidIntInput(const string& prompt) {
    int value;
    while (true) {
        cout << prompt;
        cin >> value;
        if (cin.fail()) {
            cin.clear(); 
            cin.ignore(numeric_limits<streamsize>::max(), '\n'); 
            cout << "Nhap so di thg db." << endl;
        } else {
            break;
        }
    }
    return value;
}

int main() {
    int rows = getValidIntInput("rows: ");
    int cols = getValidIntInput("columns: ");

  
    vector<vector<int> > matrix(rows, vector<int>(cols));

   
    cout << "Prime numbers:" << endl;
    for (int i = 0; i < rows; ++i) {
        for (int j = 0; j < cols; ++j) {
            int value;
            while (true) {
                cout << "[" << i << "][" << j << "]: ";
                cin >> value;

                
                if (cin.fail()) {
                    cin.clear(); 
                    cin.ignore(numeric_limits<streamsize>::max(), '\n'); 
                    cout << "Nhap so di thg db : ";
                } else if (!Prime(value)) {
                    cout << "The number is not prime. Nhap lai : ";
                } else {
                    matrix[i][j] = value;
                    break;
                }
            }
        }
    }
    
    for (int i = 0; i < rows; ++i) {
        for (int j = 0; j < cols; ++j) {
            cout << matrix[i][j] << " ";
        }
        cout << endl;
    }

    return 0;
}
```
