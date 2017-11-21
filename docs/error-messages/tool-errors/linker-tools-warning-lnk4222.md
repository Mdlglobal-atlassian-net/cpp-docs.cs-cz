---
title: "Upozornění linkerů Lnk4222 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4222
dev_langs: C++
helpviewer_keywords: LNK4222
ms.assetid: b7bb1794-41fb-4c83-b9b0-59c0d786a7da
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: a0074e71902a145df8c37b52a5a16295a2b1dfd2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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