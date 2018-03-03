---
title: "Upozornění linkerů Lnk4222 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- LNK4222
dev_langs:
- C++
helpviewer_keywords:
- LNK4222
ms.assetid: b7bb1794-41fb-4c83-b9b0-59c0d786a7da
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2a54c452a5df6f99260d6d01fbf4bb9f2f17b955
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4222"></a>Upozornění linkerů LNK4222
exportovaný symbol "značkou" by neměl přiřazené pořadí  
  
 Následující symboly nesmí exportovat podle pořadí:  
  
-   `DllCanUnloadNow`  
  
-   `DllGetClassObject`  
  
-   `DllGetClassFactoryFromClassString`  
  
-   `DllInstall`  
  
-   `DllRegisterServer`  
  
-   `DllRegisterServerEx`  
  
-   `DllUnregisterServer`  
  
 Tyto funkce jsou vždy umístěny podle názvu, pomocí `GetProcAddress`. Linkeru upozorňuje na to je druh exportu, protože to může způsobit větší bitové kopie. Toto může nastat, pokud rozsahu vaší ordinální exporty velká s relativně málo export. Například  
  
```  
EXPORTS  
   DllGetClassObject   @1  
   MyOtherAPI      @100  
```  
  
 bude vyžadovat, že 100 přihrádek v tabulce export adresa s 98 z nich jenom výplň (2-99). Na druhou stranu  
  
```  
EXPORTS  
   DllGetClassObject  
   MyOtherAPI      @100  
```  
  
 bude vyžadovat dva sloty. (Upozorňujeme, že můžete také exportovat pomocí [/EXPORT](../../build/reference/export-exports-a-function.md) – možnost linkeru.)