---
title: C2785 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2785
dev_langs:
- C++
helpviewer_keywords:
- C2785
ms.assetid: d8d13360-0d00-4815-8475-b49c7f0dc0f3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: dc0ca6235e0fd4bdd22330e807464e96280ae461
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c2785"></a>C2785 chyby kompilátoru
'declaration1' a 'declaration2' mají různé návratové typy  
  
 Návratový typ funkce specializace šablony se liší od návratový typ šablony primární funkce.  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Zkontrolujte všechny specializací šablony funkce konzistence.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C2785:  
  
```  
// C2785.cpp  
// compile with: /c  
template<class T> void f(T);  
  
template<> int f(int); // C2785  
template<> void f(int); // OK  
```