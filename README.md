## Azure Container Apps で  Docker イメージや koを管理する

### Azure セッティング
```sh
az account list
 az account set -s YOURID
```

### リソースグループの追加
```sh
az acr create     --resource-group <resourseGroupyName>   --name resistrysample     --sku basic     --admin-enabled true
az acr login --name <azureContainerRegistryName>
```

### ログインサーバの取得
```sh
az acr list --resource-group container-sample  --query "[]
.{acrLoginServer:loginServer}" --output table
```
```
// 出力
```sh
AcrLoginServer
-------------------------
resistrysample.azurecr.io
```

### ルートのDockerfileを aaa(本当はよくない名前)をつけてbuild
```sh
docker build -t resistrysample.azurecr.io/aaa:latest .
```


### imageをpushする
```sh
docker push resistrysample.azurecr.io/aaa:latest
```

### リポジトリのイメージ名を取得
```sh
az acr repository list     --name resistrysample      --output table
```

![image](https://github.com/rensawamo/aca/assets/106803080/459f5f21-e998-43c2-a7dd-b25b787ffb18)
