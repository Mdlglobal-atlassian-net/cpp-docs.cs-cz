---
title: Upozornění linkerů Lnk4222 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4222
dev_langs:
- C++
helpviewer_keywords:
- LNK4222
ms.assetid: b7bb1794-41fb-4c83-b9b0-59c0d786a7da
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 359af4c4d3b1079b2d56f108bff0ee1488ea71f9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33302146"
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