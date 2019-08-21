---
title: Upozornění kompilátoru C4687
ms.date: 11/04/2016
f1_keywords:
- C4687
helpviewer_keywords:
- C4687
ms.assetid: 2f28e0b1-7358-4c88-bd70-aad8f0aa004c
ms.openlocfilehash: 83f5c535f9cf252783110838c181c88c8b0096ee
ms.sourcegitcommit: 9d4ffb8e6e0d70520a1e1a77805785878d445b8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/20/2019
ms.locfileid: "69631599"
---
# <a name="compiler-warning-c4687"></a>Upozornění kompilátoru C4687

> '*Class*': zapečetěná abstraktní třída nemůže implementovat rozhraní '*Interface*'

## <a name="remarks"></a>Poznámky

Zapečetěný abstraktní typ je obvykle vhodný pouze pro uchovávání statických členských funkcí.

Další informace naleznete v tématu [abstract](../../extensions/abstract-cpp-component-extensions.md) a [sealed](../../extensions/sealed-cpp-component-extensions.md).

C4687 je ve výchozím nastavení vydáno jako chyba. C4687 můžete potlačit pomocí direktivy pragma [Warning](../../preprocessor/warning.md) . Pokud jste si jisti, že chcete implementovat rozhraní v zapečetěném abstraktním typu, můžete potlačit C4687.

## <a name="example"></a>Příklad

Následující ukázka generuje C4687.

```cpp
// C4687.cpp
// compile with: /clr /c
interface class A {};

ref struct B sealed abstract : A {};   // C4687
ref struct C sealed : A {};   // OK
ref struct D abstract : A {};   // OK
```
