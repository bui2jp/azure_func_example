# dotnet core

https://docs.microsoft.com/ja-jp/azure/azure-functions/create-first-function-cli-csharp?tabs=azure-cli%2Cin-process

```
インプロセス
.NET Core 3.1
```

## version確認
```
% dotnet --version 
5.0.401
% dotnet --list-runtimes
% dotnet --list-sdks
```

```
% func -v 
4.0.3971
% dotnet --version 
6.0.101
```

## 関数の追加
extensions
```
$ func new --name HttpExample --template "HTTP trigger" --authlevel "anonymous"
```

## localで実行
```
$ func start
```

## azure へデプロイ


```
$ az group create --name AzureFunctionsQuickstart-rg --location japaneast

$ az storage account create --name stazfunc001 --location japaneast --resource-group AzureFunctionsQuickstart-rg --sku Standard_LRS

$ az functionapp create --resource-group AzureFunctionsQuickstart-rg --consumption-plan-location japaneast --runtime dotnet --functions-version 3 --name dotnet-func-start001 --storage-account stazfunc001

$ func azure functionapp publish dotnet-func-start001
```

FUNCTIONS_EXTENSION_VERSIONを変更する 
```
az functionapp config appsettings set --name dotnet-func-start001  \
--resource-group AzureFunctionsQuickstart-rg \
--settings FUNCTIONS_EXTENSION_VERSION=~4
```

```
az group delete --name AzureFunctionsQuickstart-rg
```