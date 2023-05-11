# iagoMdv03test
#include <iostream>
#include <string>
#include <vector>
#include <ctime>
#include <cstdlib>

using namespace std;

vector<string> palavras {"abacaxi", "banana", "morango", "laranja", "uva"}; // Lista de palavras possíveis
const int MAX_ERROS = 6; // Número máximo de erros permitidos
vector<string> mensagens {
    "\n____\n|         |\n|         O\n|   \n|        \n|        \n|_\n Erro #1: letra incorreta.",
    "\n____\n|         |\n|         O\n|         |\n| \n|        \n|_\n Erro #2: letra incorreta.",
    "\n____\n|         |\n|         O\n|        /|\n|        \n|        \n|_\n Erro #3: letra incorreta.",
    "\n____\n|         |\n|         O\n|        /|\\\n|        \n|        \n|_\n Erro #4: letra incorreta.",
    "\n____\n|         |\n|         O\n|        /|\\\n|        /\n|_\n Erro #5: letra incorreta.",
    "\n____\n|         |\n|         O\n|        /|\\\n|        / \\\n|_\n Erro #6: letra incorreta.",
}; // Lista de mensagens para cada erro

string escolherPalavra() {
    srand(time(nullptr));
    return palavras[rand() % palavras.size()];
}

int main() {
    string palavra = escolherPalavra();
    string palavraAdivinhada(palavra.size(), '-');
    int erros = 0;

    while (erros < MAX_ERROS && palavraAdivinhada != palavra) {
        cout << "Palavra: " << palavraAdivinhada << endl;
        cout << "Digite uma letra: ";
        char letra;
        cin >> letra;

        bool acertou = false;
        for (int i = 0; i < palavra.size(); i++) {
            if (palavra[i] == letra) {
                palavraAdivinhada[i] = letra;
                acertou = true;
            }
        }

        if (!acertou) {
            cout << mensagens[erros] << endl;
            erros++;
        }
    }

    if (erros < MAX_ERROS) {
        cout << "Parabéns! Você acertou a palavra: " << palavra << endl;
    } else {
        cout << "Você perdeu! A palavra era: " << palavra << endl;
        cout << "\n____\n|         |\n|         O\n|        /|\\\n|        / \\\n|_\n" << endl;
    }

    return 0;
}
