---
title: Upozornění kompilátoru C4687
ms.date: 11/04/2016
f1_keywords:
- C4687
helpviewer_keywords:
- C4687
ms.assetid: 2f28e0b1-7358-4c88-bd70-aad8f0aa004c
ms.openlocfilehash: 50551faf817f83d8a4af848a75af67ebe7004fe7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50635474"
---
# <a name="compiler-warning-c4687"></a>Upozornění kompilátoru C4687

'class': zapečetěná abstraktní třída nemůže implementovat rozhraní "rozhraní"

Zapečetěná, abstraktní typ je obvykle užitečná pouze k uložení statické členské funkce.

Další informace najdete v tématu [abstraktní](../../windows/abstract-cpp-component-extensions.md)a [zapečetěné](../../windows/sealed-cpp-component-extensions.md).

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