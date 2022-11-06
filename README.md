# Malier
free mailer
sendEmail - Send email from a console near you!
Written by: priv3t3 <twitter@priv3t3>
// 
// 

-----------------
Instruá‰es de uso
-----------------

sendEmail-1.55 by priv3t3 <twitter@priv3t3>

Comando:  sendEmail -f ENDEREÄO [opá‰es]

  Necess†rio:
    -f ENDEREÄO               endereáo de quem est† enviando o email
    * Pelo menos um destinat†rio, via -t, -cc, ou -bcc
    * Corpo da mensagem, via -m, STDIN, ou -o message-file=FILE

  Comum:
    -t ENDEREÄO [ENDEREÄOS...] destinat†rio(s)
    -u "ASSUNTO"               assunto da mensagem
    -m "MENSAGEM"              corpo da mensagem
    -s SERVER[:PORT]           servidor smtp, default e' a porta localhost:25

  Opcional:
    -a   ARQ [ARQ...]           Arquivo(s) anexado
    -cc  ENDEREÄO [ENDEREÄO...] cc endereáos(s)
    -bcc ENDEREÄO [ENDEREÄO...] bcc endereáo(s)
    -xu  USUARIO                nome do usuario para autenticaá∆o
    -xp  SENHA                  senha para autenticaá∆o

  Extras:
    -b BINDADDR[:PORT]        endereáo do host local bind
    -l ARQLOG                 fazer LOG no arquivo indicado
    -v                        verbal, use v†rias vezes para grandes efeitos
    -q                        silencioso (n∆o ecoa saidas)
    -o NOME=VALOR             opá‰es avanáadas, para detalhes use: --help misc
        -o message-content-type=<auto|text|html>
        -o message-file=ARQUIVO      -o message-format=RAW
        -o message-header=HEADER     -o message-charset=CHARSET
        -o reply-to=ENDEREÄO         -o timeout=SEGUNDOS
        -o username=USUARIO          -o password=SENHA
        -o tls=<auto|yes|no>         -o fqdn=FQDN

  Help:
    --help                    informaá‰es gerais (que voce le agora)
    --help addressing         detalhes de endereáos e suas opá‰es
    --help message            detalhes do corpo da mensagem e suas opá‰es
    --help networking         detalhes -s, -b, etc
    --help output             detalhes de saidas e suas opá‰es
    --help misc               detalhes opá∆o -o, TLS, autent SMTP auth etc



---------------
Exemplos
---------------

Simples Email:
  sendEmail -f myaddress@isp.net \
            -t nogueira_jr@ig.com.br  \
            -s relay.isp.net     \
            -u "Teste email"      \
            -m "Ola, isso e' um teste de email."

Enviando para v†rias pessoas:
  sendEmail -f myaddress@isp.net \
            -t "Scott Thomas <scott@isp.net>" nogueira_jr@ig.com.br renee@isp.net \
            -s relay.isp.net     \
            -u "Teste email"      \
            -m "Ola, isso e' um teste de email."

Enviando para v†rias pessoas e enviando copias cc e bcc:
(existe diferentes formas de enviar para varios destinatarios, usando TO
mas voce pode usar CC e BCC para destinatarios tambem)
  sendEmail -f myaddress@isp.net \
            -t scott@isp.net;jason@isp.net;nogueira_jr@ig.com.br  \
            -cc jennifer@isp.net paul@isp.net jeremiah@isp.net \
            -bcc troy@isp.net miranda@isp.net jay@isp.net \
            -s relay.isp.net \
            -u "Teste email com copias cc e bcc" \
            -m "Ola, isso e' um teste de email."


Enviando para v†rias pessoas com v†rios anexos:
  sendEmail -f myaddress@isp.net \
            -t nogueira_jr@ig.com.br \
            -cc jennifer@isp.net paul@isp.net jeremiah@isp.net \
            -s relay.isp.net \
            -u "Teste email com c¢pias cc e bcc" \
            -m "Ola, isso e' um teste de email."
            -a /mnt/storage/document.sxw "/root/My Documents/Work Schedule.kwd"


Enviando um email com o conteudo de um arquivo no corpo da mensagem:
  cat /tmp/file.txt | sendEmail -f myaddress@isp.net \
                                -t nogueira_jr@ig.com.br \
                                -s relay.isp.net \
                                -u "Ola, isso e' um teste de email com anexo."
 

Enviando um email com o conteudo de um arquivo no corpo da mensagem (mÇtodo 2):
  sendEmail -f myaddress@isp.net \
            -t nogueira_jr@ig.com.br \
            -s relay.isp.net \
            -o message-file=/tmp/file.txt \
            -u "Ola, isso e' um teste de email com anexo."
 

Enviando um email HTML: (certifique-se que o arquivo tem <html> no in°cio)
  cat /tmp/file.html | sendEmail -f myaddress@isp.net \
                                 -t nogueira_jr@ig.com.br \
                                 -s relay.isp.net \
                                 -u "Ola, isso e' um teste de email com HTML."
 


