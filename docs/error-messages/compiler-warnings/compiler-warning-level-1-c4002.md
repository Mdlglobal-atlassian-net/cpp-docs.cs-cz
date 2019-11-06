---
title: Upozornění kompilátoru (úroveň 1) C4002
ms.date: 11/04/2016
f1_keywords:
- C4002
helpviewer_keywords:
- C4002
ms.assetid: 6bda1dfe-e2e4-4771-9794-5a404c466dd5
ms.openlocfilehash: 6aac8285e3935bb0fb910b52a7dd813d0a708732
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627392"
---
# <a name="compiler-warning-level-1-c4002"></a>Upozornění kompilátoru (úroveň 1) C4002

moc velký počet skutečných parametrů pro makro Identifier

Počet skutečných parametrů v makru překračuje počet formálních parametrů v definici makra. Preprocesor shromáždí dodatečné parametry, ale během rozšíření makra je ignoruje.

C4002 se může vyskytnout, když nesprávně použije [makra variadické](../../preprocessor/variadic-macros.md).

Následující ukázka generuje C4002:

```cpp
// C4002.cpp
// compile with: /W1
#define test(a) (a)

int main() {
   int a = 1;
   int b = 2;
   a = test(a,b);   // C4002
   // try..
   a = test(a);
}
```

Tato chyba se může vygenerovat taky v důsledku práce s shodami s kompilátorem, která se dokončila pro Visual Studio .NET 2003: další čárky v makru už nejsou přijaté.

Kompilátor již nebude v makru přijímat nadbytečné čárky. Aby kód byl platný jak v jazyce Visual Studio .NET 2003, tak ve verzi Visual Studio .NET C++, odeberte nadbytečné čárky.

```cpp
// C4002b.cpp
// compile with: /W1
#define F(x,y)
int main()
{
   F(2,,,,,,3,,,,,,)   // C4002
   // Try the following line instead:
   // F(2,3)
}
```