---
title: "Upozornění linkerů Lnk4217 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4217
dev_langs: C++
helpviewer_keywords: LNK4217
ms.assetid: 280dc03e-5933-4e8d-bb8c-891fbe788738
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 09c984d7675c73bdf225bae7d3014f81153d20e2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="linker-tools-warning-lnk4217"></a>Upozornění linkerů LNK4217
místně definované symbol symbol importovat ve funkci 'function'.  
  
 [deklarace __declspec(dllimport)](../../cpp/dllexport-dllimport.md) byl zadán pro symbol, i když symbol je definován místně. Odeberte `__declspec` modifikátor vyřešit toto upozornění.  
  
 `symbol`je název symbol, který je definován v rámci bitovou kopii. `function`je funkce, která je import symbolu.  
  
 Toto upozornění se nezobrazí, když zkompilujete pomocí možnosti [/CLR](../../build/reference/clr-common-language-runtime-compilation.md).  
  
 LNK4217 může také nastat, pokud se pokusíte propojení dvou moduly společně, když místo toho by měla zkompilujete druhý modul s knihovnou import modulu první.  
  
```  
// LNK4217.cpp  
// compile with: /LD  
#include "windows.h"  
__declspec(dllexport) void func(unsigned short*) {}  
```  
  
 A pak  
  
```  
// LNK4217b.cpp  
// compile with: /c  
#include "windows.h"  
__declspec(dllexport) void func(unsigned short*) {}  
```  
  
 Při pokusu o propojení těchto dvou modulů mít za následek LNK4217, zkompilovat druhý ukázkový s knihovnou import vzorku první vyřešit.