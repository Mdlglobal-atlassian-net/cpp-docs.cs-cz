---
title: "Kompilátoru (úroveň 1) upozornění C4096 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4096
dev_langs: C++
helpviewer_keywords: C4096
ms.assetid: abf3cca2-2f21-45d8-b025-6b513b00681e
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e6cc30547ffb29eeadb0fe377b1249de5c3df0c6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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