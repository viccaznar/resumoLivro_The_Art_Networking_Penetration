# Capítulo 1: Simulação de Ataque Adversarial (Pentesting) ⚔️

## 1.1 Definição e Propósito 🔍
Uma simulação de ataque adversarial, ou pentest, é a contratação de um especialista para imitar um hacker real, explorando falhas de forma furtiva até o relatório final. O objetivo é revelar brechas antes que invasores as descubram.


  - **Exemplo lúdico:** Imagine um famoso parque de diversões que convida um “moleque travesso” para tentar burlar cada trava, detector de movimento e porta secreta — antes que o parque abra ao público — e depois entrega um mapa com todos os pontos frágeis.


## 1.2 Escopo de Engajamento 🗂️
- Aplicações web e mobile  

- Infraestrutura de rede  

- Implementações wireless  

- Acesso físico a escritórios  

- Engajamento furtivo vs. varredura rápida  


  - **Exemplo lúdico:** É como escolher se o “moleque travesso” vai entrar fantasiado de cliente, de entregador de pizza ou simplesmente invadir pelas chaminés enquanto todo mundo dorme.


## 1.3 Threat Actor 🎯
“Threat actor” significa atacante — qualquer pessoa que queira prejudicar os ativos de TI de uma organização. Pode ser um hacker externo, um colaborador descontente ou até um entregador de flores com más intenções.


  - **Exemplo lúdico:** Um funcionário honesto é como um cidadão do reino; um threat actor é o espião disfarçado que se infiltra na corte fingindo entregar flores.


## 1.4 Internal Network Penetration Test (INPT) 🌐
No INPT, assume-se que o invasor já está “dentro das muralhas”: acesso físico ao escritório ou acesso remoto via phishing. A partir daí, basta um ponto fraco para comprometer toda a rede interna.


  - **Exemplo lúdico:** Imagine que o espião já entrou no castelo e só precisa encontrar uma janela destrancada ou uma sala de armazenamento sem guardas para plantar um dispositivo espião.


## 1.5 Workflow Típico do INPT 📊
1. **Fase 1 – Coleta de Informação**  
   - Descobrir hosts na rede  
   - Enumerar serviços e portas abertas  


2. **Fase 2 – Penetração Focada**  
   - Explorar vulnerabilidades conhecidas  
   - Estabelecer ponto de retorno seguro  
   - Capturar credenciais  


3. **Fase 3 – Pós-Exploração e Escalada**  
   - Pivotar entre sistemas  
   - Subir privilégios até administrador de domínio  


4. **Fase 4 – Documentação**  
   - Reunir evidências (logs, capturas de tela)  
   - Elaborar relatório com passos de correção  


  - **Exemplo lúdico:** É como um jogo de tabuleiro onde, em cada fase, você compra cartas de ataque (ferramentas), avança casas (sistemas explorados) e, no fim, escreve o manual de “como vencer o jogo” para ensinar aos guardas do castelo.


# Capítulo 2: Boas Práticas e Cenários Reais 🏢

## 2.1 Definir Escopo e Rules of Engagement 📋
- Documentar limites do teste  
- Acordar horários, sistemas e métodos permitidos  
- Garantir assinaturas legais  


  - **Cenário real:** Uma fábrica de automóveis define que pentest só pode usar phishing interno e jamais interromper a linha de produção, evitando prejuízo e litígio.


## 2.2 Testes Regulares e Monitoramento Contínuo 🔄
- Pentests semestrais ou trimestrais  
- Scans de vulnerabilidade semanais  
- Alertas em tempo real com SIEM  


  - **Cenário real:** Uma fintech descobriu um servidor de homologação exposto ao internet após um scan automatizado disparar um alerta às 2 h da manhã.


## 2.3 Equipe e Comunicação Integrada 🤝
- CISO, TI, jurídico e comunicação alinhados  
- Planos de resposta documentados  
- Simulações de crise (tabletop exercises)  


  - **Cenário real:** No vazamento de dados de 2018, uma empresa de tecnologia reagiu em 4 h graças ao exercício de crise realizado semanas antes, poupando milhões em multas.


## 2.4 Ferramentas e Automação 🤖
- Nmap, OpenVAS para varredura  
- Metasploit para exploração controlada  
- Ansible/Chef para automação de hardening  


```python
import nmap
scanner = nmap.PortScanner()
scanner.scan('10.0.0.0/24', arguments='-sV -T4')
for host in scanner.all_hosts():
    print(host, scanner[host].state())
```


  - **Cenário real:** Uma provedora de cloud implementou teste de penetração interno automatizado e reduziu tempo de resposta a falhas de dias para minutos.


## 2.5 Estudos de Caso 📝

- `Equifax 2017:` demora no patch levou ao vazamento de 145 mi de dados  
- `Banco Delta:` red team descobriu firewall mal configurado antes de ataque real  
- `Startup Gama:` bug bounty que identificou backdoor deixado por terceirizada  


# Capítulo 3: Exercícios de Fixação 📝

1. Explique, em suas palavras, o propósito de um pentest adversarial.  

2. Relacione cada fase do INPT com uma etapa de um “jogo de invasão” lúdico.  

3. Cite três regras essenciais de engagement que evitam problemas legais.  

4. Proponha um mini-scripts em Python ou Bash para varredura de portas numa rede pequena.  


## Soluções

1. Identificar falhas e mostrar como invasores reais explorariam a rede, antes que causem danos.  
2.  
   - Fase 1 = Mapear o tabuleiro  
   - Fase 2 = Jogar cartas de ataque  
   - Fase 3 = Mover-se pelos territórios conquistados  
   - Fase 4 = Escrever o manual de “como ganhamos”  
3.  
   - Limites do escopo e horários  
   - Autorização formal assinada  
   - Métodos e ferramentas permitidos  
4. Exemplo Bash:  


```bash
for ip in 10.0.0.{1..50}; do
  nmap -Pn -p 22,80,443 $ip
done
```
