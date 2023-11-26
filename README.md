#include <stdio.h>
#include <string.h>

#define MAX_STUDENTS 100

struct Student {
    char name[50];
    int age;
    char address[100];
};

void inputStudent(struct Student *student) {
    printf("Nhập tên sinh viên: ");
    scanf("%s", student->name);
    printf("Nhập tuổi sinh viên: ");
    scanf("%d", &(student->age));
    printf("Nhập địa chỉ sinh viên: ");
    scanf("%s", student->address);
}

void displayStudent(const struct Student *student) {
    printf("Tên sinh viên: %s\n", student->name);
    printf("Tuổi sinh viên: %d\n", student->age);
    printf("Địa chỉ sinh viên: %s\n", student->address);
}

int main() {
    struct Student students[MAX_STUDENTS];
    int numStudents = 0;

    int choice;
    do {
        printf("----- MENU -----\n");
        printf("1. Thêm sinh viên\n");
        printf("2. Hiển thị danh sách sinh viên\n");
        printf("3. Thoát\n");
        printf("Nhập lựa chọn của bạn: ");
        scanf("%d", &choice);

        switch (choice) {
            case 1:
                if (numStudents < MAX_STUDENTS) {
                    printf("Nhập thông tin sinh viên thứ %d:\n", numStudents + 1);
                    inputStudent(&students[numStudents]);
                    numStudents++;
                } else {
                    printf("Danh sách sinh viên đã đầy.\n");
                }
                break;
            case 2:
                if (numStudents > 0) {
                    printf("Danh sách sinh viên:\n");
                    for (int i = 0; i < numStudents; i++) {
                        printf("Sinh viên thứ %d:\n", i + 1);
                        displayStudent(&students[i]);
                        printf("\n");
                    }
                } else {
                    printf("Danh sách sinh viên rỗng.\n");
                }
                break;
            case 3:
                printf("Kết thúc chương trình.\n");
                break;
            default:
                printf("Lựa chọn không hợp lệ.\n");
        }
    } while (choice != 3);

    return 0;
}
