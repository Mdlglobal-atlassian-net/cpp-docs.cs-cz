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
ms.openlocfilehash: cd0e5daa2232f17a34bee2f0d8b9569e524fbf34
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80189556"
---
# <a name="compound-statements-blocks"></a>Složené příkazy (bloky)

Složený příkaz se skládá z nuly nebo více příkazů, které jsou uzavřeny ve složených závorkách ( **{}** ). Složený příkaz lze použít všude, kde je očekáván příkaz. Složené příkazy jsou často označovány za „bloky“.

## <a name="syntax"></a>Syntaxe

```
{ [ statement-list ] }
```

## <a name="remarks"></a>Poznámky

Následující příklad používá složený příkaz jako část *příkazu* **if příkazu if** (viz [příkaz if](../cpp/if-else-statement-cpp.md) pro podrobnosti o syntaxi):

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
>  Vzhledem k tomu, že deklarace je příkaz, může být deklarace jedním z příkazů v *seznamu příkazů*. Důsledkem toho mají názvy deklarované uvnitř složeného příkazu (ale nikoli explicitně deklarované jako statické) místní obor a v případě objektů i životnost. Podrobnosti o zpracování názvů s místním rozsahem najdete v tématu věnovaném [oboru](../cpp/scope-visual-cpp.md) .

## <a name="see-also"></a>Viz také

[Přehled příkazů jazyka C++](../cpp/overview-of-cpp-statements.md)
