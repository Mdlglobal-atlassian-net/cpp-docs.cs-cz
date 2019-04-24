---
title: Chyba linkerů LNK2031
ms.date: 11/04/2016
f1_keywords:
- LNK2031
helpviewer_keywords:
- LNK2031
ms.assetid: 18ed4b6e-3e75-443c-bbd8-2f6030dc89ee
ms.openlocfilehash: 003b9a58bfb08130f034530f59e2de27efa2ae8d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298916"
---
# <a name="linker-tools-error-lnk2031"></a>Chyba linkerů LNK2031

> nejde vygenerovat p/invoke pro "*function_declaration*" *decorated_name*; v metadatech chybí konvence volání

## <a name="remarks"></a>Poznámky

Při pokusu o import nativní funkce do čistého bitové kopie, mějte na paměti, že implicitní konvence volání liší mezi nativní a čisté kompilace. Další informace o čistě bitových kopiích naleznete v tématu [prázdná a ověřitelný kód (C++vyhodnocovací)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

**/CLR: pure** – možnost kompilátoru je zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

## <a name="example"></a>Příklad

Tato ukázka kódu generuje komponentu s funkcí exportovaných, nativní, jejíž konvence volání je implicitně [__cdecl](../../cpp/cdecl.md).

```cpp
// LNK2031.cpp
// compile with: /LD
extern "C" {
   __declspec(dllexport) int func() { return 3; }
};
```

## <a name="example"></a>Příklad

Následující příklad vytvoří čistě klienta, který využívá nativní funkce. Ale konvence volání v rámci **/CLR: pure** je [__clrcall](../../cpp/clrcall.md). Následující ukázka generuje LNK2031.

```cpp
// LNK2031_b.cpp
// compile with: /clr:pure LNK2031.lib
// LNK2031 expected
extern "C" int func();

int main() {
   return func();
}
```

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak využívat nativní funkce z čistě image. Všimněte si, explicitní **__cdecl** volání specifikátor konvence.

```cpp
// LNK2031_c.cpp
// compile with: /clr:pure LNK2031.lib
extern "C" int __cdecl func();

int main() {
   return func();
}
```