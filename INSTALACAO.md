# Guia de Instalação - xKore Latam

## Pré-requisitos

### 1. Node.js
- **Versão mínima**: 16.x
- **Versão recomendada**: 18.x LTS
- **Download**: https://nodejs.org/

### 2. Arquivos do OpenKore Original
Você precisa ter os seguintes arquivos do OpenKore original:
- `control/` (pasta com configurações)
- `tables/` (pasta com dados do jogo)
- `fields/` (pasta com mapas)

## Instalação Passo a Passo

### Passo 1: Preparar o Ambiente

1. **Instalar Node.js**
   ```bash
   # Verificar se está instalado
   node --version
   npm --version
   ```

2. **Clonar ou baixar o xKore Latam**
   ```bash
   # Se usando git
   git clone <repository-url>
   cd Xkore-Latam
   
   # Ou baixar e extrair o ZIP
   ```

### Passo 2: Copiar Arquivos Necessários

1. **Copiar pastas do OpenKore original**
   ```bash
   # Windows
   xcopy "..\control" "control\" /E /I /Y
   xcopy "..\tables" "tables\" /E /I /Y
   xcopy "..\fields" "fields\" /E /I /Y
   
   # Linux/Mac
   cp -r ../control ./
   cp -r ../tables ./
   cp -r ../fields ./
   ```

2. **Verificar se as pastas foram copiadas**
   ```bash
   ls control/
   ls tables/
   ls fields/
   ```

### Passo 3: Instalar Dependências

```bash
npm install
```

### Passo 4: Configurar Conta

1. **Editar arquivo de configuração**
   ```bash
   # Abrir o arquivo
   notepad control/config.txt  # Windows
   nano control/config.txt     # Linux/Mac
   ```

2. **Configurar credenciais**
   ```txt
   username seu_usuario
   password sua_senha
   char 0
   ```

3. **Configurar servidor**
   ```txt
   master Latam
   server 0
   ```

### Passo 5: Testar Instalação

```bash
# Windows
start.bat

# Linux/Mac
./start.sh
```

## Configuração Avançada

### Múltiplas Instâncias

1. **Criar pastas de controle separadas**
   ```bash
   mkdir control-char1
   mkdir control-char2
   mkdir control-char3
   ```

2. **Copiar configurações**
   ```bash
   cp control/config.txt control-char1/
   cp control/config.txt control-char2/
   cp control/config.txt control-char3/
   ```

3. **Configurar portas diferentes**
   ```txt
   # control-char1/config.txt
   XKore_listenPort 6901
   logFile logs/xkore-char1.log
   
   # control-char2/config.txt
   XKore_listenPort 6902
   logFile logs/xkore-char2.log
   
   # control-char3/config.txt
   XKore_listenPort 6903
   logFile logs/xkore-char3.log
   ```

4. **Iniciar múltiplas instâncias**
   ```bash
   # Windows
   multi-instance.bat
   
   # Linux/Mac (manual)
   node rola-latam.js -c control-char1/config.txt &
   node rola-latam.js -c control-char2/config.txt &
   node rola-latam.js -c control-char3/config.txt &
   ```

### Configurações de Rede

```txt
# XKore
XKore 3                    # Modo proxy
XKore_port 2350           # Porta do servidor
XKore_listenIp 127.0.0.1  # IP de escuta
XKore_listenPort 6901     # Porta de escuta
XKore_silent 1            # Modo silencioso
```

### Configurações de AI

```txt
# Auto ataque
attackAuto 2              # 0=desligado, 1=quando atacado, 2=sempre
attackDistance 1.5        # Distância mínima
attackMaxDistance 8       # Distância máxima
attackUseWeapon 1         # Usar arma

# Auto follow
follow 0                  # 0=desligado, 1=ligado
followDistanceMax 6       # Distância máxima
followDistanceMin 2       # Distância mínima
```

### Configurações de Log

```txt
# Log
logLevel info             # error, warning, info, debug
logFile logs/xkore.log    # Arquivo de log
debug 0                   # Modo debug
quiet 0                   # Modo silencioso
```

## Troubleshooting

### Erro: "Node.js não encontrado"
**Solução**: Instalar Node.js de https://nodejs.org/

### Erro: "Falha ao instalar dependências"
**Solução**: 
```bash
# Limpar cache do npm
npm cache clean --force

# Reinstalar dependências
rm -rf node_modules package-lock.json
npm install
```

### Erro: "Porta já em uso"
**Solução**: 
```bash
# Verificar portas em uso
netstat -an | findstr 6901  # Windows
netstat -an | grep 6901     # Linux/Mac

# Usar porta diferente
XKore_listenPort 6902
```

### Erro: "Plugin não encontrado"
**Solução**: Verificar se o arquivo existe em `plugins/LatamChecksum.js`

### Erro: "Pasta control não encontrada"
**Solução**: Copiar a pasta `control` do OpenKore original

### Erro: "Conectado ao servidor"
**Solução**: 
1. Verificar se o servidor está online
2. Verificar configurações de rede
3. Verificar firewall

### Logs não aparecem
**Solução**:
1. Verificar nível de log: `logLevel info`
2. Verificar arquivo de log: `logFile logs/xkore.log`
3. Verificar permissões da pasta `logs/`

## Comandos Úteis

### Verificar Status
```bash
# No console do bot
status
info
```

### Recarregar Configurações
```bash
# No console do bot
reload
```

### Parar Bot
```bash
# No console do bot
quit
exit

# Ou Ctrl+C
```

### Debug
```bash
# Iniciar com debug
node rola-latam.js -d

# No console do bot
debug on
log debug
```

## Estrutura de Arquivos

```
Xkore-Latam/
├── src/                    # Código fonte
├── plugins/                # Plugins
├── control/                # Configurações (copiado)
├── tables/                 # Dados do jogo (copiado)
├── fields/                 # Mapas (copiado)
├── logs/                   # Arquivos de log
├── control-char1/          # Configuração char1
├── control-char2/          # Configuração char2
├── control-char3/          # Configuração char3
├── package.json            # Dependências
├── rola-latam.js           # Arquivo principal
├── start.bat               # Script Windows
├── start.sh                # Script Linux/Mac
├── multi-instance.bat      # Multi-instância Windows
└── README.md               # Documentação
```

## Suporte

- **Issues**: Reporte bugs no GitHub
- **Discord**: Entre no servidor da comunidade
- **Wiki**: Documentação detalhada

## Changelog

### v1.0.0
- Versão inicial
- XKore 3 implementado
- Plugin LatamChecksum
- Sistema de AI básico
- Interface de comandos
- Sistema de plugins
- Logging estruturado
- Suporte a múltiplas instâncias 