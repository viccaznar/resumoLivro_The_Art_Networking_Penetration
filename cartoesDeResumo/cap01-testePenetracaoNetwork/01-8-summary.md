# Capítulo 1: O Panorama da Segurança em Redes 🌐

## 1.1 Redes Onipresentes 🌍 
Vivemos num mundo movido por sistemas de computadores interconectados, onde cada serviço, loja e aplicativo depende de redes.


  - **Exemplo lúdico:** Pense numa cidade inteira onde cada casa é ligadinha por tubos secretos de correspondência. Se um tubo entope, a cidade inteira para de receber cartas.


## 1.2 Complexidade da Gestão de Segurança 🔒
À medida que empresas crescem, surgem mais servidores, laptops, smartphones e dispositivos IoT. Controlar e proteger tudo fica cada vez mais difícil.


  - **Exemplo lúdico:** É como tentar guardar a chave de cada porta de um castelo com centenas de quartos: você precisa lembrar onde cada chave está e se nenhuma foi perdida.


## 1.3 A Porta Única que Tudo Abre 🚪
Um invasor precisa apenas de um ponto de falha — um servidor sem patch, uma senha fraca ou um dispositivo esquecido — para entrar em toda a rede.


  - **Exemplo lúdico:** Imagine um ladrão que só precisa encontrar uma janela destrancada em todo um quarteirão para invadir todas as casas conectadas por um túnel secreto.


# Capítulo 2: Pentest — Simulação Ativa de Ataque ⚔️

## 2.1 O que é um Penetration Test? 🕵️
Pentest é um exercício autorizado onde especialistas fingem ser adversários, atacando sistemas para descobrir e documentar falhas antes que hackers reais o façam.


  - **Exemplo lúdico:** É como convidar um detetive para tentar roubar o cofre do banco: ele revela exatamente onde estão as trancas soltas e as senhas fáceis.


## 2.2 INPT — A Ameaça Interna Mais Comum 👥
Internal Network Penetration Test (INPT) simula um insider malicioso ou comprometido, com acesso à rede interna, testando o que acontece quando um invasor já “está dentro”.


  - **Exemplo lúdico:** Imagine um jardineiro que, fingindo cuidar das plantas, encontra uma passagem secreta para as câmaras do tesouro.

## 2.3 As Quatro Fases do INPT 🔄
1. **Coleta de Informação**  
Mapear hosts, serviços e versões para criar um inventário de possíveis alvos.  

  - **Exemplo lúdico:** Acender lanternas por todo o castelo para ver quais portas estão abertas e quem mora em cada sala.


2. **Penetração Focada**  
Explorar vulnerabilidades para obter acesso inicial por Remote Code Execution (RCE).  

  - **Exemplo lúdico:** Usar ferramentas de arrombamento para destrancar a primeira porta interna do cofre.


3. **Pós-Exploração e Escalada de Privilégios**  
Coletar credenciais, pivotar para novos sistemas e subir ao nível de administrador de domínio.  

  - **Exemplo lúdico:** Encontrar chaves de outros quartos e roubar a chave-mestra do castelo.

4. **Documentação**  
Registrar evidências, criar narrativa passo a passo e recomendar correções.  

  - **Exemplo lúdico:** Desenhar o mapa do castelo com todas as entradas secretas e instruções para blindá-las.


# Capítulo 3: Boas Práticas e Cenários Reais 🛡️

## 3.1 Inventário e Visibilidade 👀
CMDB atualizada com IPs, DNS e funções de cada sistema.  
Integre varreduras automáticas (Nmap/OpenVAS) ao inventário.

Cenário real  
Uma fintech descobriu 50 servidores “esquecidos” ao vincular scans diários ao CMDB central, fechando 90% das brechas básicas em um mês.


## 3.2 Patching e Hardening Contínuos 🩹
Estabeleça janelas de teste e produção para updates regulares.  
Aplique benchmarks CIS e remova privilégios locais desnecessários.

Cenário real  
No vazamento da Equifax (2017), atrasos de patching expuseram 145 mi de registros; após renovar política de patches, multas bilionárias foram evitadas.

## 3.3 Exercícios de Segurança e Red Team 🔴
Realize pentests trimestrais e simulações de insider.  
Use tabletop exercises para treinar resposta a incidentes.

Cenário real  
Uma grande varejista detectou intrusão real após simulação interna de phishing, interrompendo o ataque de ransomware antes de criptografar dados.

## 3.4 Cultura de Segurança e Transparência 🤝
Recompense colaboradores que reportam falhas (bug bounty interno).  
Documente e compartilhe relatório de ferramentas e processos com clientes.

Cenário real  
Empresa de cloud manteve clientes confiantes ao fornecer inventário completo de ferramentas usadas em pentest e versões de software em seu lab.


# Capítulo 4: Exercícios de Fixação 📝
1. Explique em suas palavras por que um invasor só precisa de um ponto de falha.  

2. Relacione cada fase do INPT a uma etapa de “invasão de castelo”.  

3. Cite três práticas de hardening indispensáveis antes de um pentest.  

4. Escreva um mini-script em Bash para varrer portas 22 e 80 na rede 192.168.10.0/28.


## Soluções
1. Um único sistema vulnerável serve de porta de entrada para toda a rede porque invasores podem se mover lateralmente e escalar privilégios.  

2.  
- Coleta de Informação = Acender lanternas no castelo  
- Penetração Focada = Destrancar a primeira porta  
- Pós-Exploração = Roubar chave-mestra  
- Documentação = Mapear entradas secretas  

3.  
- Patch de segurança aplicado em até 48 h  
- Remoção de privilégios de administrador local  
- Configuração segundo CIS Benchmarks  

4.  
```bash
#!/usr/bin/env bash
for ip in 192.168.10.{1..14}; do
  nmap -Pn -p 22,80 "$ip" | grep 'open'
done
```  
