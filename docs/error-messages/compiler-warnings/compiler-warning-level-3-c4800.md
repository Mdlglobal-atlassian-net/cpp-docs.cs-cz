---
title: Upozornění kompilátoru (úroveň 4) C4800
ms.date: 03/14/2019
f1_keywords:
- C4800
helpviewer_keywords:
- C4800
ms.assetid: 4f409799-a250-45ed-bb5f-657691b0d9f7
ms.openlocfilehash: 828b38aeb184741af284f2d7722017b24f6255a3
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198585"
---
# <a name="compiler-warning-level-4-c4800"></a>Upozornění kompilátoru (úroveň 4) C4800

::: moniker range=">= vs-2019"
Visual Studio 2019 a novější:
> Implicitní převod z*typu*na bool Možné ztráty informací
::: moniker-end

C4800 je upozornění úrovně 3 v aplikaci Visual Studio 2015 a starší:
> '*Type*': vynucení hodnoty bool ' true ' nebo ' false ' (upozornění na výkon)

Toto upozornění je generováno, pokud je hodnota implicitně převedena na typ `bool`. Obvykle tato zpráva je způsobena přiřazením `int` proměnných `bool` proměnných, kde `int` proměnná obsahuje pouze hodnoty **true** a **false**a lze ji deklarovat jako `bool`typu. Pokud nemůžete přepsat výraz pro použití typu `bool`, můžete přidat "`!=0`" do výrazu, který poskytuje typ výrazu `bool`. Přetypování výrazu na typ `bool` nezakáže upozornění, které je záměrné.

::: moniker range=">= vs-2017"
Toto upozornění není vygenerováno v aplikaci Visual Studio 2017.
::: moniker-end

::: moniker range=">= vs-2019"
Toto upozornění je ve výchozím nastavení vypnuto od sady Visual Studio 2019. Pomocí __/w__*n*__4800__ povolte C4800 jako upozornění na úrovni *n* , nebo [/Wall](../../build/reference/compiler-option-warning-level.md) pro povolení všech upozornění, která jsou ve výchozím nastavení vypnutá. Další informace najdete v tématu [Upozornění kompilátoru, která jsou ve výchozím nastavení vypnutá](../../preprocessor/compiler-warnings-that-are-off-by-default.md).
::: moniker-end

## <a name="example"></a>Příklad

Následující ukázka generuje C4800 a ukazuje, jak ji opravit:

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
