---
title: C3290 Chyba kompilátoru | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3290
dev_langs:
- C++
helpviewer_keywords:
- C3290
ms.assetid: 0baf684b-1143-4953-ac99-a2fa267d8017
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bf65a35469ca978b0464c6f7275a6ac0e331da5d
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33256380"
---
# <a name="compiler-error-c3290"></a>C3290 chyby kompilátoru
'type': trivial vlastnost nemůže mít typ odkazu  
  
 Vlastnost byla deklarována nesprávně. Pokud deklarace trivial vlastnosti, kompilátor vytvoří proměnné, která se bude aktualizovat vlastnosti a není možné, že sledovací odkaz proměnné v třídě.  
  
 V tématu [vlastnost](../../windows/property-cpp-component-extensions.md) a [sledování Reference – operátor](../../windows/tracking-reference-operator-cpp-component-extensions.md) Další informace.  
  
## <a name="example"></a>Příklad  
 Následující ukázka generuje C3290.  
  
```  
// C3290.cpp  
// compile with: /clr /c  
ref struct R {};  
  
ref struct X {  
   R^ mr;  
  
   property R % y;   // C3290  
   property R ^ x;   // OK  
  
   // OK  
   property R% prop {  
      R% get() {   
         return *mr;   
      }  
  
      void set(R%) {}  
   }  
};  
  
int main() {  
   X x;  
   R% xp = x.prop;  
}  
```