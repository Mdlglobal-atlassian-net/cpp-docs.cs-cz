---
title: nullopt_t – struktura
ms.date: 08/04/2019
f1_keywords:
- optional/std::nullopt_t
- optional/std::nullopt
ms.openlocfilehash: 1f453a5d75de3f6dedb133d55c094a4f4274e08f
ms.sourcegitcommit: 16c0392fc8d96e814c3a40b0c5346d7389aeb525
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/12/2019
ms.locfileid: "68957047"
---
# <a name="nullopt_t-struct"></a>nullopt_t – struktura

Typ je jedinečný, prázdný typ, který se používá k označení volitelného objektu, neobsahuje hodnotu. [](optional-class.md) `nullopt_t`

Konstanta `nullopt` typu `nullopt_t` značí `optional` , že typ má Neinicializovaný stav. Dá se použít k inicializaci `optional` objektu nebo porovnání s jedním.

## <a name="syntax"></a>Syntaxe

```cpp
struct nullopt_t;
inline constexpr nullopt_t nullopt{ /*implementation-defined*/ };
```

## <a name="see-also"></a>Viz také:

[\<volitelné >](optional.md)\
[Volitelná třída](optional-class.md)
