---
title: "Zastaralé (C/C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc-pragma.deprecated
- deprecated_CPP
dev_langs: C++
helpviewer_keywords:
- deprecated pragma
- pragmas, deprecated
ms.assetid: 9c046f12-7875-499a-8d5d-12f8642fed2d
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 7ee6f8c77c1596789fcb731833a1fb432e77d7e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="deprecated-cc"></a>zastaralé (C/C++)
**Zastaralé** – Direktiva pragma umožňuje znamenat, že funkce, typ nebo jakýkoli jiný identifikátor může být podporován budoucí verze nebo by měla být dále používán.  
> [!NOTE]
> Informace o C ++ 14 `[[deprecated]]` atribut a pokyny k použití, která atribut vs Microsoft declspec nebo – Direktiva pragma najdete v tématu [standardní atributy C++](../cpp/attributes2.md) atribut.
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma deprecated( identifier1 [,identifier2, ...] )  
```  
  
## <a name="remarks"></a>Poznámky  
 Když kompilátor zaznamená identifikátor určeného **zastaralé** – Direktiva pragma, vydá upozornění kompilátoru [C4995](../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md).   
  
 Názvy maker lze označit jako zastaralé. Umístěte název makra do uvozovek, jinak dojde k rozšíření makra.  
  
 Protože **zastaralé** – Direktiva pragma funguje na všechny odpovídající identifikátory a nevyžaduje podpisy v úvahu, není nejlepší možnost pro místo začne konkrétních verzí přetížených funkcí. Všechny odpovídající název funkce, která je uvedena do oboru aktivuje upozornění.

  Doporučujeme použít C ++ 14 `[[deprecated]]` atribut, pokud je to možné, místo **zastaralé** – Direktiva pragma. Microsoft specifické [__declspec(deprecated)](../cpp/deprecated-cpp.md) modifikátor deklarace je také vhodnější volbou v mnoha případech než **zastaralé** – Direktiva pragma. `[[deprecated]]` Atribut a `__declspec(deprecated)` modifikátor umožňují určit nepoužívané stavu pro určité formy přetížených funkcí. Diagnostické upozornění se zobrazí pouze na odkazy na konkrétní přetížené funkce atribut nebo modifikátor platí pro.  
  
## <a name="example"></a>Příklad  
  
```  
// pragma_directive_deprecated.cpp  
// compile with: /W3  
#include <stdio.h>  
void func1(void) {  
}  
  
void func2(void) {  
}  
  
int main() {  
   func1();  
   func2();  
   #pragma deprecated(func1, func2)  
   func1();   // C4995  
   func2();   // C4995  
}  
```  
  
 Následující příklad ukazuje, jakým způsobem označit třídu jako zastaralou:  
  
```  
// pragma_directive_deprecated2.cpp  
// compile with: /W3  
#pragma deprecated(X)  
class X {  // C4995  
public:  
   void f(){}  
};  
  
int main() {  
   X x;   // C4995  
}  
```  
  
## <a name="see-also"></a>Viz také  
 [Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)