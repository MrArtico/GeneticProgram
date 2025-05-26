# Relatório de Melhorias na Programação Genética Aplicada ao Controle de Robôs

**Grupo:** 5
**Data de Entrega:** 26/05/2025  
**Repositório GitHub:** https://github.com/MrArtico/GeneticProgram/tree/main  

---

## 1. Introdução
Este relatório documenta as otimizações realizadas no algoritmo de Programação Genética (PG) para controle de um robô autônomo em ambiente 2D com obstáculos, recursos e meta. As modificações focaram em:
- Eficiência na navegação
- Prevenção de colisões
- Coleta estratégica de recursos
- Aceleração do processo evolutivo

---

## 2. Melhorias Implementadas

### 2.1. Operadores Genéticos (Classe `IndividuoPG`)
| Mudança | Original | Modificado | Justificativa |
|---------|----------|------------|---------------|
| Operadores básicos | `+`, `-`, `*`, `/` | Adicionados `desviar_obstaculo`, `buscar_recurso`, `evitar_borda` | Comportamentos especializados |
| Controle de valores | `random.uniform(-5, 5)` | `random.choice([-1, -0.5, 0, 0.5, 1])` | Movimentos mais suaves |
| Estrutura de árvores | Profundidade fixa | Subárvores especializadas por função | Maior eficiência computacional |

### 2.2. Função de Fitness (Classe `ProgramacaoGenetica`)
```python
# Cálculo de fitness balanceado
fitness_tentativa = 0
fitness_tentativa += robo.recursos_coletados * 100
fitness_tentativa += 150 if robo.meta_atingida else 0
fitness_tentativa -= robo.colisoes * 20
fitness_tentativa = max(0, fitness_tentativa)
fitness += fitness_tentativa;
```

### 2.3 Mutação e Mutação_no
| Mudança | Original | Modificado | Justificativa |
|---------|----------|------------|---------------|
| Probabilidade de mutação | 0.5 | 0.6 | Maior exploração do espaço de busca |
| Valores de mutação | [-3, 3] | [-1, -0.5, 0, 0.5, 1] | Movimentos mais precisos |
| Variáveis sensores | Lista simples | Lista ponderada com repetições | Priorização de sensores críticos |
| Operadores | Básicos | Expandidos com funções especializadas | Comportamentos mais complexos |


# Imagens de evolução anexadas no repositório...