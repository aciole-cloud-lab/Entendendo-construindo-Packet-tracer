# Laboratório: Configuração de Rede Doméstica e Dispositivos SOHO

## 🎯 Objetivo
Configurar os parâmetros essenciais de conectividade e segurança em um roteador sem fio SOHO (Small Office/Home Office), definindo o SSID da rede, o protocolo de criptografia Wi-Fi e integrando dispositivos cabeados e sem fio.

## 🛠️ Tecnologias e Ferramentas Utilizadas
* **Cisco Packet Tracer** (Simulador de redes)
* **Roteador SOHO Wireless**
* **Protocolos:** DHCP, WPA2-PSK (Criptografia sem fio)
* **Dispositivos:** 1 Roteador Sem Fio, computadores desktops (cabeados) e laptops/smartphones (sem fio).

## 📐 Parâmetros de Rede e Configuração
* **Endereço IP do Gateway (Roteador SOHO):** `192.168.0.1`
* **Máscara de Sub-rede:** `255.255.255.0`
* **Faixa de Distribuição DHCP (Pool Local):** `192.168.0.100` a `192.168.0.150`
* **Nome da Rede Sem Fio (SSID):** `CorporateHome_WiFi`
* **Tipo de Segurança Wi-Fi:** WPA2-Personal (AES)

## 📝 Passo a Passo da Implementação
1. **Acesso à Interface de Gerenciamento do Roteador SOHO:** 
   * Acessamos o roteador sem fio na aba *GUI* (Graphical User Interface) para alterar as configurações padrão de fábrica.
2. **Configuração da Conectividade Local (LAN):** 
   * Definimos o IP local do roteador como `192.168.0.1` com a máscara `255.255.255.0` e certificamo-nos de que o servidor DHCP interno estava ativado para distribuir IPs automaticamente aos hosts.
3. **Configuração da Rede Sem Fio (Wireless):** 
   * Na seção de configurações de rádio sem fio (Wireless Settings), definimos o nome da rede (*SSID*) como `CorporateHome_WiFi`.
   * Selecionamos o modo de segurança **WPA2-PSK** e cadastramos uma senha forte para autenticação dos dispositivos.
4. **Conexão dos Clientes:** 
   * Conectamos o computador de mesa (Desktop) utilizando uma interface cabeada e o Laptop utilizando a placa de rede sem fio configurada com o SSID e a senha definidos.

## 🔍 Testes e Resultados
* **Verificação de IP por DHCP:** Executamos o comando `ipconfig` nos dispositivos clientes para confirmar que receberam endereços válidos dentro da faixa `192.168.0.x`.
* **Teste de Conectividade:** Disparamos um comando `ping` dos computadores em direção ao IP do roteador (`192.168.0.1`), obtendo respostas bem-sucedidas e confirmando que a rede local (cabeada e sem fio) está integrada e funcional.

## 💡 Aprendizados e Próximos Passos
Este laboratório permitiu compreender a estrutura de uma rede de borda (periferia), abordando conceitos de segurança de acesso sem fio e distribuição local de endereços — fundamentos essenciais para entender como os pontos de acesso e as redes locais se conectam à infraestrutura de redes corporativas e em nuvem.
