# exam2
#include <stdio.h>

int atacar(int ataque, int defensa, int *vida)
{
    int dano;

    dano = ataque - defensa;

    *vida = *vida - dano;

    return dano;
}

int main()
{
    int vidaJugador;
    int ataqueJugador;
    int defensaJugador;
    int vidaEnemigo;
    int ataqueEnemigo;
    int defensaEnemigo;
    int opcion;
    int dano;

    vidaJugador = 100;
    ataqueJugador = 33;
    defensaJugador = 10;

    vidaEnemigo = 120;
    ataqueEnemigo = 30;
    defensaEnemigo = 8;

    while (vidaJugador > 0 && vidaEnemigo > 0)
     {
        printf("\n=== COMBATE ===\n");
        printf("Vida del jugador: %d\n", vidaJugador);
        printf("Vida del enemigo: %d\n", vidaEnemigo);

        printf("\n1. Atacar\n");
        printf("2. Curarse\n");
        printf("3. Huir\n");
        printf("4. defender\n");
        printf("Elige una opcion: ");
        scanf("%d", &opcion);

        if (opcion == 1)
        {
            dano = atacar(ataqueJugador, defensaEnemigo, &vidaEnemigo);

            printf("Hiciste %d de dano.\n", dano);

            if (vidaEnemigo > 0)
            {
                dano = atacar(ataqueEnemigo, defensaJugador, &vidaJugador);

                printf("El enemigo te hizo %d de dano.\n", dano);
            }
        }
        else if (opcion == 2)
        {
            vidaJugador = vidaJugador + 20;

            if (vidaJugador > 100)
            {
                vidaJugador = 100;
            }

            printf("Te has curado.\n");
        }
        else if (opcion == 3)
        {
            printf("Has huido del combate.\n");
            break;
        }
        else if (opcion == 4)
        {
            dano = atacar(ataqueEnemigo, defensaJugador+10, &vidaJugador);
            printf("El enemigo te hizo %d de dano.\n", dano);
            
        }
        else
        {
            printf("Opcion no valida.\n");
        }
    }

    if (vidaJugador <= 0)
    {
        printf("\nHas perdido.\n");
    }
    else if (vidaEnemigo <= 0)
    {
        printf("\nHas ganado.\n");
    }

    return 0;
}
