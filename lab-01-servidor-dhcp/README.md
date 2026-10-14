# Laboratório: Configuração de Servidor DHCP

## 🎯 Objetivo
Configurar e validar a distribuição automática de endereços IP, máscara de sub-rede e gateway padrão em uma rede local utilizando o Cisco Packet Tracer, simulando um ambiente corporativo básico.

## 🛠️ Tecnologias e Ferramentas Utilizadas
* **Cisco Packet Tracer** (Simulador de redes)
* **Protocolo DHCP** (Dynamic Host Configuration Protocol)
* **Dispositivos:** 1 Servidor central, 1 Switch de camada 2 e computadores clientes (Hosts).

## 📐 Topologia da Rede
<img width="571" height="346" alt="Configurando DHCP" src="https://github.com/user-attachments/assets/0a810181-7075-46f4-aa64-1319fb366c97" />
<!-- Exemplo de como inserir a imagem depois de salvá-la na pasta "images" do seu repositório: -->
![Topologia da Rede DHCP](images/topologia-dhcp.png)

## 📝 Passo a Passo da Implementação
1. **Montagem da Topologia:** 
   * Conectamos os computadores ao Switch e o Servidor ao Switch utilizando cabos de rede adequados (Straight-through).
2. **Configuração IP Estática do Servidor:** 
   * Acessamos as configurações do Servidor na aba *Desktop -> IP Configuration* e definimos um endereço IP fixo 192.168.0.1 e a respectiva máscara de sub-rede 255.255.255.0.
3. **Ativação e Ajuste do Serviço DHCP:** 
   * No Servidor, abrimos a aba *Services* e selecionamos a opção **DHCP**.
   * O serviço foi ativado (Estado: *ON*).
   * Configuramos o *Default Gateway* 192.168.0.1 e o IP inicial de distribuição 192.168.0.10.
   * Salvamos as configurações.
4. **Validação nos Hosts Clientes:** 
   * Em cada computador cliente, alteramos a configuração de IP de *Static* para **DHCP** para testar a atribuição automática de endereço.

## 🔍 Testes e Resultados
* **Comando `ipconfig`:** Executado no prompt de comando dos computadores clientes para verificar se eles receberam os parâmetros de IP corretos gerados pelo servidor.
* **Teste de Conectividade:** Realizamos um teste de `ping` bem-sucedido a partir dos computadores em direção ao gateway e ao servidor, confirmando que a rede está 100% funcional.

## 💡 Aprendizados e Próximos Passos
Este laboratório permitiu compreender a importância da automação na distribuição de endereços de rede, eliminando a necessidade de configurações manuais estáticas que são propensas a falhas em larga escala — um conceito fundamental que também se aplica diretamente à gestão de redes virtuais na nuvem (como a criação de sub-redes e DHCP na AWS).
