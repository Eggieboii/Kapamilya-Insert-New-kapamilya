void InsertKapamilya(int position)
{
	if (position <= 0)
	{
		cout << "Invalid Position!! " << endl;
		system("pause");
		return;
	}

	kapamilya* newKapamilya = new kapamilya;
	cout << "Enter Name: ";
	cin >> newKapamilya->name;
	cout << "Enter Age: ";
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
	int count = 1;

	while (current != NULL && count < position - 1) {
		current = current->next;
		count++;
	}

	if (current == NULL)
	{
		cout << "Position is out of bounds. No Kapamilya inserted." << endl;
		delete newKapamilya;
	}
	else
	{
		newKapamilya->next = current->next;
		current->next = newKapamilya;
		cout << "Kapamilya inserted at position " << position << "!" << endl;
	}

	system("pause");
	system("cls");
}
