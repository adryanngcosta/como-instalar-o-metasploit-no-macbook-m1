# Como-instalar-o-metasploit-no-macbook-m1
Este projeto mostra como instalar o Metasploitable 2 — uma máquina vulnerável usada em testes de pentest — no macOS com chip Apple Silicon (M1), utilizando o virtualizador **UTM**.

# Guia de Instalação do Metasploitable-2 no Mac usando UTM

## Requisitos

- **UTM** — emulador e host de máquina virtual para iOS/macOS  
- **Homebrew** — gerenciador de pacotes para macOS/Linux

---

## Passo 1: Instalar o UTM

1. Acesse: [https://docs.getutm.app/installation/macos/](https://docs.getutm.app/installation/macos/)  
2. Clique em **Download from GitHub** e instale o pacote.

---

## Passo 2: Instalar o Homebrew

Abra o Terminal e execute:

```
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Após a instalação, siga as instruções finais no Terminal, por exemplo:
```
echo >> /Users/seu_usuario/.zprofile
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> /Users/seu_usuario/.zprofile
eval "$(/opt/homebrew/bin/brew shellenv)"
```
Verifique se está tudo ok com:
```
brew doctor
```
Deve aparecer: Your system is ready to brew.

## Passo 3: Baixar e preparar o Metasploitable-2
Baixe o Metasploitable-2 em: https://sourceforge.net/projects/metasploitable/

Descompacte o arquivo .zip baixado.

caso não tenha algum software no mac para descompactar o arquivp.zip baixe o The Unarchiver na App Store.

Instale o qemu usando Homebrew:
```
brew install qemu
```
Navegue até a pasta do Metasploitable descompactado, por exemplo:
```
cd ~/Downloads/Metasploitable2-Linux
```
Converta o arquivo .vmdk para .qcow2:
```
qemu-img convert -O qcow2 Metasploitable.vmdk Metasploitable.qcow2
```
## Passo 4: Criar a VM no UTM

1. Abra o UTM e clique no botão + para criar uma nova VM.

2. Selecione Emulate.

3. Escolha Other no sistema operacional e, na próxima tela, None.

4. Ajuste a memória para 1024 MB (ou deixe o padrão).

5. Avance até a tela Summary.

6. Clique em Open VM Settings e depois em Save.

7. Na janela de configurações:

   Renomeie a VM para Metasploitable-2 (sem espaços).

   No menu lateral, selecione QEMU e desmarque UEFI Boot.

   Em Drives, delete o IDE Drive.

   Clique em New Drive > Import e selecione o arquivo .qcow2 criado.

8. Salve as configurações e inicie a VM.

## Passo 5: Login no Metasploitable-2
Quando a máquina iniciar, use:

Usuário: msfadmin

Senha: msfadmin















