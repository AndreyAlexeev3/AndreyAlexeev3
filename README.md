#include <iostream>
#include <fstream>
#include <cstring>
#include <cstdio>
#include <stdio.h>
#include <string>



template <typename Type>
Type Sort(Type *pt, int n);

using namespace std;

int main() {

	double a;
	int count = 0;

	

	ifstream fin;
	fin.open("input.txt");
	
	while (fin >> a)//подсчитываем количество чисел в файле
		count++;


	fin.clear();
	fin.seekg(0, ios_base::beg);


	int *arr = new int[count];
	double *ar_double_1 = new double[count];
	char *ar_char_2 = new char[count];
	
	if (fin) {
		for (int i = 0; i != count; i++) {
			fin >> arr[i];
			ar_double_1[i] = (double)arr[i];
			ar_char_2[i] = (char)arr[i];
		}
	}
	fin.close();


	cout << "Sort for int " << endl;
	Sort(arr, count);
	cout  << endl;
	cout << "Sort for double " << endl;
	Sort(ar_double_1, count);
	cout << endl;
	cout << "Sort for char " << endl;
	Sort(ar_char_2, count);
	cout << endl;
	ofstream fout("output.txt");
	for (int i = 0; i != count; i++) {
		fout << arr[i];
		fout << " ";
	}
	
	fout.close();
	system("pause");
	return 0;
}

template <typename Type>
Type Sort(Type* pt, int n)
{
	for (int startIndex = 0; startIndex < n - 1; ++startIndex)
	{
		int smallestIndex = startIndex;
		for (int currentIndex = startIndex + 1; currentIndex < n; ++currentIndex)
		{
			if (pt[currentIndex] < pt[smallestIndex])
				smallestIndex = currentIndex;
		}

		swap(pt[startIndex], pt[smallestIndex]);
	}
	for (int index = 0; index < n; ++index)
		cout << pt[index] << ' ';

	return(0);

}
