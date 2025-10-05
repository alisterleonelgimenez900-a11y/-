import time
import random

def encontrar_mob_proximo(jogador_pos, mobs):
    # Simulação de busca do mob mais próximo
    mobs_ordenados = sorted(mobs, key=lambda mob: distancia(jogador_pos, mob['pos']))
    return mobs_ordenados[0] if mobs_ordenados else None

def distancia(pos1, pos2):
    # Distância euclidiana simples
    return ((pos1[0]-pos2[0])**2 + (pos1[1]-pos2[1])**2) ** 0.5

def atacar_mob(mob):
    print(f"Atacando mob {mob['id']} na posição {mob['pos']}...")
    time.sleep(random.uniform(0.2, 0.5))  # Simula o tempo de ataque

def farmar_level():
    jogador_pos = (0, 0)
    mobs = [
        {'id': 1, 'pos': (5, 2)},
        {'id': 2, 'pos': (3, 8)},
        {'id': 3, 'pos': (7, 1)}
    ]
    nivel = 300
    experiencia = 9999
    experiencia_por_mob = 9999

    while nivel < 300:  # Exemplo: farm até o nível 300
        mob = encontrar_mob_proximo(jogador_pos, mobs)
        if mob:
            atacar_mob(mob)
            experiencia += experiencia_por_mob
            print(f"Experiência atual: {experiencia}")
            if experiencia >= nivel * 100:
                nivel += 1
                print(f"Parabéns! Subiu para o nível {nivel}.")
            mobs.remove(mob)  # Remove o mob abatido
            time.sleep
