---
title: '#undef – direktiva (C++)'
ms.date: 11/04/2016
f1_keywords:
- '#undef'
helpviewer_keywords:
- '#undef directive'
- undef directive (#undef)
- preprocessor, directives
ms.assetid: 88900e0e-2c19-4a63-b681-f3d3133c24ca
ms.openlocfilehash: cb3a08165e41f336df0e141f50310f191cd83257
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537264"
---
# <a name="undef-directive-cc"></a>#undef – direktiva (C++)
Odebere (zruší definici) název dříve vytvořený pomocí direktivy `#define`.

## <a name="syntax"></a>Syntaxe

```
#undef
identifier
```

## <a name="remarks"></a>Poznámky

**#Undef** směrnice odstraní stávající definici *identifikátor*. V důsledku toho další výskyty tohoto *identifikátor* preprocesorem ignorovány. Chcete-li odebrat definici makra pomocí **#undef**, zadejte pouze *identifikátor* ; neudělujte seznam parametrů.

Můžete také použít **#undef** směrnice pro identifikátor, který nemá žádnou předchozí definici. Tím je zajištěno, že tento identifikátor není definován. Nahrazení makra není provedena v rámci **#undef** příkazy.

**#Undef** – direktiva je obvykle spojená s `#define` směrnice vytvoření oblasti ve zdrojovém programu, ve kterém má identifikátor zvláštní význam. Určitá funkce zdrojového programu například může použít konstanty manifestu pro definování hodnot specifických pro prostředí, které nemají vliv na zbytek programu. **#Undef** – direktiva funguje taky s `#if` směrnice pro řízení podmíněné kompilace zdrojového programu. Zobrazit [#if, #elif, #else a #endif](../preprocessor/hash-if-hash-elif-hash-else-and-hash-endif-directives-c-cpp.md) Další informace.

V následujícím příkladu **#undef** odebere direktiva definice Symbolické konstanty a makra. Je uveden pouze identifikátor makra.

```
#define WIDTH 80
#define ADD( X, Y ) ((X) + (Y))
.
.
.
#undef WIDTH
#undef ADD
```

**Specifické pro Microsoft**

Lze zrušit definici z příkazového řádku pomocí maker `/U` možnost, následované názvy maker mají být zrušeny. Účinek tohoto příkazu odpovídá sekvenci `#undef` *název makra* příkazy na začátku souboru.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Preprocesor – direktivy](../preprocessor/preprocessor-directives.md)