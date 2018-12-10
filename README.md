/*gfhgjghjhgjhg
hjkhgjkhjkhjk*/
nmbvmbnm
#include <stdio.h>
#include <locale.h>
#include <string.h>
int main(){
    setlocale(LC_ALL, "Portuguese");
    int opcao, opcao2;
    char nomeFesta[30];
    char dataFesta[20];
    char horaFesta[10];
    char localFesta[40];
    char exibirFestas[100];
    char todasFestas[1000];
    char dataEscolhida[20];
    do{
        printf("\n\n");
        printf("\n##############################");
        printf("\n# #");
        printf("\n# iPARTY #");
        printf("\n# #");
        printf("\n# DETECTOR DE FESTAS #");
        printf("\n# #");
        printf("\n# #");
        printf("\n# #");
        printf("\n# #");
        printf("\n# #");
        printf("\n# #");
        printf("\n# Versão alfa 1.0 #");
        printf("\n##############################");
        printf("\n\n\n\n\n");
        printf("\nEscolha o que você quer fazer: ");
        printf("\n <1> Cadastrar festa");
        printf("\n <2> Procurar festa");
        printf("\n <3> Fechar programa \n");
        scanf("%d", &opcao);
        while(opcao < 1 || opcao > 3){
            printf("\n Opção inválida, digite novamente: ");
            scanf("%d", &opcao);
        }
        system("cls");
        switch (opcao){
            case 1:
                system("cls");
                printf("\n##############################");
                printf("\n#                            #");
                printf("\n#     CADASTRO DE FESTA      #");
                printf("\n#                            #");
                printf("\n##############################\n");
                setbuf(stdin,NULL);
                printf("\n Nome da festa: \n");
                gets(nomeFesta);
                printf("\n Data da festa(dd/mm/aa): \n");
                gets(dataFesta);
                printf("\n Horário da festa(hh:mm): \n");
                gets(horaFesta);
                printf("\n Local da festa: \n");
                gets(localFesta);
                FILE *pFesta;
                pFesta = fopen(dataFesta, "a+");
                if(pFesta == NULL){
                    printf("Erro na abertura do arquivo!");
                    return 1;
                }
                FILE *pTodas;
                pTodas = fopen("Todas as festas.txt", "a+");
                fprintf(pFesta,"\n##############################");
                fprintf(pFesta,"\n#                            #");
                fprintf(pFesta,"\n#     FESTAS DISPONÍVEIS     #");
                fprintf(pFesta,"\n#                            #");
                fprintf(pFesta,"\n##############################\n");
                fprintf(pFesta,"\n\n Nome : %s", nomeFesta);
                fprintf(pFesta,"\n\n Horário : %s", horaFesta);
                fprintf(pFesta,"\n\n Local : %s \n", localFesta);
                fclose(pFesta);
                fprintf(pTodas,"\n##############################");
                fprintf(pTodas,"\n#                            #");
                fprintf(pTodas,"\n#     FESTAS DISPONÍVEIS     #");
                fprintf(pTodas,"\n#                            #");
                fprintf(pTodas,"\n##############################\n");
                fprintf(pTodas,"\n\n Nome : %s", nomeFesta);
                fprintf(pTodas,"\n\n Horário : %s", horaFesta);
                fprintf(pTodas,"\n\n Local : %s \n", localFesta);
                fclose(pTodas);
                system("\npause");
                system("cls");
                break;
            case 2:
                printf("\nEscolha como deseja pesquisar: ");
                printf("\n <1> Mostras todas as festas");
                printf("\n <2> Buscar festas por data");
                printf("\n <3> Sair do programa\n");
                scanf("%d", &opcao2);
                switch (opcao2){
                    case 1:
                        system("cls");
                        pTodas = fopen("Todas as festas.txt", "a+");
                        if(pTodas == NULL){
                            printf("Erro na abertura do arquivo!");
                            return 1;
                        }
                        while(fgets(todasFestas, 1000, pTodas) != NULL){
                            printf("%s", todasFestas);
                        }
                        printf("\n\n");
                        system("\npause\n");
                        break;
                    case 2:
                        system("cls");
                        setbuf(stdin, NULL);
                        printf("\n Digite uma data: ");
                        gets (dataEscolhida);
                        pFesta = fopen(dataEscolhida, "a+");
                        if(pFesta == NULL){
                            printf("Erro na abertura do arquivo!");
                            return 1;
                        }
                        while(fgets(exibirFestas, 100, pFesta) != NULL){
                            printf("%s", exibirFestas);
                        }
                        printf("\n\n");
                        system("\npause\n");
                        system("cls");
                        break;
                }
        }
    }while(opcao!=3);
        system("cls");
        printf("\n\n ### FIM DE PROGRAMA ### \n\n ");
}
