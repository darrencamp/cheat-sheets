---
tags:
  - macos
---

# Table of contents

## installing powershell
It works on the mac install via  `brew upgrade powershell --cask`

### installing sql server powershell module in powershell on the mac
should be able to install a module once in the shell, refer https://www.powershellgallery.com/packages/SqlServer/21.1.18256
`Install-Module -Name SqlServer -RequiredVersion 21.1.18256`


## installing sqlserver tools 
```
brew tap microsoft/mssql-release https://github.com/Microsoft/homebrew-mssql-release
brew update
brew install mssql-tools
```

## find listening on a given port
```bash
sudo lsof -i -P | grep LISTEN | grep :$PORT
```

## kill process
```bash
sudo kill -9 <PID>
```

# metrics
ie things like temperature, fan speed etc
```bash
sudo powermetrics --samplers smc

to display CPU die temperature
sudo powermetrics --samplers smc | grep -i "CPU die temperature"
```

