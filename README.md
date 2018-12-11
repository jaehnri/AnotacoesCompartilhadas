
# AnotacoesCompartilhadas
Este repositório contém um compilado de anotações das aulas de Tópicos em Orientação a Objetos || Um trabalho colaborativo entre alunos do 4° semestre de TI no Colégio Técnico da Unicamp.

## Este repositório foi criado com a intenção de compartilhar conhecimento entre alunos de TI do COTUCA!

### Sobre
  * Feito por:
    - André Satorres;
     - Diego Daniel;
     - Francisco Luiz;
     - Eduardo Porto;
     - Caio Petrucci Rosa;
     - Luca Dillenburg;
     - João Henri;
     - Leonardo Iwashima;
     - Guilherme Rojas;
     - Lucas Romani;
     - Luis Sabença;
     - Nicholas Patapoff;
  * Colégio Técnico de Campinas - Unicamp, 2017;

### Objetivo
  * Auxiliar nos estudos para a última prova do semestre;
  * Compartilhamento de estudos e conhecimento;
  * Integração dos alunos na busca de detalhes;
  * Ampliação da cooperatividade entre os alunos.

# Anotações
## Básico
C++ é uma linguagem de programação multi-paradigma, isto é, permite mais de uma maneira de estruturar código escrito utilizando esta linguagem (sendo eles: programação imperativa, orientada a objetos e genérica). Foi desenvolvida por Bjarne Stroustrup e é baseada na linguagem de programação C, adicionando mais funcionalidades a ela (por isto possui em seu nome ++, que dá a ideia de incremento).

A biblioteca de input/output padrão é  **<iostream\>**  e possui definições para streams importantes, como:
* `std::cout` // stream de saída, o que for empurrado para cá estará visível no terminal do programa
* `std::cin` // stream de entrada, o que for pego daqui poderá ser guardado em uma variável

Exemplo:
```
#include <iostream>
int main() // funcao principal do programa
{
	std::cout << "Hello World!" << std::endl;
	// escreve Hello World! no terminal e pula uma linha (endl)

	int n;
	std::cin >> n;
	// lê um número digitado no terminal e o coloca em n

	return 0; // avisa para o sistema operacional que o programa executou
	          // sem erros
}
```

<br/>
Existem diversas bibliotecas em C++ e cada uma está inserida em um namespace diferente. Por exemplo, as declarações de cout e cin estão dentro do namespace std, e, por isso, deve-se usar std::cout e std::cin para acessá-las. Escrever o namespace não é necessário sempre, por exemplo:

```
#include <iostream>
using namespace std; // não é mais necessario escrever std sempre
int main()
{
	cout << "Hello World!" << endl;

	int n;
	cin >> n;

	return 0;
}
```
Para utilizar uma biblioteca feita feita por você, utilize #include "nomedoarquivo.h". h é a extensão utilizada para arquivos header, onde deverá estar a declaração de uma ou mais classes e seus atributos e métodos. A implementação destes deverá estar em um outro arquivo, normalmente com a extensão cpp. Fazer isto não é necessário, porém, é boa prática. 

**Exemplo de biblioteca**
```
// arquivo biblioteca.h
#ifndef BIBLIOTECA_H
#define BIBLIOTECA_H
// as últimas duas linhas são utilizadas para impedir que a classe seja
// incluída no projeto mais de uma vez

#include <iostream>
// usado na implementação
class Classe {
	private:
		int valor;
	public:
		Classe(int); // construtor
		~Classe(); // destrutor
		int getValor() { return this->valor; };
		void setValor(int v) { this->valor = v; };
		//   estas funções declaradas dentro da definição da classe
		// serão inline, isto é, o compilador irá colocar o código
		// delas diretamente no seu programa, sem fazer com que
		// a linha de execução pule até a implementação da função
		//   apenas funções pequenas e que podem ser mostradas ao
		// usuário da classe devem ser implementadas aqui
		void printar(char*);
};

#endif


// arquivo biblioteca.cpp
#include "biblioteca.h"
Classe::Classe(int v) {
	this->valor = v; // em C++, this é um ponteiro
}

Classe::~Classe() {
	//   neste caso, nada precisa ser colocado aqui.
	//   deve-se implementar destrutor quando sua classe
	// aloque memória dinamicamente (usando new ou malloc) e/ou
	// quando algum atributo da classe aloque memória dinamicamente
}

void Classe::printar(char* str) {
	std::cout << str << std::endl;
}


// arquivo main.cpp
#include "biblioteca.h"
int main() {
	//   nao foi definido um namespace para aquilo declarado dentro da
	// biblioteca biblioteca.h, portanto, não é necessário escrever
	// using namespace nome;
	Classe c(10); // chama o único construtor declarado
	c.printar("Hello World!");
	
	return 0;
}
```

<br/>
Em C++, não há uma superclasse da qual todas as outras herdam, como Java.

<br/>
