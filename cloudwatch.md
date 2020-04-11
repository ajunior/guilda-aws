# CloudWatch
Serviço de monitoramento para recursos da própria AWS, bem como das aplicações que o usuário roda por conta própria. Tanto recursos computacionais (Autoscaling groups, ELB, Route53 Health Checks) como de armazenamento disseminação de conteúdo (EBS, Storage Gateways e CloudFront) podem ser monitorados. Outros recursos que podem ser monitorados incluem SNS Topics, SQS Queues, Opsworks, além dos logs do próprio CLoudWatch e do consumo financeiro da conta na AWS.

## EC2
O monitoramente de uma instância de EC2 inclui CPU, Rede, Disco de armazenamento e Status Check.

```__Dica de prova:__``` O monitoramento da RAM pode ser customizado. Por padrão o intervalo de monitoramento de uma EC2 é de 5 minutos, mas isso pode ser configurado para intervalo de 1 (um) minuto, habilitando a opção de __monitoramento detalhado__. 

## Recuperando logs

O CloudWatch, por padrão, armazena os logs indefinidamente, mas esse tempo de retenção pode ser alterado a qualquer tempo, inclusive para qualquer Log Group.

Os logs podem ser consultados pela API __GetMetricStatistics__ da AWS ou usando ferramentas de terceiros, oferecidas pelos parceiros da AWS.

É possível recuperar dados de qualquer instância EC2 ou ELB depois de finalizada. 

## Granularidade

Depende do serviço da AWS que está sendo utilizado, por padrão a maioria das métricas usa 1 (um) minutos como intervalo padrão, mas em alguns serviços isso pode variar de 3 (três) a 5 (cinco) minutos.

```__Dica de prova:__``` Para as métricas customizáveis, o valor mínimo de granularidade que pode ser configurado é de 1 (um) minutos.

## Alarms

Pode-se criar alarmes para monitorar qualquer métrica do CloudWatch, desde a utilização de CPU de uma instância EC2 até a latência do ELB, entre outras. Um _threshold_ apropriado para a métrica deve ser configurado e o alarme é disparado, quando a métrica atinge o nível determinado, e uma ação (que também deve ser configurada) é executada. 

> É bem comum o uso de alarmes para notificar o usuário quando o consumo financeiro atinge um determinado valor.

## CloudWatch vs. CloudTrail vs. Config

- CloudWatch __monitora performance__.
- CloudTrail __monitora chamadas a API__ na plataforma da AWS.
- AWS Config __registra o estado do ambiente__ na AWS e pode notificar as mudanças.

## On Premise

CloudWatch não está restrito a monitoramento dos recursos próprios da AWS, pode ser usado _on premise_ também. Nesse caso, é necessário __baixar e instalar os agentes SSM e CloudWatch__.
