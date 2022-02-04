# Overview of Google Cloud Platform
A certificação foi desenvolida para pessoas que criam, deploy e gerenciam aplicações e infraestrutura na GCP. Trabalhar com Cloud Console, Cloud Shell e Cloud SDK.
 Os objetivos do exame irão avaliar:
  * Planejamento de uma solução cloud usando um ou mais serviços do GCP
  * Criar um ambiente em cloud para uma organização
  * Deploy de aplicações e infraestrutura
  * Usar monitoramentos e logs para garatir disponibilidade de soluções cloud
  * Configurar o gerenciamento de identitade, controle de acesso e outras medidas de segurança. 

Os objetivos estão definidos em https://cloud.google.com/certification/guides/cloud-engineer/

## Computação Servless
 Dois tipos de servless são fornecidos pelo GCP:
  * App Engine - utilizado por aplicações e containers que executam por um periodo longo de tempo ,al como website, sistemas de ponto de venda ou aplicações de negócio
  customizadas
  * Cloud Functions - executa em resposta a um evento ,al como enviar um arquivo ou adicinoar uma mensagem na fila, por curtos periodos de tempo. 24h de tempo máximo.

## Armazenamento
 Nuvens publicas oferecem os seguintes tipos:
  * Object Storage
  * File Storage
  * Block Storage
  * Caches

### Object Storage
É um sistema que gerencia o uso de armazenamento de objetos ou blobs.
Normalmente objetos são arquivos, mas não em armazenamento de arquivos convencionais. Objetos são armazenados dentro de buckets. Cada um endereçado por uma URL. Não possuem
limite de espaço em disco anexo ao servidor. Múltiplas cópias são armazenadas para melhorar a disponibilidade e durabilidade. Em alguns casos, armazenados em regiões diferentes.

### File Storage
Provém um sistema hierarquico de armazenamento para arquivos. Compartilhamento de rede dos arquivos. GCP tem o Cloud Filestore, basicamente é um NFS.
Utlizada por aplicações que necessitam um sistema operacional para acessar os arquivos. Ele desacopla o arquivos de uma VM especifica. O sistema de artquivos é um diretório, e ele existe independentemente de VM ou aplicação.

### Block Storage
Se armazenamentos de discos anexos a VM.

### Caches
Dados armazenados em memória e de rápido acesso. O tempo para acesso ao dado é chamado de latência. Dados armazenados em cache tem latência de submilisegundos.
