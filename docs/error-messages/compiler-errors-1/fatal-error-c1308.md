---
title: Závažná chyba C1308
ms.date: 11/04/2016
f1_keywords:
- C1308
helpviewer_keywords:
- C1308
ms.assetid: 46177997-069e-433a-8e20-93c846d78ffd
ms.openlocfilehash: 95e13a6914b5e02441f95dd2256532dbd1d718e5
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74747017"
---
# <a name="fatal-error-c1308"></a>Závažná chyba C1308

propojování sestavení není podporované.

A. netmodule je povolen jako vstup linkeru, ale sestavení není. Tato chyba se může vygenerovat, když se provede pokus o propojení sestavení zkompilovaného s `/clr:safe`.

Další informace naleznete v tématu [soubory. netmodule jako vstup linkeru](../../build/reference/netmodule-files-as-linker-input.md).

Následující ukázka generuje C1308:

```cpp
// C1308.cpp
// compile with: /clr:safe /LD
public ref class MyClass {
public:
   int i;
};
```

A potom

```cpp
// C1308b.cpp
// compile with: /clr /link C1308b.obj C1308.dll
// C1308 expected
#using "C1308.dll"
int main() {
   MyClass ^ my = gcnew MyClass();
}
```
