# Instalação da VM

> O servidor da empresa ecentemente recebeu um upgrade, então o antigo está disponível para o uso livre ao decorrer deste projeto

O servidor que usarei está usando o HyperV para gerenciar Maquinas Virtuais, nele instalarei uma distro do linux responsável por rodar o OCS Inventory.

---

Estarei usando Ubuntu Server como maquina virtual, já que a configuração do OCS pode ser feita via interface web.

## Primeiros passos:

Primeiramente, é feito download da ISO do [Ubuntu Server](https://mirror.ufam.edu.br/releases/24.04.2/) (utilizei o mirror a UFAM)

```bat
curl -O https://mirror.ufam.edu.br/releases/24.04.2/ubuntu-24.04.2-live-server-amd64.iso
```

Com a iso baixada, o próximo passo é a criação da maquina virtual no ambiente HyperV, no qual utilizei [este guia](https://learn.microsoft.com/en-us/windows-server/virtualization/hyper-v/get-started/create-a-virtual-machine-in-hyper-v?tabs=hyper-v-manager), diretamente do site da Microsoft:

```
1. Open Hyper-V Manager.

2. In the left pane, under Hyper-V Manager, select your server.

3. From the Actions pane, select New, and then select Virtual Machine.

4. From the New Virtual Machine Wizard, select Next.

5. Make the appropriate choices for your virtual machine on each of the pages. For more information, see New virtual machine options and defaults in Hyper-V Manager.

6. After verifying your choices in the Summary page, select Finish.

7. In Hyper-V Manager, right-click the virtual machine and select Connect....

8. In the Virtual Machine Connection window, select Action > Start.
```

A VM foi criada com as seguintes especificações:
- 8gb Memória
- 50gb Disco digital
- Adaptador de Rede ligado

Após a criação da VM, o Ubuntu server foi instalado seguindo os prompts em tela. As partições foram configuradas para usar todos os 50gb disponíveis.

Usuario `arthur` tem acesso root.







