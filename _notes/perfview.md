---
layout: note
title: Using Perfview
category: DEBUG
---
To run Perfview from the command line to catch high processor load (e.g. 80%):
```powershell
perfview collect /nogui "/StopOnPerfCounter:Processor:% Processor Total:_Total>80" /acceptEula
```


