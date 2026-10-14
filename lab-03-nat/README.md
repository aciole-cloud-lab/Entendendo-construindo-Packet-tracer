# Laboratório: Examinando o NAT (Network Address Translation)

## 🎯 Objetivo
Compreender o funcionamento do NAT (Network Address Translation) em um ambiente simulado, analisando como endereços IP privados de uma rede local são traduzidos para endereços públicos ao acessar recursos externos na internet.

## 🛠️ Tecnologias e Ferramentas Utilizadas
* **Cisco Packet Tracer** (Modo de Simulação)
* **Protocolos:** NAT / PAT (Port Address Translation), TCP/IP, HTTP
* **Dispositivos:** 1 Computador Cliente (Rede Privada), 1 Roteador SOHO com NAT ativado e 1 Servidor Web Externo (Simulando a Internet).

## 📐 Parâmetros de Rede e Configuração
* **Endereço IP do Host Local (PC):** `192.168.0.10` (Máscara: `255.255.255.0`)
* **Gateway Padrão (Roteador SOHO com NAT):** `192.168.0.1`
* **Endereço IP do Servidor Web na Internet:** `209.165.200.225`
* **Tradução:** O roteador atua mascarando o IP privado `192.168.0.10` utilizando a sua interface pública conectada à nuvem.

## 📝 Passo a Passo da Implementação
1. **Montagem da Topologia:** 
   * Configuramos o computador cliente com IP fixo e o respectivo gateway apontando para o roteador SOHO.
   * Configuramos o servidor externo simulando um destino na internet com o IP `209.165.200.225`.
2. **Ativação da Tabela NAT no Roteador:** 
   * Verificamos nas configurações do roteador SOHO que o recurso de NAT dinâmico e mascaramento de pacotes estava ativo nas interfaces de saída.
3. **Inspeção de Tráfego (Modo Simulação):** 
   * Abrimos o navegador web no computador cliente e tentamos acessar o endereço do servidor externo.
   * Utilizamos o **Simulation Mode** do Packet Tracer para capturar e inspecionar o pacote de dados camada por camada (PDU).

## 🔍 Testes e Resultados
* **Análise de Cabeçalhos (Inbound vs. Outbound):** 
  * Observamos que quando o pacote sai do computador (`192.168.0.10`), o endereço IP de origem é privado.
  * Ao passar pelo roteador SOHO, o mecanismo de NAT altera o IP de origem privado para o IP público do roteador antes de enviá-lo para a internet. Quando a resposta do servidor retorna, o NAT faz o caminho inverso, entregando o pacote de volta ao PC correto.

## 💡 Aprendizados e Próximos Passos
Este laboratório é de altíssima relevância para a computação em nuvem. O conceito de NAT estudado aqui é exatamente o que você aplica ao configurar **NAT Gateways** e **VPCs** na AWS, permitindo que instâncias em sub-redes privadas acessem atualizações na internet de forma segura sem expor seus IPs internos diretamente.
