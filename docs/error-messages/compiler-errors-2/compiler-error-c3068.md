---
title: C3068 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3068
dev_langs:
- C++
helpviewer_keywords:
- C3068
ms.assetid: 613e3447-b4a8-4268-a661-297bed63ccdf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8f378a60c79defed4fb1738515ca5b65b2851056
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256552"
---
# <a name="compiler-error-c3068"></a>C3068 chyby kompilátoru
'function': 'holé' funkce nesmí obsahovat objekty, které by vyžadovaly unwinding, pokud došlo k výjimce C++  
  
 Kompilátor nebylo možné provést na uvolnění zásobníku [holé](../../cpp/naked-cpp.md) funkce, která došlo k výjimce, protože dočasný objekt byl vytvořen v funkci a zpracovávání výjimek v jazyce C++ ([/EHsc](../../build/reference/eh-exception-handling-model.md)) byl zadán.  
  
 Pokud chcete tuto chybu vyřešit, proveďte alespoň jednu z následujících:  
  
-   Nejde kompilovat s /EHsc.  
  
-   Neoznačujte funkce jako `naked`.  
  
-   Nevytvářejte dočasný objekt ve funkci.  
  
 Pokud funkci vytvoří dočasný objekt v zásobníku, pokud funkce vyvolá výjimku, a pokud je povoleno zpracovávání výjimek v jazyce C++, kompilátor bude vyčištění zásobníku Pokud je vyvolána výjimka.  
  
 Pokud je vyvolána výjimka, kompilátoru generovaného kódu, názvem prologu a epilogu, které nejsou součástí holé funkce, je spustit pro funkci.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3068:  
  
```  
// C3068.cpp  
// compile with: /EHsc  
// processor: x86  
class A {  
public:  
   A(){}  
   ~A(){}  
};  
  
void b(A){}  
  
__declspec(naked) void c() {  
   b(A());   // C3068   
};  
```