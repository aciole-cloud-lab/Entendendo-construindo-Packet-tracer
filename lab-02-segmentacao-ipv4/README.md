# Laboratório: Segmentação de Rede e Subnetting (IPv4)

## 🎯 Objetivo
Compreender e aplicar o conceito de divisão de redes (Subnetting) utilizando o protocolo IPv4, segmentando uma rede base em blocos menores para otimizar o tráfego de broadcast e isolar departamentos dentro do Cisco Packet Tracer.

## 🛠️ Tecnologias e Ferramentas Utilizadas
* **Cisco Packet Tracer** (Simulador de redes)
* **Endereçamento IPv4 e Máscaras de Sub-rede** (Bloco `/24` dividido em sub-redes `/25`)
* **Dispositivos:** 1 Roteador, 2 Switches e computadores clientes divididos em duas sub-redes distintas.

## 📐 Topologia da Rede
![Topologia de Subnetting](images/topologia-subnetting.png)

## 📝 Planejamento do Endereçamento (Subnetting)
Para este laboratório, partimos da rede base **`192.168.1.0/24`** e aplicamos uma divisão para criar duas sub-redes com a máscara **`/25`** (`255.255.255.128`):

* **Sub-rede A (Setor Administrativo):**
  * **Endereço de Rede:** `192.168.1.0/25`
  * **Gateway Padrão (Interface do Roteador - Fa0/0):** `192.168.1.1`
  * **Faixa de IPs Utilizáveis:** `192.168.1.2` a `192.168.1.126`
  * **Exemplo de IP no Host (PC0):** `192.168.1.10` (Máscara: `255.255.255.128`)

* **Sub-rede B (Setor Técnico):**
  * **Endereço de Rede:** `192.168.1.128/25`
  * **Gateway Padrão (Interface do Roteador - Fa0/1):** `192.168.1.129`
  * **Faixa de IPs Utilizáveis:** `192.168.1.130` a `192.168.1.254`
  * **Exemplo de IP no Host (PC1):** `192.168.1.140` (Máscara: `255.255.255.128`)

## 📝 Passo a Passo da Implementação
1. **Configuração das Interfaces do Roteador (Gateway):** 
   * Acessamos a interface `FastEthernet0/0` do roteador, atribuímos o IP `192.168.1.1` com a máscara `255.255.255.128` e executamos o comando `no shutdown` para ativá-la.
   * Acessamos a interface `FastEthernet0/1` do roteador, atribuímos o IP `192.168.1.129` com a máscara `255.255.255.128` e também executamos o comando `no shutdown`.
2. **Configuração Estática dos Hosts:** 
   * No **PC0** (Sub-rede A), configuramos o IP `192.168.1.10`, máscara `255.255.255.128` e gateway `192.168.1.1`.
   * No **PC1** (Sub-rede B), configuramos o IP `192.168.1.140`, máscara `255.255.255.128` e gateway `192.168.1.129`.

## 🔍 Testes e Resultados
* **Teste Local (Dentro da mesma sub-rede):** Um `ping` disparado de `PC0` para outro computador na mesma sub-rede respondeu imediatamente via Switch, sem passar pelo roteador.
* **Teste de Roteamento entre Sub-redes:** Um `ping` disparado de `PC0` (`192.168.1.10`) para `PC1` (`192.168.1.140`) foi bem-sucedido, comprovando que o roteador encaminhou corretamente o tráfego entre as sub-redes diferentes.

## 💡 Aprendizados e Próximos Passos
Este laboratório demonstrou como fatiar uma rede corporativa utilizando máscaras de sub-rede. Dominar o cálculo de blocos CIDR e a distribuição de endereços IP é um conhecimento indispensável para projetar redes virtuais privadas (VPCs) e planejar a arquitetura de instâncias e sub-redes públicas/privadas na AWS.
