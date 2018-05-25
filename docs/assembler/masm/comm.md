---
title: COMM – | Microsoft Docs
ms.custom: ''
ms.date: 05/22/2018
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
ms.openlocfilehash: 1df6c729ab130a7ff38d7f7cf83224e7425e7dba
ms.sourcegitcommit: da7b7533d1a4dc141cc0f09149e4e4196f2fe329
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2018
---
# <a name="comm"></a>COMM

Vytvoří místní proměnné s atributy určené v *definice*.

## <a name="syntax"></a>Syntaxe

> **Comm –** *definice* [, *definice*]...

## <a name="remarks"></a>Poznámky

Místní proměnné jsou přidělena linkeru a nelze ho inicializovat. To znamená, že nemůže záviset na umístění nebo pořadí těchto proměnných.

Každý *definice* má následující formát:

[*langtype*] [**NEAR** &#124; **DÁLNÉHO**] _popisek_**:**_typ_[**:**_počet_]

Volitelné *langtype* nastaví konvence pojmenování pro název, který následuje dále. Přepíše jakékoli jazyk, který **. MODEL** – direktiva. Volitelné **NEAR** nebo **DÁLNÉHO** přepsat na aktuální model paměti. *Popisek* je název proměnné. *Typ* může být jakékoli specifikátor typu ([BAJTŮ](../../assembler/masm/byte-masm.md), [WORD](../../assembler/masm/word.md)a tak dále) nebo celé číslo určující počet bajtů. Volitelné *počet* určuje počet elementů v objektu deklarované dat; výchozí hodnota je jedna.

## <a name="example"></a>Příklad

Tento příklad vytvoří pole 512 BAJTŮ elementů:

```masm
COMM FAR ByteArray:BYTE:512
```

## <a name="see-also"></a>Viz také

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)
