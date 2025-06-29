# Dependências - xKore Latam

## Dependências Principais

### Core (Node.js Built-in)
- `net` - Rede TCP/UDP
- `crypto` - Criptografia
- `fs` - Sistema de arquivos
- `path` - Manipulação de caminhos
- `events` - Sistema de eventos
- `util` - Utilitários
- `buffer` - Manipulação de buffers
- `stream` - Streams
- `querystring` - Parsing de query strings
- `url` - Manipulação de URLs
- `http` - Cliente HTTP
- `https` - Cliente HTTPS
- `zlib` - Compressão
- `readline` - Interface de linha de comando
- `child_process` - Processos filhos
- `os` - Informações do sistema operacional
- `cluster` - Clustering
- `worker_threads` - Threads de trabalho
- `perf_hooks` - Performance hooks
- `v8` - Engine V8
- `vm` - Máquina virtual
- `assert` - Asserções
- `constants` - Constantes
- `domain` - Domínios
- `punycode` - Codificação Punycode
- `string_decoder` - Decodificação de strings
- `timers` - Timers
- `tty` - Terminal
- `tls` - TLS/SSL
- `dgram` - Datagramas UDP
- `dns` - Resolução DNS

### Dependências Externas

#### Interface e CLI
- `inquirer` - Interface de perguntas interativas
- `chalk` - Cores no terminal
- `commander` - Parser de argumentos de linha de comando

#### Logging
- `winston` - Sistema de logging estruturado

#### Utilitários
- `moment` - Manipulação de datas
- `lodash` - Utilitários JavaScript
- `node-cron` - Agendamento de tarefas

#### Rede e Comunicação
- `ws` - WebSockets
- `express` - Framework web
- `socket.io` - WebSockets em tempo real

#### Banco de Dados
- `sqlite3` - SQLite
- `mysql2` - MySQL

#### Segurança
- `bcrypt` - Hash de senhas
- `jsonwebtoken` - JWT

#### Configuração
- `dotenv` - Variáveis de ambiente
- `yaml` - Parser YAML
- `xml2js` - Parser XML

#### Web Scraping
- `cheerio` - jQuery para servidor
- `axios` - Cliente HTTP
- `form-data` - Dados de formulário
- `multer` - Upload de arquivos

#### Middleware
- `cors` - CORS
- `helmet` - Segurança HTTP
- `compression` - Compressão
- `morgan` - Logging HTTP
- `express-rate-limit` - Rate limiting

## Instalação

### Instalação Automática
```bash
npm install
```

### Instalação Manual (se necessário)
```bash
# Core
npm install inquirer chalk commander winston

# Utilitários
npm install moment lodash node-cron

# Rede
npm install ws express socket.io

# Banco de dados
npm install sqlite3 mysql2

# Segurança
npm install bcrypt jsonwebtoken

# Configuração
npm install dotenv yaml xml2js

# Web scraping
npm install cheerio axios form-data multer

# Middleware
npm install cors helmet compression morgan express-rate-limit
```

## Versões Recomendadas

```json
{
  "dependencies": {
    "inquirer": "^8.2.5",
    "chalk": "^4.1.2",
    "commander": "^9.4.1",
    "winston": "^3.8.2",
    "moment": "^2.29.4",
    "lodash": "^4.17.21",
    "node-cron": "^3.0.2",
    "ws": "^8.12.1",
    "express": "^4.18.2",
    "socket.io": "^4.6.1",
    "sqlite3": "^5.1.4",
    "mysql2": "^2.3.3",
    "bcrypt": "^5.1.0",
    "jsonwebtoken": "^9.0.0",
    "dotenv": "^16.0.3",
    "yaml": "^2.2.1",
    "xml2js": "^0.5.0",
    "cheerio": "^1.0.0-rc.12",
    "axios": "^1.3.4",
    "form-data": "^4.0.0",
    "multer": "^1.4.5-lts.1",
    "cors": "^2.8.5",
    "helmet": "^6.1.5",
    "compression": "^1.7.4",
    "morgan": "^1.10.0",
    "express-rate-limit": "^6.7.0"
  }
}
```

## Dependências de Desenvolvimento

```json
{
  "devDependencies": {
    "nodemon": "^2.0.22",
    "jest": "^29.5.0",
    "eslint": "^8.38.0",
    "prettier": "^2.8.7"
  }
}
```

## Instalação de Desenvolvimento

```bash
npm install --save-dev nodemon jest eslint prettier
```

## Scripts NPM

```json
{
  "scripts": {
    "start": "node rola-latam.js",
    "dev": "nodemon rola-latam.js",
    "test": "jest",
    "lint": "eslint src/",
    "format": "prettier --write src/"
  }
}
```

## Compatibilidade

### Node.js
- **Versão mínima**: 16.x
- **Versão recomendada**: 18.x LTS
- **Versão máxima**: 20.x

### Sistemas Operacionais
- **Windows**: 10, 11
- **Linux**: Ubuntu 18.04+, CentOS 7+, Debian 9+
- **macOS**: 10.15+

### Arquiteturas
- **x64**: Suportado
- **x86**: Suportado (limitado)
- **ARM64**: Suportado (Node.js 16+)

## Troubleshooting de Dependências

### Erro: "Module not found"
```bash
# Limpar cache
npm cache clean --force

# Reinstalar
rm -rf node_modules package-lock.json
npm install
```

### Erro: "Permission denied"
```bash
# Linux/Mac
sudo npm install

# Windows (como administrador)
npm install
```

### Erro: "Python not found"
```bash
# Instalar Python 2.7 ou 3.x
# Windows: https://www.python.org/downloads/
# Linux: sudo apt-get install python3
# Mac: brew install python3
```

### Erro: "Build tools not found"
```bash
# Windows
npm install --global windows-build-tools

# Linux
sudo apt-get install build-essential

# Mac
xcode-select --install
```

## Otimizações

### Instalação Rápida
```bash
# Usar cache
npm install --prefer-offline

# Ignorar scripts opcionais
npm install --ignore-scripts
```

### Reduzir Tamanho
```bash
# Instalar apenas produção
npm install --production

# Usar yarn (mais rápido)
yarn install
```

### Verificar Vulnerabilidades
```bash
npm audit
npm audit fix
```

## Monitoramento

### Verificar Dependências Desatualizadas
```bash
npm outdated
npm update
```

### Verificar Licenças
```bash
npm ls
npm license
```

### Análise de Bundle
```bash
npm install -g webpack-bundle-analyzer
webpack-bundle-analyzer bundle.js
``` 