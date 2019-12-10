---
title: COMM
ms.date: 12/06/2019
f1_keywords:
- COMM
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
ms.openlocfilehash: 93e7c891b1c964eca5b3ff7fd15956ef25ea05e6
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74987943"
---
# <a name="comm"></a>COMM

Vytvoří obecnou proměnnou s atributy zadanými v *definici*.

## <a name="syntax"></a>Syntaxe

> ⟦ *Definice* komunikace __,__ *definice* ... ⟧

## <a name="remarks"></a>Poznámky

Obce proměnné jsou přidělovány linkerem a nelze je inicializovat. To znamená, že nemůžete záviset na umístění nebo sekvenci takových proměnných.

Každá *definice* má následující formát:

⟦*Language-Type*⟧ ⟦ v**blízkosti** | **mnohem**⟧ _Label_ **:** _Type_⟦ **:** _Count_⟧

Argumenty *pro typ jazyka*, **blízko**a **daleko** jsou platné pouze v 32 bitů MASM.

Volitelný *typ jazyka* nastaví konvence pojmenování pro následující název. Přepisuje libovolný jazyk určený parametrem **.** Direktiva modelu. Nepovinný **téměř** nebo **úplně** přepsat aktuální paměťový model. *Popisek* je název proměnné. *Typ* může být libovolný specifikátor typu ([Byte](../../assembler/masm/byte-masm.md), [Word](../../assembler/masm/word.md)a tak dále) nebo celé číslo určující počet bajtů. Volitelný *počet* určuje počet prvků v deklarovaném datovém objektu. Výchozí *počet* je jeden.

## <a name="example"></a>Příklad

Tento příklad vytvoří pole bajtů 512:

```asm
COMM FAR ByteArray:BYTE:512
```

## <a name="see-also"></a>Viz také:

[Odkazy na direktivy](directives-reference.md)
