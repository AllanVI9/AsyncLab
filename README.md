## Membros Do Grupo:
### Allan Von Ivanov - Rm98705
### João Rodrigo - Rm551319

## O que foi modificado?
### 1. Transformação do ponto de entrada
O método Main foi alterado para static async Task Main(string[] args) para permitir o uso de await diretamente.

### 2. Download assíncrono do CSV
Substituição de WebClient.DownloadFile por HttpClient.GetByteArrayAsync com File.WriteAllBytesAsync, permitindo que o download ocorra sem bloquear a thread principal.

### 3. Leitura assíncrona do arquivo CSV
Uso de File.ReadAllLinesAsync para ler o conteúdo do arquivo de forma não bloqueante.

### 4. Cálculo de hash paralelizado
O processo de derivação de hash (CPU-bound) foi distribuído com Task.Run ou Parallel.ForEachAsync, permitindo que múltiplos municípios sejam processados simultaneamente.

### 5. Escrita assíncrona de arquivos
Substituição de StreamWriter.WriteLine e File.WriteAllText por WriteLineAsync e WriteAllTextAsync, evitando bloqueios durante a escrita dos arquivos CSV e JSON.

## Impactos Observados:

### Redução significativa no tempo total de execução, especialmente em máquinas com múltiplos núcleos, devido à paralelização do cálculo de hash.

### Maior responsividade em ambientes com interface gráfica ou servidores web, já que operações de I/O não bloqueiam a thread principal.

### Melhor escalabilidade: o programa pode lidar com conjuntos maiores de dados sem travar ou degradar a experiência.

# ⚡ AsyncLab

## 🧪 Laboratório Async

### 🎯 Objetivo
Analisar o programa e tornar a sua execução **assíncrona**.

### 📝 Atividades
- 🔍 Identificar pontos do programa que podem ser transformados em chamadas assíncronas;  
- ⏱️ Observar o impacto no tempo de execução;  

### 📦 Entrega
- 📌 A entrega deve ser feita através de um **fork** deste repositório.  
- ✍️ No arquivo `README.md` do fork, devem constar:  
  - 👥 **Nomes dos membros do grupo**;  
  - 🛠️ **Descrição das modificações realizadas** para tornar o programa assíncrono;  
  - 📊 Observações sobre os **impactos observados no tempo de execução**.  

### 🌐 Repositório
[https://github.com/profvinicius84/AsyncLab](https://github.com/profvinicius84/AsyncLab)

---

👨‍🏫 © 2025 | Professor Vinícius Costa Santos
