---
title: Chyba kompilátoru C3268
ms.date: 11/04/2016
f1_keywords:
- C3268
helpviewer_keywords:
- C3268
ms.assetid: d74a630c-daea-4e29-9759-83efef7fb184
ms.openlocfilehash: 191456a1e290b568897ba76cd5bdccb8f83c310b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201458"
---
# <a name="compiler-error-c3268"></a>Chyba kompilátoru C3268

> '*Function*': Obecná funkce nebo členská funkce obecné třídy nemůže mít seznam parametrů proměnných

## <a name="remarks"></a>Poznámky

Možnosti **/clr: Pure** a **/clr: Safe** jsou zastaralé v aplikaci Visual Studio 2015 a nejsou podporovány v aplikaci Visual Studio 2017.

Další informace najdete v tématu [Obecné](../../extensions/generics-cpp-component-extensions.md) .

## <a name="example"></a>Příklad

Následující ukázka generuje C3268.

```cpp
// C3268.cpp
// compile with: /clr:pure /c
generic <class ItemType>
void Test(ItemType item, ...) {}   // C3268
// try the following line instead
// void Test(ItemType item) {}

generic <class ItemType2>
ref struct MyStruct { void Test(...){} };   // C3268
// try the following line instead
// ref struct MyStruct { void Test2(){} };   // OK
```
