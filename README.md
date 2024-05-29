# Construindo-um-Simulador-de-Batalhas-com-Lua

Neste artigo, vamos criar um simulador de batalhas em Lua, utilizando múltiplos scripts como módulos. Vamos abordar os seguintes tópicos:

1. **Introdução**
2. **Organização do Projeto**
3. **Implementação dos Módulos**
4. **Loop Lógico Infinito**
5. **Interface de Ação para o Usuário**

## **1. Introdução**
A ideia é criar um jogo de batalhas em que o usuário possa tomar decisões e alterar o curso da batalha. Usaremos Lua para implementar esse simulador.

## **2. Organização do Projeto**
Vamos organizar nosso projeto em diferentes arquivos Lua, cada um representando um módulo específico. Por exemplo:
- `main.lua`: O ponto de entrada do programa.
- `batalha.lua`: O módulo responsável pela lógica das batalhas.
- `personagens.lua`: O módulo que define os personagens e suas características.

## **3. Implementação dos Módulos**
### `personagens.lua`
```lua
-- personagens.lua

local Personagem = {}

function Personagem.novo(nome, vida, ataque)
    local self = {}
    self.nome = nome
    self.vida = vida
    self.ataque = ataque

    function self.atacar(outro)
        outro.vida = outro.vida - self.ataque
    end

    return self
end

return Personagem
```

### `batalha.lua`
```lua
-- batalha.lua

local Batalha = {}

function Batalha.iniciar(jogador1, jogador2)
    while jogador1.vida > 0 and jogador2.vida > 0 do
        jogador1:atacar(jogador2)
        jogador2:atacar(jogador1)
    end

    if jogador1.vida > 0 then
        print(jogador1.nome .. " venceu!")
    else
        print(jogador2.nome .. " venceu!")
    end
end

return Batalha
```

## **4. Loop Lógico Infinito**
No arquivo `main.lua`, podemos criar um loop infinito para que o usuário possa tomar decisões durante a batalha.

### `main.lua`
```lua
-- main.lua

local Personagem = require("personagens")
local Batalha = require("batalha")

local jogador1 = Personagem.novo("Herói", 100, 20)
local jogador2 = Personagem.novo("Monstro", 80, 15)

Batalha.iniciar(jogador1, jogador2)
```

## **5. Interface de Ação para o Usuário**
Para criar uma interface de ação, podemos usar a biblioteca `io` para ler entradas do usuário e exibir informações sobre a batalha.

Agora você tem um simulador de batalhas em Lua! Personalize os personagens, adicione mais módulos e explore outras funcionalidades. Divirta-se criando seu próprio jogo de batalhas!

Espero que este artigo tenha sido útil para quem precisar, sinta-se inspirado a continuar explorando a programação em Lua.
