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
ms.openlocfilehash: 09348d061fde4cb09eb6eb351f146404f355e184
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80187788"
---
# <a name="__uuidof-operator"></a>__uuidof – operátor

**Specifické pro společnost Microsoft**

Získá identifikátor GUID připojený k výrazu.

## <a name="syntax"></a>Syntaxe

```
__uuidof (expression)
```

## <a name="remarks"></a>Poznámky

*Výraz* může být název typu, ukazatel, odkaz nebo pole tohoto typu, šablona specializovaná na tyto typy nebo proměnná těchto typů. Argument je platný, pokud jej kompilátor může použít k vyhledání připojeného identifikátoru GUID.

Zvláštní případ tohoto vnitřního objektu je v případě, že je jako argument zadán buď **0** , nebo null. V takovém případě **__uuidof** vrátí identifikátor GUID, který je tvořen nulami.

Pomocí tohoto klíčového slova je možné extrahovat identifikátor GUID připojený k:

- Objekt pomocí rozšířeného atributu [UUID](../cpp/uuid-cpp.md) .

- Blok knihovny vytvořený s atributem [Module](../windows/attributes/module-cpp.md) .

> [!NOTE]
> V sestavení pro ladění **__uuidof** vždy dynamicky inicializuje objekt (za běhu). V sestavení pro vydání je **__uuidof** možné staticky (v době kompilace) inicializovat objekt.

Z důvodu kompatibility s předchozími verzemi je **_uuidof** synonymem pro **__uuidof** , pokud je zadána možnost kompilátoru [/za \(Disable Language Extensions)](../build/reference/za-ze-disable-language-extensions.md) .

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

V případech, kdy už název knihovny není v oboru, můžete místo **__uuidof**použít `__LIBID_`. Příklad:

```cpp
StringFromCLSID(__LIBID_, &lpolestr);
```

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Výrazy s unárními operátory](../cpp/expressions-with-unary-operators.md)<br/>
[Klíčová slova](../cpp/keywords-cpp.md)
