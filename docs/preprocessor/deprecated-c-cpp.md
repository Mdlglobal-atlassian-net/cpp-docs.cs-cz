---
title: zastaralá direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.deprecated
- deprecated_CPP
helpviewer_keywords:
- deprecated pragma
- pragmas, deprecated
ms.assetid: 9c046f12-7875-499a-8d5d-12f8642fed2d
ms.openlocfilehash: 2e76d1c53cb900c108e2839a9aad17b330143a5d
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222400"
---
# <a name="deprecated-pragma"></a>zastaralá direktiva pragma

Zastaralá direktiva pragma vám umožní označit, že funkce, typ nebo jakýkoli jiný identifikátor již nemusí být v budoucí verzi podporován nebo by již neměl být použit.

> [!NOTE]
> Informace o atributu c++ `[[deprecated]]` 14 a pokyny k použití tohoto atributu místo modifikátoru společnosti Microsoft `__declspec(deprecated)` nebo **zastaralé** direktivy pragma naleznete v tématu [atributy v C++ ](../cpp/attributes.md).

## <a name="syntax"></a>Syntaxe

> **#pragma zastaralé (** *identifier1* [ **;** *identifier2* ...] **)**

## <a name="remarks"></a>Poznámky

Když kompilátor narazí na identifikátor určený zastaralou direktivou pragma, vydává upozornění kompilátoru [C4995](../error-messages/compiler-warnings/compiler-warning-level-3-c4995.md).

Názvy maker lze označit jako zastaralé. Umístěte název makra do uvozovek, jinak dojde k rozšíření makra.

Vzhledem k tomu, že zastaralá direktiva pragma funguje na všech shodných identifikátorech a nebere v úvahu signatury, není nejlepší možností pro zastaralé konkrétní verze přetížených funkcí. Libovolný odpovídající název funkce, která je uvedena v oboru, aktivuje upozornění.

Doporučujeme použít atribut c++ 14 `[[deprecated]]` , pokud je to možné, namísto **zastaralé** direktivy pragma. Modifikátor deklarace [__declspec (](../cpp/deprecated-cpp.md) nepoužívaného společností Microsoft) je také lepší volbou v mnoha případech, než je zastaralá direktiva pragma. `[[deprecated]]` Atribut a`__declspec(deprecated)` modifikátor umožňují zadat zastaralý stav pro konkrétní formy přetížených funkcí. Diagnostické upozornění se zobrazí pouze v odkazech na konkrétní přetíženou funkci, na kterou se atribut nebo modifikátor vztahuje.

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

## <a name="see-also"></a>Viz také:

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)