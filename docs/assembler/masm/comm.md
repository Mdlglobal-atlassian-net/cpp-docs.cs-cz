---
title: POTVRD | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- COMM
dev_langs:
- C++
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 87bf6d91de052d7ecaf637100b455e66819c748b
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43690029"
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
