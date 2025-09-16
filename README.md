# Azure Open AI no VNet

## DEV Community

Um espaço para discutir e acompanhar o desenvolvimento de software e gerenciar sua carreira em tecnologia.

---

### Introdução

Os modelos GPT estão hospedados em vários provedores de serviços atualmente, e o Microsoft Azure é um deles. Embora os modelos em si sejam os mesmos, existem muitas diferenças, incluindo:

- Custo
- Funcionalidades
- Tipos de modelos e versões
- Localização geográfica
- Segurança
- Suporte
- Etc.

Um dos aspectos mais importantes ao usá-lo em um ambiente corporativo é, claro, a segurança. Usando os recursos de segurança de rede do Azure com o Azure Open AI, os clientes podem consumir o serviço Open AI de dentro da VNet, garantindo que nenhuma informação flua publicamente.

### Implementação de Exemplo

O repositório de amostras do Azure fornece arquivos Bicep de exemplo para implantar o Azure Open AI em um ambiente VNet.

**GitHub:** openai-enterprise-iac

Os principais recursos usados pelo Bicep são:

- VNet
- Integração VNet para App Web
- Endpoint Privado para Azure Open AI
- Endpoint Privado para Pesquisa Cognitiva
- Zona de DNS Privada

Usando esses recursos, todo o tráfego externo do App Web é roteado apenas dentro da VNet e todos os nomes são resolvidos em endereços IP privados. O Open AI e a Pesquisa Cognitiva desativam o endereço IP público, portanto, não há mais interface pública disponível.

### Implantação

O arquivo Bicep implantará os seguintes recursos do Azure:

Vamos implantar e confirmar como funciona. Criarei um grupo de recursos na região East US para meu próprio teste.

```bash
git clone https://github.com/Azure-Samples/openai-enterprise-iac
cd openai-enterprise-iac
az group create -n openaitest -l eastus
az deployment group create -g openaitest -f .\infra\main.bicep
```

Uma vez que eu execute o comando acima, vejo que a implantação começou. Aguarde até que a implantação seja concluída.

### Teste

Vamos ver se a implantação foi bem-sucedida.

#### Azure Open AI

Vamos tentar o acesso público primeiro. Consegui criar uma implantação sem problemas. Mas quando tento a partir do playground de chat no meu Portal do Azure, vejo o seguinte erro.

Como está o acesso via Web API? 

De uma ferramenta avançada do App Service, faço login na sessão Bash e primeiro pingo a URL do serviço. Vejo que o endereço IP privado atribuído ao Endpoint Privativo é retornado. Em seguida, uso o comando curl para enviar uma solicitação ao endpoint.

---

Esse conteúdo resume a discussão sobre o uso do Azure Open AI em um ambiente VNet, focando em segurança e implementação prática. Se você tiver mais perguntas ou precisar de mais detalhes, fique à vontade para perguntar!
# Azure Open AI no VNet

## DEV Community

Um espaço para discutir e acompanhar o desenvolvimento de software e gerenciar sua carreira em tecnologia.

---

### Introdução

Os modelos GPT estão hospedados em vários provedores de serviços atualmente, e o Microsoft Azure é um deles. Embora os modelos em si sejam os mesmos, existem muitas diferenças, incluindo:

- Custo
- Funcionalidades
- Tipos de modelos e versões
- Localização geográfica
- Segurança
- Suporte
- Etc.

Um dos aspectos mais importantes ao usá-lo em um ambiente corporativo é, claro, a segurança. Usando os recursos de segurança de rede do Azure com o Azure Open AI, os clientes podem consumir o serviço Open AI de dentro da VNet, garantindo que nenhuma informação flua publicamente.

### Implementação de Exemplo

O repositório de amostras do Azure fornece arquivos Bicep de exemplo para implantar o Azure Open AI em um ambiente VNet.

**GitHub:** openai-enterprise-iac

Os principais recursos usados pelo Bicep são:

- VNet
- Integração VNet para App Web
- Endpoint Privado para Azure Open AI
- Endpoint Privado para Pesquisa Cognitiva
- Zona de DNS Privada

Usando esses recursos, todo o tráfego externo do App Web é roteado apenas dentro da VNet e todos os nomes são resolvidos em endereços IP privados. O Open AI e a Pesquisa Cognitiva desativam o endereço IP público, portanto, não há mais interface pública disponível.

### Implantação

O arquivo Bicep implantará os seguintes recursos do Azure:

Vamos implantar e confirmar como funciona. Criarei um grupo de recursos na região East US para meu próprio teste.

```bash
git clone https://github.com/Azure-Samples/openai-enterprise-iac
cd openai-enterprise-iac
az group create -n openaitest -l eastus
az deployment group create -g openaitest -f .\infra\main.bicep
```

Uma vez que eu execute o comando acima, vejo que a implantação começou. Aguarde até que a implantação seja concluída.

### Teste

Vamos ver se a implantação foi bem-sucedida.

#### Azure Open AI

Vamos tentar o acesso público primeiro. Consegui criar uma implantação sem problemas. Mas quando tento a partir do playground de chat no meu Portal do Azure, vejo o seguinte erro.

Como está o acesso via Web API? 

De uma ferramenta avançada do App Service, faço login na sessão Bash e primeiro pingo a URL do serviço. Vejo que o endereço IP privado atribuído ao Endpoint Privativo é retornado. Em seguida, uso o comando curl para enviar uma solicitação ao endpoint.

---

Esse conteúdo resume a discussão sobre o uso do Azure Open AI em um ambiente VNet, focando em segurança e implementação prática. Se você tiver mais perguntas ou precisar de mais detalhes, fique à vontade para perguntar!
