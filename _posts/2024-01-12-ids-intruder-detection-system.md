O IDS (Sistemas de Detecção de Intruso) é uma ferramenta que emite alertas de ataque numa **Rede**.
Ele pode estar posicionado na **Rede**, ou até mesmo no **Host** que você está atacando.
Basicamente, quando alguém tenta interagir com algum serviço, ou realiza por exemplo uma varredura de portas, ele emite um alerta.
No entanto, ele realiza essas tarefas **baseado em regras configuradas pelo usuário**, assim como no caso do **Firewall**.

Uma ferramenta muito conhecida para realizar a função de **IDS**, é o **Snort**, diponível para Linux.

```shell
apt-get install snort
```

Após instalar, basta ir até a pasta do **Snort** no sistema: **/etc/snort/**
Existem vários arquivos dentro dessa pasta, o principal deles é o **snort.conf**, e na pasta **rules/** é onde encontramos as regras que serão aplicadas ao sistema.

Para executar o **Snort**, basta utilizar o seguinte comando:

```shell
snort -A fast -q -h 192.168.0.1/24 -c snort.conf
```

O comando acima salva a saída de alertas em /etc/snort/alert

ou

```shell
snort -A console -q -h 192.168.0.1/24 -c snort.conf
```

O comando acima, monitora em tempo real e joga a saída de alertas no terminal.

#### Exemplo de Regra Simples

```shell
alert tcp any any -> 192.168.0.11 any (msg: "Port   Scanning";sid:1000001;rev:001;)
```

**alert** = Ação que será executada
**tcp** = Protocolo
**any** = Endereço IP de Origem
**any** = Porta de Origem
**192.168.0.11** = Endereço IP de Destino
**any** = Porta de Destino
**(msg: ...)** = Opções

Monitora as conexões na porta 22 (Através da flag S, ou seja, flag **SYN**)
```sell
alert tcp any any -> 192.168.0.2 22 (msg: "Connection received at SSH Service";flag:S;sid:1000002;rev:001;)
```

Monitora o acesso ao arquivo **robots.txt** na porta 80.
```shell
alert tcp any any -> 192.168.0.2 80 (msg:"[File Access: robots.txt]";content:"robots.txt";sid:1000003;rev:001;)
```
