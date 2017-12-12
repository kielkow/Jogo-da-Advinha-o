# Jogo-da-Advinhação
Um simples jogo desenvolvido em C, mas que utiliza de muitos comandos básicos utilizados para a introdução ao aprendizado da linguagem.

#include <stdio.h>
#include <stdlib.h>
#include <time.h>

int main(){
  
  printf("*******************************\n");
  printf("Bem vindo ao Jogo da Advinhação\n");
  printf("*******************************\n");
  
  int nivel;
  int totaldetentativas;
  
  printf("\nQual o nível de dificuldade que gostaria de jogar?\n");
  printf("\n(1) Fácil ; (2) Médio ; (3) Difícil\n");
  printf("Escolha: ");
  scanf("%d", &nivel);
  
  switch(nivel){
    case 1:
      totaldetentativas = 20;
      break;
    
    case 2:
      totaldetentativas = 10;
      break;
    
    case 3:
      totaldetentativas = 5;
      break;
    
    default:
      totaldetentativas = 5;
      break;
  }
  
  printf("\nLembre-se! O Número Secreto está entre 0 e 99!\n");
  
  int i = 1;
  int chute;
  double pontos = 1000;
  double pontos_perdidos;
  int acertou = 0;
  
  int segundos = time(0);
  srand(segundos);
  
  int numerogrande = rand();
  int numerosecreto = numerogrande % 100;
  
  
  for(i = 1; i <= totaldetentativas; i++){
  
  printf("\nQual é seu %d° chute?\n", i);
  scanf("%d", &chute);
  
  if(chute < 0){
    printf("\nNumero inválido\n");
    i--;
    continue;
  }
  
  printf("\nSeu %d° chute foi o numero %d!\n", i, chute);
  
  acertou = chute == numerosecreto;
  int maior = chute > numerosecreto;
  
  if (acertou){
    printf("Parabéns, você acertou! O Número Secreto é %d !\n", numerosecreto);
    printf("Seu numero de tentativas foi %d", i);
    break;
  }
  else if (maior){
      printf("Numero chutado é maior que o Número Secreto\n");
    }
  else{
      printf("Numero chutado é menor que o Número Secreto\n");
    }
   printf("\nSeu número de tentativas foi %d\n", i);
   
  pontos_perdidos = abs(chute - numerosecreto)/(double)2;
  pontos = pontos - pontos_perdidos;
  }
  
  if(!acertou){
    printf("\nNão desista, tente novamente !\n"); 
  }
  else{
    printf("\nSua pontuação final foi: %.2f\n", pontos);
    printf("\nFim do Jogo\n");
  }
  
  
  
  
  
 return 0; 
}
