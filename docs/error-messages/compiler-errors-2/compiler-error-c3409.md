---
title: "C3409 Chyba kompilátoru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3409
dev_langs: C++
helpviewer_keywords: C3409
ms.assetid: e372d9fa-230c-4b28-b6d3-6ad81ccf9dbb
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 083c71cdaa1cb3fe1959ce59e16e3d1e6949159d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3409"></a>C3409 chyby kompilátoru
není povolen prázdný atribut bloku  
  
 Hranaté závorky měla interpretovat kompilátoru jako [atribut](../../windows/cpp-attributes-reference.md) nebyly nalezeny bloku, ale žádné atributy.  
  
 Kompilátor může generovat tuto chybu, pokud použijete hranaté závorky jako součást definice výrazu lambda. K této chybě dojde, když kompilátor nemůže určit, jestli jsou hranaté závorky součástí definice výrazu lambda nebo bloku atribut. Další informace o výrazy lambda najdete v tématu [výrazy Lambda](../../cpp/lambda-expressions-in-cpp.md).  
  
### <a name="to-correct-this-error"></a>Oprava této chyby  
  
1.  Pokud jsou hranaté závorky součástí bloku atribut:  
  
    1.  Zadejte jeden nebo více atributů v bloku atribut.  
  
    2.  Odeberte atribut bloku.  
  
2.  Pokud jsou hranaté závorky část výrazu lambda:  
  
    1.  Ujistěte se, že výrazu lambda dodržuje platné syntaxe pravidla.  
  
         Další informace o syntaxe výrazu lambda najdete v tématu [syntaxe výrazu Lambda](../../cpp/lambda-expression-syntax.md).  
  
    2.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří C3409.  
  
```  
// C3409.cpp  
// compile with: /c  
#include <windows.h>  
[]   // C3409  
class a {};  
  
// OK  
[object, uuid("00000000-0000-0000-0000-000000000000")]  
__interface x {};  
  
[coclass, uuid("00000000-0000-0000-0000-000000000001")]  
class b : public x {};  
```  
  
## <a name="example"></a>Příklad  
 Následující příklad generuje C3409, protože používá výrazu lambda `mutable` specifikace, ale neposkytuje seznam parametrů. Kompilátor nemůže určit, jestli jsou hranaté závorky součástí definice výrazu lambda nebo bloku atribut.  
  
```  
// C3409b.cpp  
  
int main()  
{  
   [] mutable {}();  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [atribut](../../windows/cpp-attributes-reference.md)   
 [Lambda – výrazy](../../cpp/lambda-expressions-in-cpp.md)   
 [Syntaxe výrazu lambda](../../cpp/lambda-expression-syntax.md)