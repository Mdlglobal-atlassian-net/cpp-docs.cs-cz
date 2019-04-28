---
title: conform
ms.date: 11/04/2016
f1_keywords:
- conform_CPP
- vc-pragma.conform
helpviewer_keywords:
- conform pragma
- forScope conform pragma
- pragmas, conform
ms.assetid: 71b3e174-c53c-4bfc-adf3-af39b1554191
ms.openlocfilehash: 35c3b06106779a9056f682ff76c6ed4b4ab1ab41
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366756"
---
# <a name="conform"></a>conform
**Specifické pro C++**

Určuje chování za běhu [/Zc: forscope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) – možnost kompilátoru.

## <a name="syntax"></a>Syntaxe

> **#pragma v souladu (** *název* [**, zobrazit** ] [**,** { **na** | **vypnout** }] [[**,** { **nabízených** | **pop** }] [**,** *identifikátor* ]] **)**

### <a name="parameters"></a>Parametry

*Jméno*<br/>
Určuje název možnosti kompilátoru, který má být upraven. Jediné platné *název* je `forScope`.

**show**<br/>
(Volitelné) Způsobí, že aktuální nastavení *název* (true nebo false), který se má zobrazit pomocí upozornění v průběhu kompilace. Například, `#pragma conform(forScope, show)`.

**on**, **off**<br/>
(Volitelné) Nastavení *název* k **na** umožňuje [/Zc: forscope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) – možnost kompilátoru. Výchozí hodnota je **vypnout**.

**push**<br/>
(Volitelné) Posune aktuální hodnotu *název* do zásobníku vnitřního kompilátoru. Pokud zadáte *identifikátor*, můžete zadat **na** nebo **vypnout** hodnota *název* doručí do zásobníku. Například, `#pragma conform(forScope, push, myname, on)`.

**pop**<br/>
(Volitelné) Nastaví hodnotu *název* hodnotu v horní části vnitřního zásobníku kompilátoru a potom vezme zásobníku. Pokud je zadaný identifikátor s **pop**, zásobníku bude odebrán, zpět, dokud najde záznam s *identifikátor*, které budou také být odebrány; aktuální hodnota pro *název* v Další záznam do zásobníku stane novou hodnotu *název*. Pokud zadáte **pop** s *identifikátor* , který není v záznamu v zásobníku, **pop** se ignoruje.

*identifier*<br/>
(Volitelné) Může být součástí **nabízených** nebo **pop** příkazu. Pokud *identifikátor* se používá, pak **na** nebo **vypnout** specifikátor je také možné.

## <a name="example"></a>Příklad

```cpp
// pragma_directive_conform.cpp
// compile with: /W1
// C4811 expected
#pragma conform(forScope, show)
#pragma conform(forScope, push, x, on)
#pragma conform(forScope, push, x1, off)
#pragma conform(forScope, push, x2, off)
#pragma conform(forScope, push, x3, off)
#pragma conform(forScope, show)
#pragma conform(forScope, pop, x1)
#pragma conform(forScope, show)

int main() {}
```

## <a name="see-also"></a>Viz také:

[Direktivy Pragma a klíčové slovo __Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)