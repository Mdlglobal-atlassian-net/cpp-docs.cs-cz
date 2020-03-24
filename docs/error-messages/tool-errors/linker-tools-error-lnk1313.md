---
title: Chyba linkerů LNK1313
ms.date: 11/04/2016
f1_keywords:
- LNK1313
helpviewer_keywords:
- LNK1313
ms.assetid: 5df0b72e-bb3f-428c-8d84-6084238f9827
ms.openlocfilehash: a2314f160dc6add45547082c7804ec5e2c8f2349
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194860"
---
# <a name="linker-tools-error-lnk1313"></a>Chyba linkerů LNK1313

> zjistil se modul IJW/Native. nejde propojit s čistými moduly.

## <a name="remarks"></a>Poznámky

Aktuální verze vizuálu C++ nepodporuje propojování nativních nebo smíšených spravovaných a nativních souborů. obj pomocí souborů. obj kompilovaných pomocí **/clr: Pure**.

Možnost **/clr: Pure** Compiler je v aplikaci visual Studio 2015 zastaralá a není podporovaná v rámci sady visual Studio 2017.

## <a name="example"></a>Příklad

```cpp
// LNK1313.cpp
// compile with: /c /clr:pure
// a pure module
int main() {}
```

## <a name="example"></a>Příklad

```cpp
// LNK1313_b.cpp
// compile with: /c /clr
// an IJW module
void test(){}
```

## <a name="example"></a>Příklad

Následující ukázka vygeneruje LINKERŮ LNK1313.

```cpp
// LNK1313_c.cpp
// compile with: /link LNK1313.obj LNK1313_b.obj
// LNK1313 warning expected
```
