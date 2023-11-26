#include <iostream>
using namespace std;

// Định nghĩa cấu trúc sinh viên
struct Student {
    string name;
    int age;
    string address;
};

// Hàm nhập thông tin sinh viên
void inputStudent(Student& student) {
    cout << "Nhập tên sinh viên: ";
    getline(cin >> ws, student.name); // Sử dụng getline để nhập chuỗi có khoảng trắng
    cout << "Nhập tuổi sinh viên: ";
    cin >> student.age;
    cout << "Nhập địa chỉ sinh viên: ";
    getline(cin >> ws, student.address);
}

// Hàm hiển thị thông tin sinh viên
void displayStudent(const Student& student) {
    cout << "Tên sinh viên: " << student.name << endl;
    cout << "Tuổi sinh viên: " << student.age << endl;
    cout << "Địa chỉ sinh viên: " << student.address << endl;
}

int main() {
    const int MAX_STUDENTS = 100;
    Student students[MAX_STUDENTS];
    int numStudents = 0;

    char choice;
    do {
        cout << "----- MENU -----" << endl;
        cout << "1. Thêm sinh viên" << endl;
        cout << "2. Hiển thị danh sách sinh viên" << endl;
        cout << "3. Thoát" << endl;
        cout << "Nhập lựa chọn của bạn: ";
        cin >> choice;

        switch (choice) {
            case '1':
                if (numStudents < MAX_STUDENTS) {
                    cout << "Nhập thông tin sinh viên thứ " << numStudents + 1 << ":" << endl;
                    inputStudent(students[numStudents]);
                    numStudents++;
                } else {
                    cout << "Danh sách sinh viên đã đầy." << endl;
                }
                break;
            case '2':
                if (numStudents > 0) {
                    cout << "Danh sách sinh viên:" << endl;
                    for (int i = 0; i < numStudents; i++) {
                        cout << "Sinh viên thứ " << i + 1 << ":" << endl;
                        displayStudent(students[i]);
                        cout << endl;
                    }
                } else {
                    cout << "Danh sách sinh viên rỗng." << endl;
                }
                break;
            case '3':
                cout << "Kết thúc chương trình." << endl;
                break;
            default:
                cout << "Lựa chọn không hợp lệ." << endl;
        }
    } while (choice != '3');

    return 0;
}
