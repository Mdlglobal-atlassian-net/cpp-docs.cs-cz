---
title: COMM
ms.date: 12/06/2019
f1_keywords:
- COMM
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
ms.openlocfilehash: 0ea02806cae3295af0846baa6c4e9049d54c271b
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75315170"
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

Volitelný *typ jazyka* nastaví konvence pojmenování pro následující název. Přepisuje libovolný jazyk určený parametrem **.** Direktiva modelu. Nepovinný **téměř** nebo **úplně** přepsat aktuální paměťový model. *Popisek* je název proměnné. *Typ* může být libovolný specifikátor typu ([Byte](byte-masm.md), [Word](word.md)a tak dále) nebo celé číslo určující počet bajtů. Volitelný *počet* určuje počet prvků v deklarovaném datovém objektu. Výchozí *počet* je jeden.

## <a name="example"></a>Příklad

Tento příklad vytvoří pole bajtů 512:

```asm
COMM FAR ByteArray:BYTE:512
```

## <a name="see-also"></a>Viz také:

\ – [referenční informace o direktivách](directives-reference.md)
[Gramatika BNF MASM](masm-bnf-grammar.md)
