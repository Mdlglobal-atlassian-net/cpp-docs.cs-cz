---
title: Složené příkazy (bloky)
ms.date: 11/04/2016
f1_keywords:
- '}'
- '{'
helpviewer_keywords:
- blocks, about blocks
- compound statements
ms.assetid: 23855939-7430-498e-8936-0c70055ea701
ms.openlocfilehash: 60d7e88c5ccccac5a1d967a91c8a82dd954d9afc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337345"
---
# <a name="compound-statements-blocks"></a>Složené příkazy (bloky)

Složený příkaz se skládá z nuly nebo více příkazů uzavřených ve složených závorkách (**{ }**). Složený příkaz lze použít všude, kde je očekáván příkaz. Složené příkazy jsou často označovány za „bloky“.

## <a name="syntax"></a>Syntaxe

```
{ [ statement-list ] }
```

## <a name="remarks"></a>Poznámky

Následující příklad používá složený příkaz jako *část příkazu* **if** (podrobnosti o syntaxi naleznete v [příkazu if:](../cpp/if-else-statement-cpp.md)

```cpp
if( Amount > 100 )
{
    cout << "Amount was too large to handle\n";
    Alert();
}
else
{
    Balance -= Amount;
}
```

> [!NOTE]
> Vzhledem k tomu, že prohlášení je prohlášení, prohlášení může být jedním z příkazů v *seznamu příkazů*. Důsledkem toho mají názvy deklarované uvnitř složeného příkazu (ale nikoli explicitně deklarované jako statické) místní obor a v případě objektů i životnost. Podrobnosti o zpracování názvů s místním oborem naleznete v tématu [Obor.](../cpp/scope-visual-cpp.md)

## <a name="see-also"></a>Viz také

[Přehled příkazů jazyka C++](../cpp/overview-of-cpp-statements.md)
