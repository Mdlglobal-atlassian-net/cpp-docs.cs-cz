---
title: Kompilátoru (úroveň 4) upozornění C4220 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4220
dev_langs:
- C++
helpviewer_keywords:
- C4220
ms.assetid: aba18868-825f-4763-9af6-3296406a80e4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f5a48bc836bbead8bc9004f797855fcc4c1baaf
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33294164"
---
# <a name="compiler-warning-level-4-c4220"></a>C4220 kompilátoru upozornění (úroveň 4)
vararg odpovídá zbývající parametry  
  
 V části rozšíření Microsoft výchozí (/Ze) odpovídá ukazatel na funkci ukazatel na funkci s podobné, ale proměnné, argumenty.  
  
## <a name="example"></a>Příklad  
  
```  
// C4220.c  
// compile with: /W4  
  
int ( *pFunc1) ( int a, ... );  
int ( *pFunc2) ( int a, int b);  
  
int main()  
{  
   if ( pFunc1 != pFunc2 ) {};  // C4220  
}  
```  
  
 Tyto ukazatele neodpovídají žádné pod kompatibility ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).