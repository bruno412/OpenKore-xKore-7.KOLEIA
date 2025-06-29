# OpenKore Node.js - Ragnarok Latam

Uma conversão completa do OpenKore de Perl para Node.js, especificamente adaptada para o servidor Ragnarok Latam, com suporte ao modo XKore 3 e plugin LatamChecksum.

## 🚀 Status do Projeto

### ✅ **Módulos Implementados (17/50+)**
- **Actor.js** - Classe base para todos os atores (Player, Monster, NPC, etc.)
- **ActorList.js** - Gerenciamento de listas de atores com busca e filtragem
- **Field.js** - Gerenciamento de mapas com pathfinding A* e carregamento de .fld2
- **Network.js** - Sistema de conexão TCP com reconexão automática e parseamento de pacotes
- **Task.js** - Sistema de tarefas com dependências, retry e progresso
- **Settings.js** - Configurações e carregamento de arquivos de controle
- **Tables.js** - Sistema de tabelas do jogo (items, monsters, skills, maps)
- **FileParser.js** - Parser de arquivos de configuração e controle
- **AI.js** - Inteligência artificial com estados, seleção de alvos e macros
- **Commands.js** - Sistema de comandos interativo
- **Log.js** - Sistema de logs com rotação e níveis
- **Utils.js** - Utilitários e funções auxiliares
- **XKore.js** - Modo XKore 3 com injeção de DLL
- **Actor::Player** - Subclasse de ator para jogadores
- **Actor::Monster** - Subclasse de ator para monstros
- **Actor::NPC** - Subclasse de ator para NPCs
- **Actor::You** - Subclasse de ator para o personagem principal

### 🔄 **Em Desenvolvimento**
- Network submodules (PacketParser, MessageTokenizer, etc.)
- TaskManager para gerenciamento avançado de tarefas
- AI submodules (Attack, CoreLogic, Slave, etc.)

### 📊 **Progresso Geral**
- **Funcionalidade Básica**: 15% completa
- **Funcionalidade Avançada**: 1% completa
- **Pronto para Uso**: Desconhecido
- **Pronto para Produção**: Em desenvolvimento

## 🏆 Características Principais

### ✨ **Funcionalidades Implementadas**
- ✅ **Sistema de Atores**: Gerenciamento completo de players, monstros, NPCs e personagem principal
- ✅ **Pathfinding A***: Navegação inteligente em mapas
- ✅ **Sistema de Tarefas**: Execução sequencial e paralela de ações
- ✅ **Configurações Dinâmicas**: Carregamento automático de arquivos de controle
- ✅ **Tabelas do Jogo**: Acesso completo a dados de items, monstros, skills
- ✅ **Sistema de Logs**: Logs detalhados com rotação automática
- ✅ **Interface de Comandos**: Comandos interativos para controle do bot
- ✅ **Modo XKore 3**: Em trabalho....
- ✅ **Plugin LatamChecksum**: Suporte específico para Ragnarok Latam

### 🏗️ **Integração com OpenKore Original**
- O sistema Node.js utiliza e integra todos os arquivos reais da base openkore-unkore-openkore_main (`control`, `tables`, `fields`), mantendo compatibilidade total com a estrutura e lógica do OpenKore original.

## 📦 Instalação

### Pré-requisitos
- Node.js 16+ 
- NPM ou Yarn
- Windows (para modo XKore)

### Instalação Rápida
```bash
# Clonar o repositório
git clone <repository-url>
cd Xkore-Latam

# Instalar dependências
npm install

# Configurar arquivos de controle
cp -r ../control/* control/
cp -r ../tables/* tables/
cp -r ../fields/* fields/

# Executar
node rola-latam.js
```

## ⚙️ Configuração

### 1. **Arquivo Principal**: `config.txt`
```ini
# Configurações do servidor
server_host 127.0.0.1
server_port 6900
username seu_usuario
password sua_senha

# Configurações do bot
auto_login 1
auto_reconnect 1
reconnect_delay 5
max_reconnect_attempts 5

# Configurações de AI
ai_enabled 1
ai_attack_auto 1
ai_attack_useWeapon 1
ai_attack_distance 1.5
```

### 2. **Arquivos de Controle**
- `mon_control.txt` - Controle de monstros
- `items_control.txt` - Controle de itens
- `pickupitems.txt` - Itens para pegar
- `avoid.txt` - Monstros para evitar
- `shop.txt` - Configurações de venda
- `buyer_shop.txt` - Configurações de compra
- `macros.txt` - Macros automáticas
- `responses.txt` - Respostas automáticas

### 3. **Múltiplas Instâncias**
```bash
# Instância 1
node rola-latam.js --control control1 --port 6901

# Instância 2  
node rola-latam.js --control control2 --port 6902

# Instância 3
node rola-latam.js --control control3 --port 6903
```

## 🎮 Uso

### Inicialização
```bash
# Iniciar bot
node rola-latam.js

# Iniciar com configuração específica
node rola-latam.js --config config2.txt

# Iniciar em modo debug
node rola-latam.js --debug
```

### Comandos Disponíveis
```
ai on/off          - Ativar/desativar AI
attack <target>    - Atacar alvo
move <x> <y>       - Mover para posição
use <skill> <target> - Usar skill
pickup <item>      - Pegar item
status             - Mostrar status
config reload      - Recarregar configurações
tables info        - Informações das tabelas
help               - Mostrar ajuda
quit               - Sair
```

### Exemplos de Uso
```javascript
// Exemplo de uso programático
const { Actor, Player, Monster, NPC, You, ActorList, Task } = require('./src');

// Criar jogador
const player = new Player();
player.ID = 12345;
player.name = 'MeuChar';
player.setPosition(100, 200);

// Criar monstro
const monster = new Monster();
monster.monsterID = 1001;
monster.name = 'Poring';

// Criar NPC
const npc = new NPC();
npc.npcID = 2001;
npc.name = 'Kafra';

// Criar personagem principal
const you = new You();
you.name = 'MeuCharPrincipal';

you.setPosition(150, 250);

// Criar lista de monstros
const monsters = new ActorList('Monsters');
monsters.add(monster);

// Criar tarefa de movimento
const moveTask = new Task('Move', { x: 150, y: 250 });
await moveTask.start();
```

## 🗂️ Estrutura do Projeto

```
Xkore-Latam/
├── src/                    # Código fonte
│   ├── Actor.js           # Classe base para atores
│   ├── ActorList.js       # Gerenciamento de listas
│   ├── Player.js          # Subclasse de ator para jogadores
│   ├── Monster.js         # Subclasse de ator para monstros
│   ├── NPC.js             # Subclasse de ator para NPCs
│   ├── You.js             # Subclasse de ator para personagem principal
│   ├── Field.js           # Gerenciamento de mapas
│   ├── Network.js         # Conexões de rede
│   ├── Task.js            # Sistema de tarefas
│   ├── Settings.js        # Configurações
│   ├── Tables.js          # Tabelas do jogo
│   ├── AI.js              # Inteligência artificial
│   ├── Commands.js        # Sistema de comandos
│   ├── Log.js             # Sistema de logs
│   ├── Utils.js           # Utilitários
│   └── XKore.js           # Modo XKore
├── control/               # Arquivos de controle
├── tables/                # Tabelas do jogo
├── fields/                # Arquivos de mapa
├── plugins/               # Plugins
├── logs/                  # Logs do sistema
├── rola-latam.js          # Arquivo principal
├── package.json           # Dependências
└── README.md              # Documentação
```

## 🔌 Plugins

- **LatamChecksum**: Plugin para autenticação Ragnarok Latam

## 🛠️ Troubleshooting

- Certifique-se de que todos os arquivos de controle, tabelas e campos estejam presentes nas pastas correspondentes.
- Use o comando `config reload` para recarregar configurações sem reiniciar o bot.
- Consulte os logs em `logs/` para detalhes de erros e execução.

## 📚 Contribuição

- Siga o padrão dos módulos já implementados.
- Documente suas funções e classes.
- Envie pull requests com descrições detalhadas.

## 📄 Licença

Este projeto é licenciado sob a licença MIT.

## 🙏 Agradecimentos

- **OpenKore Team** - Projeto original em Perl
- **Ragnarok Latam** - Servidor de destino
- **Node.js Community** - Runtime e ecossistema
- **Contribuidores** - Apenas eu por enquanto...

## 📞 Suporte

### Canais de Suporte
- **Issues**: GitHub Issues
- **Discord**: none 
- **Documentação**: breve

### Informações de Contato
- **Email**: stigma@xcore-nodejs.com

---

**⚠️ Aviso Legal**: Este software é para fins educacionais. Use por sua conta e risco. Respeite os termos de serviço do jogo.

**🎮 Divirta-se jogando!** 