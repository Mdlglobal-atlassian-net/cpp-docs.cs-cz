---
title: __uuidof – operátor
ms.date: 10/10/2018
f1_keywords:
- __LIBID_cpp
- __uuidof_cpp
- __uuidof
- _uuidof
helpviewer_keywords:
- __uuidof keyword [C++]
- __LIBID_ keyword [C++]
ms.assetid: badfe709-809b-4b66-ad48-ee35039d25c6
ms.openlocfilehash: a14ef9043ec2196ff930a37d0eff95e90024d3d5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62244153"
---
# <a name="uuidof-operator"></a>__uuidof – operátor

**Microsoft Specific**

Získá identifikátor GUID připojený k výrazu.

## <a name="syntax"></a>Syntaxe

```
__uuidof (expression)
```

## <a name="remarks"></a>Poznámky

*Výraz* může být název typu, ukazatel, odkaz nebo pole tohoto typu, specializovaná šablona pro tyto typy nebo proměnná těchto typů. Argument je platný, pokud jej kompilátor může použít k vyhledání připojeného identifikátoru GUID.

Zvláštní případ je, když buď **0** nebo je jako argument zadána hodnota NULL. V takovém případě **__uuidof** vrátí identifikátor GUID, který je tvořen nulami.

Pomocí tohoto klíčového slova je možné extrahovat identifikátor GUID připojený k:

- Objekt podle [uuid](../cpp/uuid-cpp.md) rozšířeného atributu.

- Bloku knihovny vytvořenému s [modulu](../windows/attributes/module-cpp.md) atribut.

> [!NOTE]
> V sestavení pro ladění **__uuidof** vždy inicializuje objekt dynamicky (za běhu). V sestavení pro vydání **__uuidof** staticky (v době kompilace) inicializovat objekt.

Z důvodu kompatibility s předchozími verzemi **_uuidof** je synonymum pro **__uuidof** Pokud – možnost kompilátoru [/Za \(zakázat jazyková rozšíření)](../build/reference/za-ze-disable-language-extensions.md) je zadat.

## <a name="example"></a>Příklad

Následující kód (zkompilován s knihovnou ole32.lib) zobrazí identifikátor uuid vytvořeného bloku knihovny s atributem module:

```cpp
// expre_uuidof.cpp
// compile with: ole32.lib
#include "stdio.h"
#include "windows.h"

[emitidl];
[module(name="MyLib")];
[export]
struct stuff {
   int i;
};

int main() {
   LPOLESTR lpolestr;
   StringFromCLSID(__uuidof(MyLib), &lpolestr);
   wprintf_s(L"%s", lpolestr);
   CoTaskMemFree(lpolestr);
}
```

## <a name="comments"></a>Komentáře

V případech, kdy knihovnu s názvem je již v oboru, můžete použít `__LIBID_` místo **__uuidof**. Příklad:

```cpp
StringFromCLSID(__LIBID_, &lpolestr);
```

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)