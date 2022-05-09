#include <iostream>
#include <string>
#include <fstream>
#include <cstdlib>

using namespace std;

int main() {
    string answer, username, password, line;
    fstream data;
    bool success = false;
    
    cout << "New User? (yes or no) : ";
    cin >> answer;
    if(answer == "yes") {
        while(!success) {
            cout << "create a login\n";
            cout << "enter username\n";
            cin >> username;
        
            data.open("logins.txt", ios::in);
        
            bool user_exists = false;
            while(!data.eof()) {
                data >> line;
                if(line == username) {
                    user_exists = true;
                }
            }
            if(user_exists) {
                cout << "username taken, try again\n";
            } else {
                success = true;
            }
            data.close();
        }
        
        bool success = false;
        while(!success) {
            cout << "enter password\n";
            cin >> password;
            int test1, test2;
            bool number_pres = false, upper_pres = false;
        
            for(int i = 0; i < password.length(); i++) {
                test1 = isdigit(password[i]);
                test2 = isupper(password[i]);
                if(test1 != 0) {
                    number_pres = true;
                } else if(test2 != 0) {
                    upper_pres = true;
                }
            }
        
            if(!number_pres || !upper_pres) {
                cout << "password must have an upper case letter and a number. \n";
            } else {
                success = true;
            }
        }
        
        data.open("logins.txt", ios::app);
        
        data << username << "\n";
        data << password << "\n\n";
        
        data.close();
    } else if(answer == "no") {
        bool found_user = false;
        
        while(!found_user) {
            cout << "enter username\n";
            cin >> username;
            data.open("logins.txt", ios::in);
            while(!data.eof()) {
                data >> line;
                if(line == username) {
                    found_user = true;
                    break;
                }
            }
            if(!found_user) {
                cout << "username does not exist, try again\n";
                data.close();
            }
        }
        bool password_correct = false;
        int attempt = 0;
        data>>line;
        while(!password_correct && attempt < 5) {
            cout << "enter password\n";
            cin >> password;
            if(line == password) {
                cout << "Welcome back, " << username << "!\n";
                password_correct = true;
            } else if(attempt == 4) {
                attempt++;
                cout << "too many failed attempts, locked out... \n";
            } else {
                cout << "password incorrect, try again\n";
                attempt++;
            }
        }
        data.close();
    } else {
        cout << "invalid input\n";
    }
    data.close();
    
    return 0;
}
