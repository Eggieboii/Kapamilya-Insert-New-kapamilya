# Kapamilya-Insert-New-kapamilya


// Kapamilya.cpp : This file contains the 'main' function. Program execution begins and ends there.
//

#include <iostream>
using namespace std;

struct kapamilya {
	char name[20];
	int age;
	kapamilya* next;
};
kapamilya* lolo = NULL;

void createKapamilya() {
	system("cls");
	lolo = new kapamilya;
	cout << "Enter name: ";
	cin >> lolo->name;
	cout << "Enter age: ";
	cin >> lolo->age;
	lolo->next = NULL;
	system("cls");
}

void displayKapamilya()
{
	kapamilya* current = lolo;
	if (current == NULL)
	{
		cout << "No Kapamilya to display!" << endl;
		system("pause");
		return;
	}
	while (current != NULL)
	{
		cout << "Kapamilya Name: " << current->name << endl
			<< "Kapamilya Age: " << current->age << endl;
		current = current->next;
	}
	system("pause");
}

void addNewKapamilya() {
	if (lolo == NULL) {
		cout << "Wala pang ancestor. Please create one first." << endl;
		system("pause");
		return;
	}

	kapamilya* NewBaby = new kapamilya;
	cout << "Enter name: ";
	cin >> NewBaby->name;
	cout << "Enter age: ";
	cin >> NewBaby->age;
	NewBaby->next = NULL;

	kapamilya* current = lolo;
	while (current->next != NULL) {
		current = current->next;
	}
	current->next = NewBaby;

	system("cls");
}

void removeHeadKapamilya()
{
	if (lolo == NULL) {
		cout << "No Kapamilya to remove!" << endl;
		system("pause");
		return;
	}
	else
	{
		kapamilya* temp = lolo;
		lolo = lolo->next;
		delete temp;
		cout << "Head of the Kapamilya removed!" << endl;
	}

	system("pause");
	system("cls");
}

void removeNthKapamilya() {
	if (lolo == NULL) {
		cout << "No Kapamilya to remove!" << endl;
		system("pause");
		return;
	}

	int n;
	cout << "Enter the position of the Kapamilya to remove: ";
	cin >> n;

	if (n <= 0) {
		cout << "Invalid position!" << endl;
		system("pause");
		return;
	}

	if (n == 1) {
		removeHeadKapamilya();
		return;
	}

	kapamilya* current = lolo;
	kapamilya* previous = NULL;
	int count = 1;

	while (current != NULL && count < n) {
		previous = current;
		current = current->next;
		count++;
	}

	if (current == NULL) {
		cout << "Position is out of bounds.  No Kapamilya removed." << endl;
	}
	else {
		previous->next = current->next;
		delete current;
		cout << "Kapamilya removed!" << endl;
	}
	system("pause");
}

void addNewKAncestor() {
	if (lolo == NULL) {
		cout << "No Kapamilya to add ancestor!" << endl;
		system("pause");
		return;
	}

	kapamilya* newAncestor = new kapamilya;
	cout << "Enter name: ";
	cin >> newAncestor->name;
	cout << "Enter age: ";
	cin >> newAncestor->age;
	newAncestor->next = lolo; // New ancestor points to the current head
	lolo = newAncestor; // New ancestor becomes the new head

	system("pause");
	system("cls");
}

void InsertKapamilya(int position)
{
	if (position <= 0)
	{
		cout << "Invalid Position!! " << endl;
		system("pause");
	}

	kapamilya* newKapamilya = new kapamilya;
	cout << "Enter Name: " << endl;
	cin >> newKapamilya->name;
	cout << "Enter Age: " << endl;
	cin >> newKapamilya->age;
	newKapamilya->next = NULL;

	if (position == 1)
	{
		newKapamilya->next = lolo;
		lolo = newKapamilya;
		system("cls");
		return;
	}
	kapamilya* current = lolo;
	kapamilya* previous = NULL;
	int count = 1;

	while (current != NULL && count < position) {
		previous = current;
		current = current->next;
		count++;
	}

	if (current == NULL && count < position) {
		cout << "Position is out of bounds. No Kapamilya inserted." << endl;
		delete newKapamilya;
	}
	else {
		newKapamilya->next = current;
		previous->next = newKapamilya;
		cout << "Kapamilya inserted at position " << position << "!" << endl;
	}

	system("pause");
	system("cls");
}

int main() {
	int choice;
	do {
		cout << "1. Create Kapamilya" << endl;
		cout << "2. Add new Kapamilya" << endl;
		cout << "3. Display Kapamilya" << endl;
		cout << "4. Remove head Kapamilya" << endl;
		cout << "5. Remove nth Kapamilya" << endl;
		cout << "6. Add new Ancestor" << endl;
		cout << "7. Insert Kapamilya " << endl;
		cout << "8. Exit" << endl;
		cout << "Enter your choice: ";
		cin >> choice;

		if (choice == 1) {
			createKapamilya();
		}
		else if (choice == 2) {
			addNewKapamilya();
		}
		else if (choice == 3) {
			displayKapamilya();
		}
		else if (choice == 4) {
			removeHeadKapamilya();
		}
		else if (choice == 5) {
			removeNthKapamilya();
		}
		else if (choice == 6) {
			addNewKAncestor();
		}
		else if(choice == 7)
		{
			int position;
			cout << "Enter Your position to insert in Kapamilya: " << endl;
			cin >> position;
		}
	} while (choice != 8);

	return 0;
}

