---
title: do-while – příkaz (C)
ms.date: 11/04/2016
f1_keywords:
- do
helpviewer_keywords:
- do-while keyword [C]
ms.assetid: f2ac20a6-10c7-4a08-b5e3-c3b3639dbeaf
ms.openlocfilehash: 3658fe7635ad77db6d6e08ff9d7c30e29d665721
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438585"
---
# <a name="do-while-statement-c"></a>do-while – příkaz (C)

Příkaz *do-while* umožňuje opakovat příkaz nebo složený příkaz, dokud se zadaný výraz nevrátí na hodnotu NEPRAVDA.

## <a name="syntax"></a>Syntaxe

*příkaz iterace*: &nbsp;&nbsp;&nbsp;&nbsp;**do***příkazu into* **(** *výraz* **);**

*Výraz* v příkazu do *-while* je vyhodnocen po provedení tohoto textu smyčky. Proto je tělo smyčky vždy provedeno alespoň jednou.

*Výraz* musí být aritmetického typu nebo typu ukazatele. Provádění pokračuje následujícím způsobem:

1. Tělo příkazu je spuštěno.

1. Dále je vyhodnocen *výraz* . Pokud má *výraz* hodnotu false, příkaz do *-while* se ukončí a řízení projde dalšímu příkazu v programu. Pokud je *výraz* true (nenulový), proces se opakuje, počínaje krokem 1.

Příkaz *do-while* může také skončit při spuštění příkazu **Break**, **goto**nebo **return** v těle příkazu.

Toto je příklad příkazu *do-while* :

```C
do
{
    y = f( x );
    x--;
} while ( x > 0 );
```

V tomto příkazu into *-while* jsou spouštěny dva příkazy `y = f( x );` a `x--;` bez ohledu na počáteční hodnotu `x`. Pak se vyhodnotí `x > 0`. Pokud je `x` větší než 0, tělo příkazu se provede znovu a `x > 0` se znovu vyhodnotí. Tělo příkazu se provede opakovaně, dokud `x` zůstane větší než 0. Provedení příkazu *do-while* končí, když `x` nabývá 0 nebo záporné. Tělo smyčky se provede aspoň jednou.

## <a name="see-also"></a>Viz také

[do-while – příkaz (C++)](../cpp/do-while-statement-cpp.md)
