# Laboratório: Uso de Telnet e SSH para Gerenciamento Remoto

## 🎯 Objetivo
Comparar o acesso e o gerenciamento remoto de dispositivos de rede utilizando protocolos inseguros em texto plano (Telnet) versus protocolos criptografados e seguros (SSH), aplicando boas práticas de segurança da informação.

## 🛠️ Tecnologias e Ferramentas Utilizadas
* **Cisco Packet Tracer** (Simulador de redes)
* **Protocolos de Gerenciamento:** Telnet (Porta 23) e SSH v2 (Porta 22)
* **Ferramentas de Análise:** Linha de comando (CLI), utilitários de terminal.
* **Dispositivos:** 1 Switch gerenciável (ou Roteador) e 1 Computador de Gerenciamento.

## 📐 Parâmetros de Rede e Configuração
* **Endereço IP de Gerenciamento do Switch (VLAN 1):** `192.168.1.2` (Máscara: `255.255.255.0`)
* **Endereço IP do Computador Cliente:** `192.168.1.10` (Máscara: `255.255.255.0`)
* **Credenciais de Acesso:** Usuário administrador configurado localmente no dispositivo.

## 📝 Passo a Passo da Implementação
1. **Configuração do Endereço IP de Gerenciamento:** 
   * Acessamos a CLI do Switch para configurar a interface virtual de gerência (`interface vlan 1`), atribuindo o IP `192.168.1.2` e ativando-a com o comando `no shutdown`.
2. **Configuração do Servidor Telnet:** 
   * Definimos uma senha de acesso local (`line vty 0 15`) e habilitamos a autenticação por senha em texto plano.
3. **Configuração do Servidor SSH (Seguro):** 
   * Configuramos um nome de domínio criptográfico no dispositivo (`ip domain-name cisco.local`).
   * Geramos as chaves de criptografia RSA (`crypto key generate rsa`) com tamanho recomendado.
   * Ativamos a versão 2 do SSH (`ip ssh version 2`) e restringimos as linhas VTY para aceitar apenas conexões seguras (`transport input ssh`).
4. **Execução dos Testes a partir do Cliente:** 
   * No prompt de comando do PC de gerenciamento, testamos a conexão utilizando `telnet 192.168.1.2` e posteriormente `ssh -l admin 192.168.1.2`.

## 🔍 Testes e Resultados
* **Sessão Telnet:** A conexão foi estabelecida, mas o tráfego gerado viaja inteiramente em texto plano, o que significa que qualquer ferramenta de captura de pacotes (*sniffing*) na rede conseguiria interceptar a senha de administrador.
* **Sessão SSH:** A conexão exigiu a troca de chaves criptografadas e a autenticação foi realizada sobre um túnel seguro e criptografado, garantindo a confidencialidade dos comandos executados.

## 💡 Aprendizados e Próximos Passos
Este laboratório reforça a mentalidade de segurança em infraestrutura de TI. O uso de **SSH** é o padrão obrigatório de mercado para administrar servidores Linux e acessar instâncias de máquinas virtuais na nuvem (como o serviço **AWS EC2** via porta 22), substituindo completamente protocolos obsoletos e vulneráveis como o Telnet.
