---
title: "C3290 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C3290
dev_langs: C++
helpviewer_keywords: C3290
ms.assetid: 0baf684b-1143-4953-ac99-a2fa267d8017
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c3dceac5102936bbb86f5c103fb0c9240f5ee2d2
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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