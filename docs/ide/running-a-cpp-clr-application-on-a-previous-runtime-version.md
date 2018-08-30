---
title: Spuštění aplikace C++ - clr v předchozí verzi modulu Runtime | Dokumentace Microsoftu
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
ms.openlocfilehash: 20a20002397e285680927fe519e4eac7b68cc343
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216559"
---
# <a name="running-a-c-clr-application-on-a-previous-runtime-version"></a>Spuštění aplikace C++ /clr v předchozí verzi modulu runtime
Pokud není uvedeno jinak, aplikace v jazyce C++ rozhraní .NET Framework je určený pro spouštět verze společného běhového jazykového (CLR), kterou kompilátor používá k sestavení aplikace. Je však možné, aplikace .exe, pro kterou je vytvořena jedna verze modulu runtime pro spuštění na jakoukoli jinou verzi, která poskytuje požadovanou funkci.  
  
 Chcete-li to provést, zadejte soubor app.config, který obsahuje informace o verzi modulu runtime v `supportedRuntime` značky.  
  
 V době běhu souboru app.config musí mít název ve tvaru *název_souboru.přípona*.config, kde *název_souboru.přípona* je název spustitelného souboru, který spouští aplikaci, a musí být ve stejném adresáři jako spustitelný soubor. Například pokud vaše aplikace jmenuje TestApp.exe, soubor app.config by měl jmenovat TestApp.exe.config.  
  
 Pokud zadáte více než jedna verze modulu runtime a aplikace bude spuštěna na počítači, který má více než jedna verze modulu runtime nainstalovaný, aplikace použije první verzi zadané v konfiguračním souboru a je nainstalovaná.  
  
 Další informace najdete v tématu [postupy: Konfigurace aplikace pro cílení na určitou verzi rozhraní .NET Framework](https://msdn.microsoft.com/5247b307-89ca-417b-8dd0-e8f9bd2f4717).  
  
 Ke spuštění na verzi 1.0 nebo 1.1 verzi CLR, aplikace, která je vytvořená ve Visual C++ musí být zkompilován pomocí kompilátoru [/CLR: initialAppDomain](../build/reference/clr-common-language-runtime-compilation.md).  
  
## <a name="see-also"></a>Viz také  
 [Nasazení aplikací klasické pracovní plochy](../ide/deploying-native-desktop-applications-visual-cpp.md)