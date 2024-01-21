# MENU
#include <iostream>

using namespace std;

int Menu()
{
    int x;
    cout<<endl;
    cout<<"1. Dodaj element tablicy"<<endl;
    cout<<"2. Wstaw element tablicy"<<endl;
    cout<<"3. Usun element tablicy"<<endl;
    cout<<"4. Wyświetl elementy tablicy"<<endl;
    cout<<"7. Wyjscie z programu"<<endl;
    cin>>x;
    cout<<endl;
    return x;
}

int main()
{
    int m;
    int *p = NULL;
    int n = 0;
    while(true)
    {
        m = Menu();
        switch(m)
        {
        case 7:
            {
                return 0;
            }
        case 1:
            {
                int * tmp = NULL;
                tmp = new int[n+1];
                if(p != NULL)
                {
                    for(int i=0;i<n;i++)
                    {
                        tmp[i] = p[i];
                    }
                    delete[] p;
                }
                cout<<"Podaj wartosc elementu tablicy: ";
                cin>>tmp[n];
                p = tmp;
                n++;
                break;
            }
        case 2:
            {
                int index, wartosc;
                cout << "Podaj wartosc: ";
                cin >> wartosc;
                cout << endl;
                cout << "Podaj indeks: ";
                cin >> index;
                cout << endl;
                if (index < 0 || index > n)
                {
                    cout << "Błedny indeks" << endl;
                }
                int * tmp = NULL;
                tmp = new int[n + 1];
                for (int i = 0; i < index; i++)
                {
                    tmp[i] = p[i];
                }
                tmp[index] = wartosc;
                for (int i = index + 1; i < n; i++)
                {
                    tmp[i] = p[i - 1];
                }
                delete[] p;
                p = tmp;
                n++;
                break;
            }
        case 3:
            {
                int index;
                cout << "Podaj indeks: ";
                cin >> index;
                cout << endl;
                int * tmp = NULL;
                tmp = new int[n - 1];
                int a = 0;
                if (p != NULL)
                {
                    for (int i = 0; i < n; i++)
                    {
                        if (i != index)
                        {
                            tmp[a] = p[i];
                            a++;
                        }
                    }
                }
                for (int i = 0; i < n; i++)
                {
                    p[i] = tmp[i];
                }
                delete[] tmp;
                n--;
                break;
            }
        case 4:
            {
                cout<<"Zawartosc tablicy:"<<endl;
                for(int i=0;i<n;i++)
                {
                    cout<<p[i]<<", ";
                }
                cout<<endl;
                break;
            }
        default:
            {
                cout<<"Nieprawidlowa opcja"<<endl;
            }

        }
    }

    return 0;
}
