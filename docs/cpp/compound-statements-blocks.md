---
title: Složené příkazy (bloky) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- '}'
- '{'
dev_langs:
- C++
helpviewer_keywords:
- blocks, about blocks
- compound statements
ms.assetid: 23855939-7430-498e-8936-0c70055ea701
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89e243dd1905e61a6c9a1b16c1936d7d6617ba17
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46116812"
---
# <a name="compound-statements-blocks"></a>Složené příkazy (bloky)

Složený příkaz se skládá z nuly nebo více příkazů uzavřených do složených závorek (**{}**). Složený příkaz lze použít všude, kde je očekáván příkaz. Složené příkazy jsou často označovány za „bloky“.

## <a name="syntax"></a>Syntaxe

```
{ [ statement-list ] }
```

## <a name="remarks"></a>Poznámky

Následující příklad používá složený příkaz jako *příkaz* součástí **Pokud** – příkaz (naleznete v tématu [if – příkaz](../cpp/if-else-statement-cpp.md) podrobnosti o syntaxi):

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
>  Jelikož deklarace je příkaz, deklarace může být jeden z příkazů v *seznamu příkazů*. Důsledkem toho mají názvy deklarované uvnitř složeného příkazu (ale nikoli explicitně deklarované jako statické) místní obor a v případě objektů i životnost. Zobrazit [oboru](../cpp/scope-visual-cpp.md) podrobné informace o zpracování názvů s místním rozsahem.

## <a name="see-also"></a>Viz také:

[Přehled příkazů jazyka C++](../cpp/overview-of-cpp-statements.md)