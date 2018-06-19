---
title: Kompilátoru (úroveň 1) upozornění C4087 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4087
dev_langs:
- C++
helpviewer_keywords:
- C4087
ms.assetid: 546e4d57-5c8e-422c-8ef1-92657336dad5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5b9962abc29b94425f96c978f3dd7e8d3f7c251
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33278441"
---
# <a name="compiler-warning-level-1-c4087"></a>C4087 kompilátoru upozornění (úroveň 1)
'function': deklarovat s seznam parametrů, void.  
  
 Deklarace funkce nemá žádné formální parametry, ale má volání funkce skutečného parametry. Další parametry jsou předány podle konvence volání funkce.  
  
 Toto upozornění je pro kompilátor jazyka C.  
  
## <a name="example"></a>Příklad  
  
```  
// C4087.c  
// compile with: /W1  
int f1( void ) {  
}  
  
int main() {  
   f1( 10 );   // C4087  
}  
```