---
title: Chyba kompilátoru C3533 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3533
dev_langs:
- C++
helpviewer_keywords:
- C3533
ms.assetid: a68b1ba5-466e-4190-a1a4-505ccfe548b7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6201f59e3ccefaa920f79f9b9889bd187fb2e0b0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042556"
---
# <a name="compiler-error-c3533"></a>Chyba kompilátoru C3533

'type': Parametr nemůže mít typ, který obsahuje nastavení auto.

Parametr metody nebo šablony se nedá deklarovat pomocí `auto` – klíčové slovo Pokud výchozí [/Zc: Auto](../../build/reference/zc-auto-deduce-variable-type.md) – možnost kompilátoru je v platnosti.

### <a name="to-correct-this-error"></a>Oprava této chyby

1. Odeberte `auto` – klíčové slovo z deklarace parametru.

## <a name="example"></a>Příklad

Následující příklad provede C3533, protože deklaruje parametr funkce se `auto` – klíčové slovo a je kompilován **/Zc: Auto**.

```
// C3533a.cpp
// Compile with /Zc:auto
void f(auto j) {} // C3533
```

## <a name="example"></a>Příklad

Následující příklad provede C3533 v režim C ++ 14, protože deklaruje parametr šablony s `auto` – klíčové slovo a je kompilován **/Zc: Auto**. (V C ++ 17, je to platnou definici šablony třídy s parametrem jedné šablony bez typu, jehož typ je odvozen.)

```
// C3533b.cpp
// Compile with /Zc:auto
template<auto T> class C {}; // C3533
```

## <a name="see-also"></a>Viz také

[Auto – klíčové slovo](../../cpp/auto-keyword.md)<br/>
[/Zc:auto (odvození typu proměnné)](../../build/reference/zc-auto-deduce-variable-type.md)
