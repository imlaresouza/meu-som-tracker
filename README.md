
---

## 💻 Código-Fonte (meusomtracker.c)

```c
#include <stdio.h>
#include <string.h>

#define DIAS 7
#define MUSICAS 5

int main() {
    int escutas[DIAS][MUSICAS];
    int totalPorDia[DIAS] = {0};
    int totalPorMusica[MUSICAS] = {0};

    char dias[DIAS][10] = {"Seg", "Ter", "Qua", "Qui", "Sex", "Sab", "Dom"};
    char musicas[MUSICAS][40] = {
        "Creep - Radiohead",
        "Boys Don't Cry - The Cure",
        "Iris - Goo Goo Dolls",
        "Somebody's Watching Me - Rockwell",
        "Spending My Time - Roxette"
    };

    printf("🎵 Bem-vindo ao MeuSomTracker!\n");
    printf("Vamos registrar quantas vezes você ouviu suas músicas favoritas durante a semana.\n\n");

    for (int i = 0; i < DIAS; i++) {
        printf("Dia %s:\n", dias[i]);
        for (int j = 0; j < MUSICAS; j++) {
            printf("  Quantas vezes você ouviu '%s'? ", musicas[j]);
            scanf("%d", &escutas[i][j]);
            totalPorDia[i] += escutas[i][j];
            totalPorMusica[j] += escutas[i][j];
        }
        printf("\n");
    }

    int picoDia = 0;
    for (int i = 1; i < DIAS; i++) {
        if (totalPorDia[i] > totalPorDia[picoDia]) {
            picoDia = i;
        }
    }

    int hit = 0;
    for (int j = 1; j < MUSICAS; j++) {
        if (totalPorMusica[j] > totalPorMusica[hit]) {
            hit = j;
        }
    }

    printf("\n📊 Total de escutas por dia:\n");
    for (int i = 0; i < DIAS; i++) {
        printf("%s: %d escutas\n", dias[i], totalPorDia[i]);
    }

    printf("\n🎶 Total de escutas por música:\n");
    for (int j = 0; j < MUSICAS; j++) {
        printf("%s: %d escutas\n", musicas[j], totalPorMusica[j]);
    }

    printf("\n🔥 Dia que você mais ouviu música: %s (%d escutas)\n", dias[picoDia], totalPorDia[picoDia]);
    printf("⭐ Música mais escutada: %s (%d escutas)\n", musicas[hit], totalPorMusica[hit]);

    printf("\n📈 Gráfico de Popularidade:\n");
    for (int j = 0; j < MUSICAS; j++) {
        printf("%s: ", musicas[j]);
        int barras = totalPorMusica[j] / 2;
        for (int b = 0; b < barras; b++) {
            printf("♪");
        }
        printf("\n");
    }

    return 0;
    }
