# Monte a sua aplicação!
Há um AKS disponível em RG-CloudSec-FIAP\AKSFIAPCloudSec00x.

Dentro deste AKS, há 2 NodesPool: nodepool1 e aplicativos

Questões:
<BR>(a) Crie um _Namespace_ para a sua aplicação com o seu RM **( +4 ptns)**
<BR>(b) Com base no seu _namespace_, no login server do seu ACR e no tag do seu repositório, suba a aplicação (adapte o arquivo Deployment.yaml de acordo com suas necessidades) **( +4 pnts)**
<BR>(c) Publique e teste a sua aplicação (acesso HTTP ou HTTPS) **( +2 Pnts)**
<BR>(**ATENÇÃO**) Criação de recursos adicionais, a partir do momento que a prova estiver aberta: 20/ago/26 - 18:45 (ex, ACR, AKS, VM, etc) **( -1 Pnt por recurso criado)**


Se sua aplicação de votação (ou outra que achar necessário) estiver publicada no seu ACR criado de maneira independente, vc precisará vincular este ACR ao AKS.
<BR>Se ainda não tiver feito, mude o repositório da sua aplicação (provavelmente Azure-Vote) para o valor do seu RM


Observações e dicas:
- Se a sua aplicação não estiver no repositório do ACR [CloudsecFiaplss001], você já deve ter criado seu próprio ACR ou jogar a aplicação para o [CloudsecFiaplss001]. 
- Se estiver trazendo a sua aplicação de outro ACR, não se esqueça de atualizar o AKS com o seu Container Registry.
- Você precisará usar comandos da Azure (az) e de Kubernetes (kubectl) para que fique mais fácil.
- Não precisa criar um novo AKS nem apagar o AKS existente. Os nodes já estão configurados para receber a aplicação (cuidado para não ser penalizado na criação de recursos).
- Use seu agente preferido de IA para ajudar nestas questões. Principalmente quando tiver dúvidas sobre a linha de comando correta.

Código para o deploy do seu repositório no AKLjjj
`Deployment.yaml`
```

apiVersion: apps/v1
kind: Deployment
metadata:
  name: app-seurm
  namespace: appns-seurm
spec:
  replicas: 1
  selector:
    matchLabels:
      app: app-a
  template:
    metadata:
      labels:
        app: app-a
    spec:
      nodeSelector:
        agentpool: apps
      containers:
      - name: app-a
        image: (Seu ACR ou ACR Padrão).azurecr.io/repositorio:tag
        ports:
        - containerPort: 80
```
