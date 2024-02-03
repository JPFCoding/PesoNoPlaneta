#include <stdio.h>
#include <locale.h>

int main()
{
    float n,p,x=0;
    int z,s;
    char nome[100],linha[100],planeta[100];
    FILE*f;
    setlocale(LC_ALL, "Portuguese");
    do{
        printf("Seja bem vinda/o, vamos calcular como você pesaria se vivesse em um planeta que não a terra?\nDigite seu peso:\n\t");
        scanf("%f",&n);
        printf("\nQual o seu nome?\nDigite com hífen ou wonderline ao invés de espaço, por favor.\n\t");
        scanf("%s",nome);
        printf("\nEm qual planeta você gostaria de saber quanto pesa?\nAperte 1 para Mercúrio:\nAperte 2 para Vênus:\nAperte 3 para Marte:\nAperte 4 para Júpiter:\nAperte 5 para Saturno:\n\t");
        scanf("%f",&p);
            if(p==1){
                x=n*(0.37);
                printf("\nVocê escolheu Mercúrio, seu peso relativo é: %f",x);
                strcpy(planeta,"Mercúrio");
            }
            if(p==2){
                x=n*(0.88);
                printf("\nVocê escolheu Vênus, seu peso relativo é: %f",x);
                strcpy(planeta,"Vênus");
            }
            if(p==3){
                x=n*(0.38);
                printf("\nVocê escolheu Marte, seu peso relativo é: %f",x);
                strcpy(planeta,"Marte");
            }
            if(p==4){
                x=n*(2.64);
                printf("\nVocê escolheu Júpiter, seu peso relativo é: %f",x);
                strcpy(planeta,"Júpiter");
                }
            if(p==5){
                x=n*(1.15);
                printf("\nVocê escolheu Saturno, seu peso relativo é: %f",x);
                strcpy(planeta,"Saturno");
            }
        f=fopen("Peso.txt","a");
        fprintf(f,"Nome %s\n",nome );
        fprintf(f,"Planeta escolhido:%s\n",planeta);
        fprintf(f,"Peso relativo no planeta:%f\n",x);
        fprintf(f,"\n\n");
        fclose(f);
        printf("\nGostaria de saber quais pessoas fizeram o teste e quais os seus pesos relativos?\nDigite 2.\nSe não, digite qualquer número.\n\t");
        scanf("%d",&s);
            if(s==2){
                f=fopen("peso.txt","r");
                if(f==NULL){
                    printf("\nArquivo vazio");
                    return(1);
                }
                while(fgets(linha,sizeof(linha),f)!=NULL){
                    printf("%s",linha);
                }
                fclose(f);
                }
            else{
                printf("\nComando inválido");
            }

        printf("\nAperte qualquer número para repetir o processo:\n\nAperte 0 para sair:\n\t");
        scanf("%d",&z);
    }while(z!=0);

return(0);
}
