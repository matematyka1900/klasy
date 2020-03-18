# klasy
klasy dla Lajkonika
#include <iostream>
#include <string>


using namespace std;


class Biblioteka
{	
int ewidencja = 4;

public:
	string rodzaj[4] = { "Piekna", "Techniczna",
							 "Naukowa", "Filozoficzna" };
	int get_ewidencja() { return ewidencja; }
	void set_ewidencja(int);
	void get_rodzaj();

	
	
	
};
class Ksiazka
{
public:	
	Ksiazka()
	{
		nastepna = 0;
	}
	int numer;
	string tytul;
	string autor;
 
	Ksiazka* nastepna;
	

};

class Bibliotekarka 
{
	int pesel = 2134454323;
public:
	Bibliotekarka()
	{
		pierwsza = 0;
	}
	

	Ksiazka* pierwsza;
	int get_pesel() { return pesel; }
	void zapisz_w_bazie(int numer,string tytul, string autor)
	{
		Ksiazka* nowa = new Ksiazka;
		nowa->numer = numer;
		nowa->tytul = tytul;
		nowa->autor = autor;
		if (pierwsza == 0)
		{
			pierwsza = nowa;
		}
		else
		{
			Ksiazka* temp = pierwsza;
			while (temp->nastepna)
			{
				temp = temp->nastepna;
			}
			temp->nastepna = nowa;
			nowa->nastepna = NULL;
		}


	}
	
	void wyswietl_liste()
	{
		Ksiazka* temp = pierwsza;
		while (temp)
		{
			cout << "autor: " << temp->autor <<"\t"<< "tytul: " << temp->tytul << endl;
			temp = temp->nastepna;
		}
	}
	void usun_osobe(int nr);

};


class Czytelnik
{
	string imie;
	string nazwisko;
	int pesel;
	
public:
	void set(const int& psl, const string& im, const string& nazw);
	void set();
	void pokaz();
	//void ileMaPo�yczonych();
	//string napiszPonaglenie();

};
void bibl(Biblioteka b2[], int k);
void bibl(Bibliotekarka b2[], int k);
