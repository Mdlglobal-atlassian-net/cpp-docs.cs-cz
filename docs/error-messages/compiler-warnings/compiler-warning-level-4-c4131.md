---
title: Kompilátoru (úroveň 4) upozornění C4131 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4131
dev_langs:
- C++
helpviewer_keywords:
- C4131
ms.assetid: 7903b3e1-454f-4be2-aa9b-230992f96a2d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6563d5faf3a9f050deb3cb7831c1a908739c8532
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33291987"
---
# <a name="compiler-warning-level-4-c4131"></a>C4131 kompilátoru upozornění (úroveň 4)
'function': používá deklarátor starého stylu  
  
 Deklarace zadaná funkce není v podobě prototypu.  
  
 Deklarace funkcí starého stylu mají být převedeny na prototypu formuláře.  
  
 Následující příklad ukazuje deklaraci starého funkce:  
  
```  
// C4131.c  
// compile with: /W4 /c  
void addrec( name, id ) // C4131 expected  
char *name;  
int id;  
{ }  
```  
  
 Následující příklad ukazuje prototypu formuláře:  
  
```  
void addrec( char *name, int id )  
{ }  
```