---
title: COMM
ms.date: 08/30/2018
f1_keywords:
- COMM
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
ms.openlocfilehash: d36161ba54ca80fc0f576c6f0a7c2a9410bf8075
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541033"
---
# <a name="comm"></a>COMM

Vytvoří obecnou proměnnou s atributy zadanými v *definici*.

## <a name="syntax"></a>Syntaxe

> ⟦ *Definice* komunikace __,__ *definice* ... ⟧

## <a name="remarks"></a>Poznámky

Obce proměnné jsou přidělovány linkerem a nelze je inicializovat. To znamená, že nemůžete záviset na umístění nebo sekvenci takových proměnných.

Každá *definice* má následující formát:

⟦*Language-Type*⟧ ⟦ v**blízkosti** | **mnohem**⟧ _Label_ **:** _Type_⟦ **:** _Count_⟧

Volitelný *typ jazyka* nastaví konvence pojmenování pro následující název. Přepisuje libovolný jazyk určený parametrem **.** Direktiva modelu. Nepovinný **téměř** nebo **úplně** přepsat aktuální paměťový model. *Popisek* je název proměnné. *Typ* může být libovolný specifikátor typu ([Byte](../../assembler/masm/byte-masm.md), [Word](../../assembler/masm/word.md)a tak dále) nebo celé číslo určující počet bajtů. Volitelný *počet* určuje počet prvků v deklarovaném datovém objektu. Výchozí *počet* je jeden.

## <a name="example"></a>Příklad

Tento příklad vytvoří pole bajtů 512:

```asm
COMM FAR ByteArray:BYTE:512
```

## <a name="see-also"></a>Viz také:

[Odkazy na direktivy](directives-reference.md)
