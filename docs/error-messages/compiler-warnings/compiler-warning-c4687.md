---
title: Upozornění kompilátoru C4687
ms.date: 11/04/2016
f1_keywords:
- C4687
helpviewer_keywords:
- C4687
ms.assetid: 2f28e0b1-7358-4c88-bd70-aad8f0aa004c
ms.openlocfilehash: 1978e1a35ba5b5d59b5961a21378d8af6921d145
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "58778660"
---
# <a name="compiler-warning-c4687"></a>Upozornění kompilátoru C4687

'class': zapečetěná abstraktní třída nemůže implementovat rozhraní "rozhraní"

Zapečetěná, abstraktní typ je obvykle užitečná pouze k uložení statické členské funkce.

Další informace najdete v tématu [abstraktní](../../extensions/abstract-cpp-component-extensions.md)a [zapečetěné](../../extensions/sealed-cpp-component-extensions.md).

C4687 je vyvoláno jako chyba ve výchozím nastavení. Můžete potlačit C4687 s [upozornění](../../preprocessor/warning.md) direktivy pragma. Pokud jste si jisti, že chcete implementovat rozhraní v zapečetěná, abstraktní typ, můžete potlačit C4687.

## <a name="example"></a>Příklad

Následující ukázka generuje C4687.

```
// C4687.cpp
// compile with: /clr /c
interface class A {};

ref struct B sealed abstract : A {};   // C4687
ref struct C sealed : A {};   // OK
ref struct D abstract : A {};   // OK
```