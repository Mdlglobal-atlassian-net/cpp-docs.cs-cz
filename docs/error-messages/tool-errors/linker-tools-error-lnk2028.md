---
title: Chyba linkerů LNK2028
ms.date: 11/04/2016
f1_keywords:
- LNK2028
helpviewer_keywords:
- LNK2028
ms.assetid: e2b03293-6066-464d-a050-ce747bcf7f0e
ms.openlocfilehash: ef9e3eae655a4fbee1c3da74f6036e5fb22434b1
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194613"
---
# <a name="linker-tools-error-lnk2028"></a>Chyba linkerů LNK2028

"*exported_function*" (*decorated_name*), na které odkazuje funkce "*function_containing_function_call*" (*decorated_name*)

## <a name="remarks"></a>Poznámky

Při pokusu o import nativní funkce do čistě image mějte na paměti, že konvence implicitního volání se liší mezi nativním a čistým kompilací.

Možnost **/clr: Pure** Compiler je v aplikaci visual Studio 2015 zastaralá a není podporovaná v rámci sady visual Studio 2017.

## <a name="example"></a>Příklad

Tato ukázka kódu vygeneruje komponentu s exportovanou, nativní funkcí, jejíž konvence volání je implicitně [__cdecl](../../cpp/cdecl.md).

```cpp
// LNK2028.cpp
// compile with: /LD
__declspec(dllexport) int func() {
   return 3;
}
```

## <a name="example"></a>Příklad

Následující ukázka vytvoří čistě klienta, který využívá nativní funkci. Nicméně konvence volání v rámci **/clr: Pure** je [__clrcall](../../cpp/clrcall.md). Následující ukázka generuje LINKERŮ LNK2028.

```cpp
// LNK2028_b.cpp
// compile with: /clr:pure lnk2028.lib
// LNK2028 expected
int func();

int main() {
   return func();
}
```
