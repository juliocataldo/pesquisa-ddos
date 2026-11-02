# pesquisa-ddos

Material de estudo sobre ataques de negação de serviço (DoS/DDoS) e análise de tráfego de rede com o Wireshark.

## O que tem aqui

| Arquivo | Descrição |
|---|---|
| `captura-loja.pcap` | Captura de tráfego **sintética** (gerada por script, não é tráfego real) de um servidor web durante um incidente de indisponibilidade. Cerca de 5,6 MB, com pacotes truncados nos primeiros 160 bytes. |
| `SHA256SUMS` | Soma de verificação do arquivo, para conferir a integridade do download. |

Todos os endereços IP pertencem aos blocos reservados para documentação (RFC 5737: `192.0.2.0/24`, `198.51.100.0/24` e `203.0.113.0/24`). Não há dados pessoais, de empresas ou de ambientes reais.

## Como usar

1. Baixe o arquivo `captura-loja.pcap`.
2. Confira a integridade. No PowerShell:

   ```powershell
   Get-FileHash .\captura-loja.pcap -Algorithm SHA256
   ```

   No Linux ou macOS: `sha256sum -c SHA256SUMS`.
3. Abra no [Wireshark](https://www.wireshark.org/) e investigue.

### Pontos de partida no Wireshark

- **Statistics → Capture File Properties**: total de pacotes e duração.
- **Statistics → I/O Graph**: volume de pacotes ao longo do tempo.
- **Statistics → Endpoints** e **Conversations**: quem fala com quem e quanto.
- [Display filters](https://wiki.wireshark.org/DisplayFilters): por exemplo `ip.addr == x.x.x.x`, `tcp.port == 80`, `udp.port == 53`, `tcp.flags.syn == 1 && tcp.flags.ack == 0`.

## Referências

- [Guia do usuário do Wireshark](https://www.wireshark.org/docs/wsug_html_chunked/)
- [Capturas de exemplo do Wireshark](https://wiki.wireshark.org/SampleCaptures)
- [What is a DDoS attack? (Cloudflare)](https://www.cloudflare.com/learning/ddos/what-is-a-ddos-attack/)
- [Understanding Denial-of-Service Attacks (CISA)](https://www.cisa.gov/news-events/news/understanding-denial-service-attacks)
- [MITRE ATT&CK: T1498 Network Denial of Service](https://attack.mitre.org/techniques/T1498/) e [T1499 Endpoint Denial of Service](https://attack.mitre.org/techniques/T1499/)
- [RFC 2827 / BCP 38: Network Ingress Filtering](https://www.rfc-editor.org/rfc/rfc2827)

## Ética e legislação

Use o conhecimento daqui apenas em ambientes próprios ou com autorização por escrito. No Brasil, invadir dispositivo ou derrubar serviço sem autorização pode configurar crime (Lei 12.737/2012).

## Autor

Julio Cataldo.
