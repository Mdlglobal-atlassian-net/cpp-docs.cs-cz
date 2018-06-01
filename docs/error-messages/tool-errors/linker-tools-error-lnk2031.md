---
title: Chyba linkerů Lnk2031 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK2031
dev_langs:
- C++
helpviewer_keywords:
- LNK2031
ms.assetid: 18ed4b6e-3e75-443c-bbd8-2f6030dc89ee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d86ea6da8a73d9ba2427e9455c4fca87cd32dd2b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34703662"
---
# <a name="linker-tools-error-lnk2031"></a>Chyba linkerů LNK2031

> Nelze vygenerovat p/invoke pro "*function_declaration*" *decorated_name*; chybí v metadatech konvence volání

## <a name="remarks"></a>Poznámky

Při pokusu o import nativní funkce do čistého bitové kopie, nezapomeňte, že implicitní konvence volání liší mezi nativní a čistý kompilace. Další informace o čisté bitové kopie najdete v tématu [prázdná a ověřitelný kód (C + +/ CLI)](../../dotnet/pure-and-verifiable-code-cpp-cli.md).

**/CLR: pure** – možnost kompilátoru je zastaralé v sadě Visual Studio 2015 a nepodporované v Visual Studio 2017.

## <a name="example"></a>Příklad

Tato ukázka kódu generuje součást s funkce exportované, nativní, jejichž konvence volání je implicitně [__cdecl](../../cpp/cdecl.md).

```cpp
// LNK2031.cpp
// compile with: /LD
extern "C" {
   __declspec(dllexport) int func() { return 3; }
};
```

## <a name="example"></a>Příklad

Následující příklad vytvoří čistý klienta, který zpracovává nativní funkce. Ale konvence volání pod **/CLR: pure** je [__clrcall](../../cpp/clrcall.md). Následující ukázka generuje LNK2031.

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

Následující příklad ukazuje, jak využívat nativní funkce z čisté bitové kopie. Poznámka: explicitní **__cdecl** volání specifikátor konvence.

```cpp
// LNK2031_c.cpp
// compile with: /clr:pure LNK2031.lib
extern "C" int __cdecl func();

int main() {
   return func();
}
```