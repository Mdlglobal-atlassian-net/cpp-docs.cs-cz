---
title: (Úroveň 4) upozornění kompilátoru C4800
ms.date: 03/14/2019
f1_keywords:
- C4800
helpviewer_keywords:
- C4800
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
ms.openlocfilehash: 46418063625e16385497740a4f7e3d837e923156
ms.sourcegitcommit: a901c4acbfc80ca10663d37c09921f04c5b6dd17
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/18/2019
ms.locfileid: "58142584"
---
# <a name="compiler-warning-level-4-c4800"></a>(Úroveň 4) upozornění kompilátoru C4800

::: moniker range=">= vs-2019"
Visual Studio 2019 a novější:
> Implicitní převod z '*typ*' na typ bool. Ztráty informací je to možné
::: moniker-end

C4800 je upozornění úrovně 3 v sadě Visual Studio 2015 a starších verzích:
> "*typ*': vynucení hodnota logická hodnota"true"nebo"Nepravda"(upozornění ohledně výkonu)

Toto upozornění se vygeneruje, když hodnota je implicitně převeden na typ `bool`. Obvykle se tato zpráva způsoben přirazením `int` proměnné `bool` proměnné kde `int` proměnná obsahuje pouze hodnoty **true** a **false**a může být znova deklarovat jako typ `bool`. Pokud nelze přepsat výraz, který má použít typ `bool`, potom můžete přidat "`!=0`" na výraz, který poskytuje typ výrazu `bool`. Přetypování na typ výrazu `bool` nemá zakázat upozornění, která je záměrné.

::: moniker range=">= vs-2017"
Toto upozornění není aktivováno v sadě Visual Studio 2017.
::: moniker-end

::: moniker range=">= vs-2019"
Toto upozornění je vypnuto ve výchozím nastavení spouští v aplikaci Visual Studio 2019. Použití __/w__*n*__4800__ umožňující C4800 jako úroveň *n* upozornění, nebo [/Wall](../../build/reference/compiler-option-warning-level.md) povolit všechna upozornění, která ve výchozím nastavení jsou vypnuté. Další informace najdete v tématu [kompilátoru upozornění, že je vypnuto ve výchozím nastavení](../../preprocessor/compiler-warnings-that-are-off-by-default.md).
::: moniker-end

## <a name="example"></a>Příklad

Následující ukázka generuje C4800 a ukazuje, jak ho opravit:

```cpp
// C4800.cpp
// compile with: /W4 /w44800
int main() {
   int i = 0;

   // To fix, instead try:
   // bool i = 0;

   bool j = i;   // C4800
   j++;
}
```