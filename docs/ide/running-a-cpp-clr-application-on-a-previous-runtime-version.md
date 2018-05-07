---
title: Spuštění aplikace C++ - clr v předchozí verzi modulu Runtime | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- applications [C++], runtime version specified
- versions [C++]
- app.config files, runtime version specified
- compatibility [C++], runtime version specified
- backward compatibility [C++], runtime version specified
- application deployment [C++], runtime version specified
- common language runtime [C++], version specified
- deploying applications [C++], runtime version specified
ms.assetid: 940171b7-6937-4b14-8e87-c199e23f4f2e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4f8e76930eb9191d27085d92a9d3a678812715fc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="running-a-c-clr-application-on-a-previous-runtime-version"></a>Spuštění aplikace C++ /clr v předchozí verzi modulu runtime
Pokud není uvedeno jinak, aplikace C++ rozhraní .NET Framework je sestavena pro běh na běžné verzi modulu runtime (CLR) jazyk, kompilátor použije pro sestavení aplikace. Je však možné .exe aplikace, která je sestavená pro jednu verzi modulu runtime ke spuštění na jakoukoli jinou verzi, která poskytuje požadovanou funkci.  
  
 K tomu, zadejte obsahující informace o verzi modulu runtime v souboru app.config `supportedRuntime` značky.  
  
 V době běhu souboru app.config musí mít název ve tvaru *název_souboru.přípona*.config, kde *název_souboru.přípona* je název spustitelného souboru, který spouští aplikaci a musí být ve stejném adresáři jako spustitelný soubor. Například pokud vaše aplikace jmenuje TestApp.exe, soubor app.config by měl jmenovat TestApp.exe.config.  
  
 Pokud zadáte více než jednu verzi modulu runtime a spuštění aplikace na počítači, který má více než jedna verze nainstalované runtime, aplikace použije první verzi, která je zadána v konfiguračním souboru a je nainstalovaná.  
  
 Další informace najdete v tématu [postupy: Konfigurace aplikace pro cílové verze rozhraní .NET Framework](http://msdn.microsoft.com/en-us/5247b307-89ca-417b-8dd0-e8f9bd2f4717).  
  
 Ke spuštění na verze 1.0 nebo 1.1 verzi modulu CLR, aplikace, která je sestavena Visual C++ musí být zkompilovány kompilátoru pomocí [/CLR: initialAppDomain](../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="see-also"></a>Viz také  
 [Nasazení aplikací klasické pracovní plochy](../ide/deploying-native-desktop-applications-visual-cpp.md)