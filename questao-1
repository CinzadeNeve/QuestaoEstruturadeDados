/******************************************************************************

                            Online C Compiler.
                Code, Compile, Run and Debug C program online.
Write your code in this editor and press "Run" button to compile and execute it.

*******************************************************************************/

#include <stdio.h>
#include <stdlib.h>


//Estrutura para representar os Nós de uma lista
struct no{
    int elemento;
    struct no *prox;
};
typedef struct no No;


//Estrutura para representar o cabeçalho de uma lista
struct lista{
    int tamanho;
    struct no *prox;
};
typedef struct lista Lista;


//Função para iniciar uma lista
Lista* InicializarLista(){
    Lista *lista = (Lista*)malloc(sizeof(Lista));
    if(!lista){
        printf("Erro na alocacao dos dados\n");
        exit(1);
    }
    
    lista->tamanho = 0;
    lista->prox = NULL;
    
    return lista;
}

//Função Inserir um elemento na lista
void InserirElemento(Lista* lista, int x){
    No *novoNo = (No*)malloc(sizeof(No));
    if(!novoNo){
        printf("Erro na alocacao dos dados\n");
        exit(1);
    }
    
    novoNo->prox = NULL;
    novoNo->elemento = x;
    
    if(lista->prox == NULL){
        lista->prox = novoNo;
        lista->tamanho++;
    }else{
        No*aux = lista->prox;
        while(aux != NULL){
            if(aux->prox == NULL){
                aux->prox = novoNo;
                break;
            }else{
                aux = aux->prox;
            }
        }
        lista->tamanho++;
    }
    
}


//Função para remover um elemento da lista
No* RemoverElemento(Lista* lista, int x){
    No *aux = lista->prox;
    
    if(aux != NULL){
        if(aux->prox == NULL){
            if(aux->elemento == x){
                lista->prox = NULL;
                lista->tamanho--;
                return(aux);   
            }
        }
        else{
            No *atual = aux->prox;
            No *anterior = aux;
            while(atual != NULL){
                if(atual->elemento == x){
                    lista->tamanho--;
                    anterior->prox = atual->prox;
                    return(atual);
                }else{
                    anterior = atual;
                    atual = atual->prox;
                }
            } 
        }
    }
    
    return NULL;
}


//Função para buscar um elemento na lista
No* BuscarElemento(Lista* lista, int x){
    No* aux = lista->prox;
    while(aux != NULL){
        if(aux->elemento == x){
            return aux;
        }
        aux = aux->prox;
    }
    return NULL;
}

//Função para Zerar uma lista
void ZerarLista(Lista* lista){
    if(lista->prox != NULL){
        No* atual = lista->prox;
        No* proxNo = NULL;
        while(atual != NULL){
            proxNo = atual->prox;
            free(atual);
            atual = proxNo;
        }
    }
}

//Função para exibir todos os elementos da lista
void ExibirLista(Lista* lista){
    No *aux = lista->prox;
    printf("=== LISTA DE TODOS OS ELEMENTOS PRESENTES ===\n");
    while(aux != NULL){
        printf("%i ", aux->elemento);
        aux = aux->prox;
    }
    printf("\n");
}


void screen_init(){
    int operacao;
    int sair = 0;
    int x;
    
    Lista*lista = InicializarLista();

    
    printf("1 - Inserir Elemento\n");
    printf("2 - Remover Elemento\n");
    printf("3 - Buscar Elemento\n");
    printf("4 - Exibir Lista\n");
    printf("5 - Zerar Lista\n");
    printf("6 - Sair\n");
    
    do{
        
        printf("Escolha uma operacao: ");
        scanf(" %i", &operacao);
        switch(operacao){
            case 1:
                printf("Digite o elemento a ser inserido: ");
                scanf(" %i", &x);
                InserirElemento(lista,x);
                break;
            case 2:
                printf("Digite o elemento a ser removido: ");
                scanf(" %i", &x);
                if(RemoverElemento(lista, x) != NULL){
                    printf("Elemento removido com sucesso\n");
                }else{
                    printf("Elemento não encontrado\n");
                }
            break;
                
            case 3:
                printf("Digite o elemento a ser buscado: ");
                scanf(" %i", &x);
                if(BuscarElemento(lista, x) != NULL){
                    printf("O elemento foi encontrado!\n");
                }else{
                    printf("O elemento não foi encontrado na lista :(\n");
                }
            break;
                
            case 4:
                ExibirLista(lista);
            break;
                
            case 5:
                ZerarLista(lista);
            break;
                
            case 6:
                sair = 1;
                printf("Obrigado por utilizar nosso programa\n");
            break;
                
            default:
                printf("Operacao invalida! Digite novamente\n");
            break;
        }
    }while(sair!=1);
}


int main(){
    screen_init();
    return 0;
}
