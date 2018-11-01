---
title: COMM
ms.date: 08/30/2018
f1_keywords:
- COMM
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
ms.openlocfilehash: 342c8acd95fd45de1a21dc298325de9a7b40b717
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434798"
---
# <a name="comm"></a>COMM

Vytvoří místní proměnnou s atributy určené v *definice*.

## <a name="syntax"></a>Syntaxe

> **POTVRD** *definice* [, *definice*]...

## <a name="remarks"></a>Poznámky

Místní proměnné se přiděluje pomocí linkeru a nelze inicializovat. To znamená, že nemohou záviset na umístění nebo pořadí těchto proměnných.

Každý *definice* má následující formát:

[*langtype*] [**NEAR** &#124; **FAR**] _popisek_**:**_typ_[**:**_počet_]

Volitelný *langtype* nastaví zásady vytváření názvů pro název, který následuje. Přepíše libovolný jazyk určený **. MODEL** směrnice. Volitelný **NEAR** nebo **FAR** přepsat aktuální model paměti. *Popisek* je název proměnné. *Typ* může být libovolný typ specifikátor ([BAJTŮ](../../assembler/masm/byte-masm.md), [slovo](../../assembler/masm/word.md), a tak dále) nebo celé číslo určující počet bajtů. Volitelný *počet* určuje počet prvků v objektu deklarovanému datovému; výchozí hodnota je jeden.

## <a name="example"></a>Příklad

Tento příklad vytvoří pole prvků 512 BAJTŮ:

```asm
COMM FAR ByteArray:BYTE:512
```

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>
