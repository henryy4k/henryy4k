#include <iostream>
#include <cstdlib>
#include <ctime>

using namespace std;

const int TAMANHO = 6;
const int BOMBAS = 3;
const int JOGADAS_MAX = 5;

void inicializaCampo(char campo[TAMANHO][TAMANHO]) {
    for (int i = 0; i < TAMANHO; i++) {
        for (int j = 0; j < TAMANHO; j++) {
            campo[i][j] = '1';
        }
    }
}

void posicionaBombas(char campo[TAMANHO][TAMANHO]) {
    srand(time(NULL));
    int i, j;
    for (int k = 0; k < BOMBAS; k++) {
        do {
            i = rand() % TAMANHO;
            j = rand() % TAMANHO;
        } while (campo[i][j] == 'X');
        campo[i][j] = 'X';
    }
}

void mostraCampo(char campo[TAMANHO][TAMANHO]) {
    // Implemente a função para mostrar o campo de forma clara e organizada
}

int main() {
    char campo[TAMANHO][TAMANHO];
    int linha, coluna, jogadas = 0;

    inicializaCampo(campo);
    posicionaBombas(campo);

    while (jogadas < JOGADAS_MAX) {
        mostraCampo(campo);
        cout << "Digite a linha e coluna (1-" << TAMANHO << "): ";
        cin >> linha >> coluna;

        // Validar entrada e verificar se a posição é válida

        if (campo[linha - 1][coluna - 1] == 'X') {
            cout << "Você perdeu! A bomba estava em (" << linha << ", " << coluna << ")" << endl;
            mostraCampo(campo);
            break;
        } else {
            campo[linha - 1][coluna - 1] = 'O';
            jogadas++;
        }
    }

    if (jogadas == JOGADAS_MAX) {
        cout << "Parabéns! Você venceu!" << endl;
    }

    return 0;
}
