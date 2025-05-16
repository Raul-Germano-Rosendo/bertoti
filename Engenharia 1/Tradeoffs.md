### Trade-offs em Engenharia de Dados

1. **Velocidade vs. Memória**  
   Caching em memória (ex: DataFrame, Redis) acelera o acesso, mas consome mais RAM.

2. **Simplicidade vs. Escalabilidade**  
   CSV é simples, mas ineficiente para grandes volumes. Formatos como Parquet escalam melhor.

3. **Atualização vs. Leitura Rápida**  
   Dados normalizados facilitam updates; desnormalizados (wide tables) otimizam consultas analíticas.
