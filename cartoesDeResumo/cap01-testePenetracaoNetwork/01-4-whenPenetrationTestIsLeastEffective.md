# Capítulo 1: Quando o Pentest é Menos Eficaz 🛑

## 1.4.1 Cenários de Baixa Efetividade ⚠️

Pentests muito avançados perdem valor quando a organização ainda falha nos fundamentos de segurança. Se há “frutas fáceis” espalhadas — brechas que qualquer iniciante encontra — não adianta chamar um “hacker profissional” para derrubar muralhas que sequer existem.


  - **Exemplo lúdico:** Pense num pomar onde há maçãs caídas no chão. Em vez de escalar a árvore, o ladrão só precisa apanhar a fruta que já está no nível do chão para saciar a fome.


### Frutas fáceis (Low-Hanging Fruit)
- Senhas e configurações padrão  
- Credenciais compartilhadas entre sistemas  
- Todos têm direitos de administrador local  
- Patches ausentes com exploits públicos  


  - **Exemplo lúdico:** É como deixar a porta da adega destrancada, usar a mesma chave na porta principal e dar cartões VIP a todos os visitantes—o vigia nem precisa correr para entregar o produto.


## 1.4.2 Quando Realmente Precisa de Pentest? ✔️  
Antes de contratar um pentest “do zero ao fim”, responda honestamente a perguntas simples de maturidade. Se faltar robustez em qualquer aspecto, trate disso primeiro.

Perguntas de Maturidade:  

1. Temos registro atualizado de cada IP e nome DNS na rede?  
2. Existe programa de patching rotineiro para sistemas operacionais e apps?  
3. Utilizamos scanner comercial para varreduras periódicas?  
4. Removemos direitos de administrador local dos notebooks?  
5. Exigimos e aplicamos senhas fortes em todas as contas?  
6. Empregamos autenticação multifator em todos os acessos?


  - **Exemplo lúdico:** É como querer testar a resistência de um cofre antes de trocar as fechaduras velhas por um sistema biométrico. Se a fechadura antiga abre com grampos de papel, o cofre não precisa de teste de impacto.


# Capítulo 2: Boas Práticas e Cenários Reais 🧰

## 2.1 Consolide os Básicos 🔑
- Catalogar todos os ativos: IPs, DNS e funções.  
- Patching automático com janelas de teste.  
- Remover privilégios excessivos e aplicar MFA.  
- Políticas de senhas únicas e complexas.


  - **Exemplo lúdico:** É como numerar cada porta de uma mansão, trocar fechaduras semanalmente e dar chaves individuais codificadas aos moradores.


## 2.2 Ferramentas e Automação 🤖
- Nmap/OpenVAS para varredura regular.  
- Ansible ou Chef para hardening automático.


```bash
#!/usr/bin/env bash
# Bash: varredura de host e portas comuns
for ip in 192.168.0.{1..50}; do
  nmap -Pn -p 22,80,443 "$ip"
done
```


  - **Cenário real:** Uma startup reduziu falhas em 70% após integrar scans diários e playbooks de correção automática.


## 2.3 Cultura de Segurança e Treinamento 🧠
- Simulações de phishing mensais.  
- Programas de bug bounty e recompensas.  
- Tabletop exercises para resposta a incidentes.


  - **Cenário real:** Uma fintech salvou milhões ao detectar um ataque real via simulação interna de phishing que descobriu credenciais vazadas.


# Capítulo 3: Exercícios de Fixação 📝
1. Explique por que testar um sistema cheio de vulnerabilidades óbvias antes de um pentest avançado é perda de tempo.  
2. Dê um exemplo lúdico sobre “low-hanging fruit” em um castelo medieval.  
3. Quais quatro práticas básicas devem estar prontas antes de contratar um pentest “do zero ao fim”?  
4. Implemente um mini-script em Bash que enumere máquinas ativas e portas 22, 3389 e 3306.


## Soluções
1. Porque o foco deveria ser primeiro fechar brechas triviais que permitem invasores iniciantes entrarem sem esforço.  

2. Um bardo que pula muralhas para pegar moedas que alguém esqueceu no chão do pátio.  

3.  
   - Inventariar ativos e DNS  
   - Rotina de patching e janelas de teste  
   - MFA e remoção de privilégios locais  
   - Políticas de senhas fortes e exclusivas  

4.  
```bash
#!/usr/bin/env bash
for ip in 10.0.1.{1..100}; do
  nmap -Pn -p 22,3389,3306 "$ip"
done
``` 
