#include<stdlib.h>
#include<stdio.h>
#include<string.h>
#include<locale.h>
#include<math.h>
/*int convertdec(char numero[],int tam,int basen) {
	int decimal[50];
	int soma=0;
	char aux[30];
	for (int i = 0; numero[i] != '.'; i++) {
		aux[i] = numero[i];
	}
	//int inteiro = atoi(aux[1]);
	if (basen == 2) {
		for (int i = 0; ; i++) {
			if (aux[i]=='0' || aux[i]=='1') {
				if(aux[i]=='0'){
					soma += 0;
				}else {
					soma += pow(2,i);
				}
			}else {
				break;
			}
		}
	}
	return soma;
}
float frac(char numero[],int basen,int tam) {
	int i;
	float soma=0;
	for (i = 0; numero[i] != '.'; i++);
	i++;
	for (int j=1; i < tam;i++) {
		if (numero[i]=='0') {
			soma += 0;
			j++;
		}
		if(numero[i]=='1'){
			soma += pow(2,-j);
		}
	}
	return soma;
}*/

void binto(char *numero_somente, int base2,char *numero) {
	int a;
	long int reminder,octal,j;
	float soma=0;
	int *aux;
	printf("entrei\n");
	if (base2 == 8) {
		int cont = 0;
		int i;
		printf("entrei uhu\n");
		for (int i = 0; numero[i] != ' '; i++) {
		    printf("%d",i);
			cont++;
			printf("%d",cont);
		}
		aux/*[cont];*/ = (int*)malloc(sizeof(int) * cont); //mesma coisa que "int aux[cont];"*/
		for (i = 0; i < cont; i++) {
			aux[i] = numero_somente[i];
		}
		for (i = 0; i < cont; i++) {
		    printf("entrei uhuuu");
		    while(numero_somente[i]!=0){
			    reminder=numero_somente[i]%10;
			    printf("%d:",reminder);
			    octal=octal+reminder*j;
			    printf("%d:",octal);
			    j=j*2;
			    printf("%d:",j);
			    numero_somente[i]=numero_somente[i]/10;
			    printf("%s:",numero_somente[i]);
		    }
		}
	}
	if (base2 == 10) {
		a = 0;		
	}
	if (base2 == 16) {
		a = 0;
	}
	free (aux);
}

void decide(char *numero) {

	char numero_somente[50];
	int i;
	int base, base2;//base  a converter;

	for (i = 0; numero[i] != ' '; i++) {
		numero_somente[i] = numero[i];
	}
	i++;
	if (numero[i] == '2') {
		for (int cont=i++; numero[cont] != ' '; cont++) {
		}
		i++;
		if (numero[i] == '8') {
			base2 = 8;
			printf("a\n");
			binto(numero_somente, base2,numero);
		}
		if (numero[i + 1] == '0') {
			base2 = 10;
		}
		if (numero[i + 1] == '6') {
			base2 = 16;
		}
	}
	if (numero[i] == '8') {
		for (; numero[i] != ' '; i++) {
		}
		i++;
		if (numero[i] == '2') {
			base2 = 2;
			//converteb(numero, 8);
		}
		if (numero[i + 1] == '0') {
			base2 = 10;
		}
		if (numero[i + 1] == '6') {
			base2 = 16;
		}
	}
	if (numero[i + 1] == '0' && numero[i + 2] != ' ') {
		for (; numero[i] != ' '; i++) {
		}
		i++;
		if (numero[i] == '8') {
			base2 = 8;
			//converteb(numero, 8);
		}
		if (numero[i] == '2') {
			base2 = 2;
		}
		if (numero[i + 1] == '6') {
			base2 = 16;
		}
	}
	if (numero[i + 1] == '6' && numero[i + 2] != ' ') {
		for (; numero[i] != ' '; i++) {
		}
		i++;
		if (numero[i] == '8') {
			base2 = 8;
			//converteb(numero, 8);
		}
		if (numero[i + 1] == '0') {
			base2 = 10;
		}
		if (numero[i] == '2') {
			base2 = 2;
		}
	}
}

int main() {
	char numero[50];
	int basen, baset, tam;
	float c, f;
	printf("Programa de coversão de Bases\n");
	printf("Funcionamento: \n");
	printf("(sinal)(numero)\"ESPAÇO\"(base do numero)\"ESPAÇO\"(base a converter): \n");
	fgets(numero, 50, stdin);
	decide(numero);
	//printf("%s\n",numero );
	/*tam = strlen(numero);
	c=convertdec(numero,tam,basen);
	f=frac(numero,tam,basen);
	printf("%i.%f", c, f);
	fputs(numero, stdout);
	//printf(" base: %i base t:%i\n",basen,baset);
	*/
	//system("pause");
	return 0;
}
