---
title: "Kompilátoru (úroveň 4) upozornění C4207 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4207
dev_langs: C++
helpviewer_keywords: C4207
ms.assetid: f4e09e3e-ac87-4489-8e3f-c8f76b82e721
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 31211fb7eb8d71bf214d41d5649cc91a92c9b7fb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4207"></a>C4207 kompilátoru upozornění (úroveň 4)
nestandardní rozšíření používané: rozšířené inicializátoru formuláře  
  
 Rozšíření Microsoft (/Ze), bude možné inicializovat nenastavenou velikostí pole `char` pomocí řetězce v rámci složené závorky.  
  
## <a name="example"></a>Příklad  
  
```  
// C4207.c  
// compile with: /W4  
char c[] = { 'a', 'b', "cdefg" }; // C4207  
  
int main()  
{  
}  
```  
  
 Takové inicializacích jsou neplatné v části kompatibility ANSI ([/Za](../../build/reference/za-ze-disable-language-extensions.md)).