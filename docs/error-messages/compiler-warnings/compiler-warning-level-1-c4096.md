---
title: Kompilátoru (úroveň 1) upozornění C4096 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4096
dev_langs:
- C++
helpviewer_keywords:
- C4096
ms.assetid: abf3cca2-2f21-45d8-b025-6b513b00681e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3787ef5482841e33658e02371fa0f6d1682612ac
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-1-c4096"></a>C4096 kompilátoru upozornění (úroveň 1)
"a": rozhraní není rozhraní modelu COM; nebude vygenerované k IDL  
  
 Definice rozhraní, které opravu jako rozhraní modelu COM nebyl definován jako rozhraní modelu COM a nebude proto vygenerované IDL souboru.  
  
 V tématu [atributy rozhraní](../../windows/interface-attributes.md) pro seznam atributy, které indikují rozhraní je rozhraní modelu COM.  
  
 Následující ukázka generuje C4096:  
  
```  
// C4096.cpp  
// compile with: /W1 /LD  
#include "windows.h"  
[module(name="xx")];  
  
// [object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface a  
{  
};  
  
[coclass, uuid("00000000-0000-0000-0000-000000000002")]  
struct b : a  
{  
};   // C4096, remove coclass or uncomment object  
```