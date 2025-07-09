# Capítulo 1: Laboratório de Pentest ⚙️

## 1.6 Raciocínio Base 🧠 
Aprender pentest requer prática em um ambiente controlado. O texto apresenta o projeto Capsulecorp Pentest, um laboratório virtual pronto para simular uma rede corporativa vulnerável e a máquina atacante, permitindo seguir o processo INPT na prática.


- **Exemplo lúdico:** Imagine um castelo em miniatura montado em uma mesa de sinuca: você pode testar catapultas, túneis secretos e muralhas falsas sem arriscar o castelo de verdade.


# Capítulo 2: Conceitos e Componentes do Lab 🏗️

## 2.1 Projeto Capsulecorp Pentest 📦
É um repositório open source que fornece uma rede virtual vulnerável e uma VM atacante, orquestrada por VirtualBox, Vagrant e Ansible.


- **Exemplo lúdico:** Pense em uma cozinha de brinquedo com panelinhas defeituosas: você testa receitas explosivas sem queimar seu próprio fogão.


### 2.1.1 Ferramentas Utilizadas 🛠️
- VirtualBox: hypervisor para rodar VMs.  
- Vagrant: automatiza criação e gerenciamento de VMs via Vagrantfile.  
- Ansible: configura sistemas automaticamente com playbooks.


  - **Exemplo lúdico:** É como usar um robô masterchef (Ansible) para equipar fornos (VMs) que um mágico (Vagrant) invoca do nada, tudo no seu quintal (seu PC).


# Capítulo 3: Boas Práticas e Cenários Reais 🏢

## 3.1 Isolamento e Segurança 🔒
- Crie o lab em rede NAT ou Host-Only para evitar impactos na rede real.  
- Habilite snapshots para retornar rapidamente ao estado original.


- **Cenário real:** Uma consultoria de TI usa laboratório isolado com snapshots antes de pentests em clientes, reduzindo o tempo de reset de 4 h para 5 minutos.


## 3.2 Documentação e Versionamento 📚
- Mantenha Vagrantfile e playbooks no Git com commits claros.  
- Use tags de versão para relacionar configuração às aulas ou testes.


- **Cenário real:** Startups financeiras versionam playbooks em branchs por sprint, garantindo reprodutibilidade dos testes de segurança em cada release.


## 3.3 Atualização e Manutenção ⏱️
- Atualize boxes do Vagrant e roles do Ansible periodicamente.  
- Teste mudanças em um lab paralelo antes de atualizar o principal.


- **Cenário real:** Um grande banco mantém um staging lab que atualiza semanalmente, evitando drift nos exercícios de Red Team.


# Capítulo 4: Exercícios de Fixação 🎓
1. Clone o repositório Capsulecorp Pentest e liste os arquivos principais.  

2. Escreva um trecho de Vagrantfile declarando uma VM chamada `attacker` com 2 CPUs e 2 GB de RAM.  

3. Crie um playbook Ansible que instale o Nmap na máquina atacante.  

4. Explique como retornar o lab a um snapshot anterior após um teste.


## Soluções
**1.**  
Repositório clonado contém:  
- `Vagrantfile`  
- `ansible/playbook.yml`  
- `machines/` (subpastas com VMs)  
- `docs/` (documentação)


**2.**  
```ruby
# Vagrantfile
Vagrant.configure("2") do |config|
  config.vm.define "attacker" do |vm|
    vm.vm.box = "ubuntu/focal64"
    vm.vm.provider "virtualbox" do |vb|
      vb.memory = "2048"
      vb.cpus   = 2
    end
  end
end
```

**3.**  
```yaml