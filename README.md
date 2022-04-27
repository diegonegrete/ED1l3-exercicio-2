# ED1l3-exercicio-2
#include <iostream>
using namespace std;

struct Lista
{
	int prontuario;
	string nome;
	double salario;
	struct Lista *prox;
};

Lista* init()
{
	return NULL;
}

int isEmpty(Lista* lista)
{
	return (lista==NULL);
}

Lista* insert(Lista* lista, int i, string a, double b)
{
	Lista* novo = new Lista();
	novo->prontuario = i;
	novo->nome = a;
	novo->salario = b;
	novo->prox = lista;
	return novo;
}

void print(Lista* lista)
{
	Lista* aux;
	aux = lista;
	double totalsal = 0;
	while(aux != NULL)
	{
		if(aux->prontuario != NULL)
		{
			cout << "Prontuario: " << aux->prontuario<< "    Nome: " << aux->nome<< "    Salario: R$" << aux->salario << endl;
			totalsal = totalsal + aux->salario;
		}
		aux = aux->prox;
	}
	cout << "O total de todos os salarios e de R$" << totalsal << endl;
	cout << "----------------" << endl;
}

Lista* find(Lista* lista, int i)
{
	Lista* aux;
	aux = lista;
	while (aux != NULL && aux->prontuario != i)
	{
		aux = aux->prox;
	}
	return aux;
}

Lista* remove(Lista* lista, int i)
{
	Lista *aux;
	Lista *ant = NULL;
	
	aux = lista;
	while (aux != NULL && aux->prontuario != i)
	{
		ant = aux;
		aux = aux->prox;
	}
	
	if (aux == NULL)
	{
		return lista;
	}
	
	if (ant == NULL) 
	{
		aux->prontuario = NULL;
	}
	else 
	{
		ant->prox = aux->prox;
	}
	
	return lista;
}

void freeLista(Lista* lista)
{
    Lista *aux;
    aux = lista;
    while (aux != NULL)
	{
		Lista *ant = aux->prox;
		free(aux);
		aux = ant;
	}
}

int main(int argc, char** argv)
{
	Lista *minhaLista;
	minhaLista = init();
	int op, num;
	for(int j = 0 ; j <=0; )
	{
		cout << "0 - SAIR" << endl;
		cout << "1 - INCLUIR" << endl;
		cout << "2 - EXCLUIR" << endl;
		cout << "3 - PESQUISAR" << endl;
		cout << "4 - LISTAR" << endl;
		cout << "Digite o numero da opcao escolhida"<< endl;
		cin >> op;
		cout << endl;
		
		switch(op){
			case 0:{
				cout << endl << endl << "Programa finalizado";
				j++;
				break;
			}
			case 1:{
				system("cls");
				for(int l = 0 ; l <=0;)
				{
					cout << "INSERIR"<< endl << endl;
					cout << "Digite o numero do prontuario"<< endl;
					cin >> num;
				
					Lista *procurado = find(minhaLista, num);
					if (procurado != NULL)
					{
						for(int p = 0; p <=0;)
						{
							cout << "Prontuario ja cadastrado!!! " << endl;
					   	    cout << "Digite 1 para continuar e cadastrar outro funcionario." << endl;	
					   	    cout << "Digite 2 para encerrar a funcao de cadastros" << endl;
					   	    int t;
					   	    cin >> t;
							if(t == 2){
								p++;
								l++;
							}else if(t==1){
								p++;
							}
							else
							{
								cout<< "Digite uma opcao valida!!!"<< endl;
							}
						}
				   	    
					}
					else
					{
							cout << "Digite o numero do prontuario"<< endl;
							string nomes;
							cin >> nomes;
							cout << "Digite o salario"<< endl;
							double sal;
							cin >> sal;
							minhaLista = insert(minhaLista, num, nomes, sal);
							cout << endl<< endl;
							l++;
					}
				}
				break;
			}
			case 2:{
				system("cls");
				cout << "EXCLUIR"<< endl << endl;
				cout << "Digite o numero do prontuario"<< endl;
				cin >> num;
				minhaLista = remove(minhaLista, num);
				cout << endl<< endl;
				break;
			}
			case 3:{
				system("cls");
				cout << "PESQUISAR"<< endl << endl;
				cout << "Digite o numero do prontuario"<< endl;
				cin >> num;
				Lista *procurado = find(minhaLista, num);
				if (procurado != NULL)
				{
			   	    cout << "Prontuario: " << procurado->prontuario << "    Nome: " << procurado->nome<< "    Salario: R$" << procurado->salario << endl;	
				}
				else
				{
					cout << "Prontuario nao encontrado!" << endl;
				}
				cout << endl<< endl;
				break;
			}
			case 4:
				{
					system("cls");
					cout << "LISTAR"<< endl << endl;
					print(minhaLista);
					cout << endl<< endl;
				}
			}
		
		
	}	
	return 0;
}
