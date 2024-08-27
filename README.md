
from bot_abstract import BotAbstract

import random

class Botdesconocido(BotAbstract):
    
    def _init_(self):
        self.opponent_moves = []

    @property
    def Nombre(self) -> str:
        return "desconocido"
    
    def Jugar(self, jugada_numero: int, jugada_previa_oponente: str) -> str:
        # almacenar el movimiento anterior del oponente
        if jugada_previa_oponente:
            self.opponent_moves.append(jugada_previa_oponente)
        
        # analiza el patron de movimiento del oponente
        if len(self.opponent_moves) >= 3:
            if self.opponent_moves[-1] == self.opponent_moves[-2] == self.opponent_moves[-3]:
                # El oponente está repitiendo movimientos, contrarresta con 'M'
                return 'M'
        
        # Introducir algo de aleatoriedad para evitar la previsibilidad.
        if random.random() < 0.2:  # 20% oportunidad de hacer un movimiento aleatorio
            return random.choice(['S', 'M'])
        
        # Movimiento predeterminado
        return 'S'   # Elija 'S' como movimiento estándar

# Esta estrategia ayuda al robot a adaptarse a las tendencias del oponente y a mantener la imprevisibilidad.
