---
title: Kompilátoru (úroveň 1) upozornění C4167 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4167
dev_langs:
- C++
helpviewer_keywords:
- C4167
ms.assetid: 74a420bd-9371-4167-b1ee-74dd8680f97b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c72d6fd88b8c4797b2e352d6d30dbf797a23a00d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33280329"
---
# <a name="compiler-warning-level-1-c4167"></a>C4167 kompilátoru upozornění (úroveň 1)
funkce: k dispozici pouze jako vnitřní funkce  
  
 **#Pragma funkce** se pokusí vynutit kompilátoru pro použití konvenční volání funkce, které musí být použity v vnitřní formuláře. – Direktiva pragma se ignoruje.  
  
 Abyste se vyhnuli toto upozornění, odeberte **#pragma funkce**.  
  
## <a name="example"></a>Příklad  
  
```  
// C4167.cpp  
// compile with: /W1  
#include <malloc.h>  
#pragma function(_alloca )   // C4167: _alloca() is intrinsic only  
int main(){}  
```