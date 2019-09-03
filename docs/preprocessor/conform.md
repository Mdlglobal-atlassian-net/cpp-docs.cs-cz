---
title: conform – direktiva pragma
ms.date: 08/29/2019
f1_keywords:
- conform_CPP
- vc-pragma.conform
helpviewer_keywords:
- conform pragma
- forScope conform pragma
- pragmas, conform
ms.assetid: 71b3e174-c53c-4bfc-adf3-af39b1554191
ms.openlocfilehash: 816ff85bb19f549c6ea072073bd89fcd503545f2
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220495"
---
# <a name="conform-pragma"></a>conform – direktiva pragma

**C++Konkrétní**

Určuje chování při spuštění možnosti kompilátoru [/Zc: forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) .

## <a name="syntax"></a>Syntaxe

> **#pragma vyhovující (** *název* [ **, show** ] [ **,** { **on** | **off** }] [[ **,** { **push** | **POP** }] [ **,** *identifikátor* [ **,** { **on** **off}** ]  |  ] ] **)**

### <a name="parameters"></a>Parametry

*Jméno*\
Určuje název možnosti kompilátoru, která se má upravit. Jediným platným *názvem* je `forScope`.

**uvádí**\
Volitelné Způsobí, že se aktuální nastavení *názvu* (true nebo false) zobrazí prostřednictvím zprávy upozornění během kompilace. Například, `#pragma conform(forScope, show)`.

**zapnuto**, **vypnuto**\
Volitelné Nastavení *název* **na zapnuto** povolí možnost kompilátoru [/Zc: forScope](../build/reference/zc-forscope-force-conformance-in-for-loop-scope.md) . Výchozí hodnota je **off**.

**replik**\
Volitelné Posune aktuální hodnotu *názvu* do vnitřního zásobníku kompilátoru. Pokud zadáte *identifikátor*, můžete zadat hodnotu **on** nebo **off** pro *název* , který se má vložit do zásobníku. Například, `#pragma conform(forScope, push, myname, on)`.

**výstrah**\
Volitelné Nastaví hodnotu *názvu* na hodnotu v horní části interního zásobníku kompilátoru a pak dořadí zásobník. Pokud je identifikátor zadán s příkazem **POP**, zásobník bude odebrán zpět, dokud nenajde záznam s identifikátorem,který bude také odebrán; aktuální hodnota pro *název* v dalším záznamu zásobníku se stala novou hodnotou pro *název*. Pokud zadáte položku **POP** s *identifikátorem* , který není v záznamu v zásobníku, bude **bod POP** ignorován.

*RID*\
Volitelné Dá se zahrnout do příkazu **push** nebo **POP** . Pokud je použit *identifikátor* , lze také použít specifikátor **on** nebo **off** .

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

[Direktivy pragma a klíčové slovo __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
