# General

Informações gerais para setup em uma máquina Windows 11 (default)


## Setup máquina

- Faça a instalação do AWS CLI V2, [clique aqui](https://awscli.amazonaws.com/AWSCLIV2.msi)
- Faça o setup de AWS Credentials (_short term credentials_), [clique aqui](https://docs.aws.amazon.com/cli/latest/userguide/cli-configure-files.html)
- Faça a instalação do OpenTofu usando o Powershell, [clique aqui](https://opentofu.org/docs/intro/install/standalone/), mas tem uns pulos do gato abaixo:

```powershell
# Aquele cat jump
Set-ExecutionPolicy -ExecutionPolicy RemoteSigned -Scope CurrentUser

# Download the installer script:
Invoke-WebRequest -outfile "install-opentofu.ps1" -uri "https://get.opentofu.org/install-opentofu.ps1"

# Run the installer com skip verify, sem dependencias adicionais neste momento
& .\install-opentofu.ps1 -installMethod standalone -skipVerify

# Remove the installer (se quiser)
Remove-Item install-opentofu.ps1
```


## Inicialização

Entre na pasta 'terraform' e rode o seguinte comando

```bash
tofu init
```

Agora ajuste o profile no arquivo [0-provider.tf](terraform/0-provider.tf)


## Planejamento e validação

Ainda na pasta 'terraform' rode os seguintes comando:

```bash
tofu validate
tofu plan
```


## Aplicação

Com as informações validadas, aplique no Cloud com o seguinte comando

```bash
tofu apply -auto-approve
```

## Done

Verifique as informações no seu console AWS!