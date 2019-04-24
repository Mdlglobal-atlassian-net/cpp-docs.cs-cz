---
title: Chyba linkerů LNK2028
ms.date: 11/04/2016
f1_keywords:
- LNK2028
helpviewer_keywords:
- LNK2028
ms.assetid: e2b03293-6066-464d-a050-ce747bcf7f0e
ms.openlocfilehash: ed2dc1a95d4dd7c447b360da21b5046e20f79083
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298981"
---
# <a name="linker-tools-error-lnk2028"></a>Chyba linkerů LNK2028

"*exported_function*" (*decorated_name*) odkazovaný ve funkci "*function_containing_function_call*" (*decorated_name*)

## <a name="remarks"></a>Poznámky

Při pokusu o import nativní funkce do čistého bitové kopie, mějte na paměti, že implicitní konvence volání liší mezi nativní a čisté kompilace.

**/CLR: pure** – možnost kompilátoru je zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

## <a name="example"></a>Příklad

Tato ukázka kódu generuje komponentu s funkcí exportovaných, nativní, jejíž konvence volání je implicitně [__cdecl](../../cpp/cdecl.md).

```cpp
// LNK2028.cpp
// compile with: /LD
__declspec(dllexport) int func() {
   return 3;
}
```

## <a name="example"></a>Příklad

Následující příklad vytvoří čistě klienta, který využívá nativní funkce. Ale konvence volání v rámci **/CLR: pure** je [__clrcall](../../cpp/clrcall.md). Následující ukázka generuje LNK2028.

```cpp
// LNK2028_b.cpp
// compile with: /clr:pure lnk2028.lib
// LNK2028 expected
int func();

int main() {
   return func();
}
```