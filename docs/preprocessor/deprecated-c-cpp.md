---
title: Zastaralé (C/C++) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- vc-pragma.deprecated
- deprecated_CPP
dev_langs:
- C++
helpviewer_keywords:
- deprecated pragma
- pragmas, deprecated
ms.assetid: 9c046f12-7875-499a-8d5d-12f8642fed2d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d51ee23ab4e4be9cf24b913cb0c4ffa325a9bbf5
ms.sourcegitcommit: d4c803bd3a684d7951bf88dcecf1f14af43ae411
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/10/2018
ms.locfileid: "42466380"
---
# <a name="deprecated-cc"></a>zastaralé (C/C++)
**Zastaralé** – Direktiva pragma umožňuje určit, že funkce, typ nebo jakýkoli jiný identifikátor pravděpodobně nebude podporovat v budoucí verzi nebo by již nelze použít.  
> [!NOTE]
> Informace o C ++ 14 `[[deprecated]]` atribut a pokyny, kdy se má použít atribut vs Microsoft declspec nebo direktivy pragma naleznete v tématu [C++ standardní atributy](../cpp/attributes.md) atribut.
  
## <a name="syntax"></a>Syntaxe  
  
```  
#pragma deprecated( identifier1 [,identifier2, ...] )  
```  
  
## <a name="remarks"></a>Poznámky  
Když kompilátor narazí určený identifikátor **zastaralé** – Direktiva pragma, vydá upozornění kompilátoru [C4995](../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md).   
  
Názvy maker lze označit jako zastaralé. Umístěte název makra do uvozovek, jinak dojde k rozšíření makra.  
  
Vzhledem k tomu, **zastaralé** – Direktiva pragma lze použít na všechny odpovídající identifikátory a podpisů nebere účtu, není nejlepší možnosti pro ukončení podpory pro konkrétní verze přetížených funkcí. Žádné odpovídající název funkce, která je přeneseny do rozsahu se aktivuje upozornění.

Doporučujeme použít C ++ 14 `[[deprecated]]` atribut, pokud je to možné, namísto **zastaralé** direktivy pragma. Specifické pro Microsoft [__declspec(deprecated)](../cpp/deprecated-cpp.md) modifikátoru deklarace je také vhodnější použít v mnoha případech než **zastaralé** direktivy pragma. `[[deprecated]]` Atribut a `__declspec(deprecated)` modifikátor vám umožňují určit stav již nepoužívaných konkrétních podob přetížených funkcí. Diagnostické upozornění se zobrazí pouze na odkazy na konkrétní přetížení funkce atribut nebo modifikátor se vztahuje na.  
  
## <a name="example"></a>Příklad  
  
```cpp  
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
  
```cpp  
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