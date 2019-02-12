---
title: Vyhodnocení tokenů
ms.date: 11/04/2016
helpviewer_keywords:
- tokens, evaluating
ms.assetid: 28870b62-dff6-4644-8b75-d58f340b48d2
ms.openlocfilehash: 15775ca9a7ada46aaf4e53ae952cd67e95bbf8d3
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56152544"
---
# <a name="evaluation-of-tokens"></a>Vyhodnocení tokenů

Při interpretaci tokenů kompilátor před přechodem na další token zahrne do jednoho tokenu co nejvíce znaků. Vlivem tohoto chování kompilátor možná nebude interpretovat tokeny zamýšleným způsobem, pokud nejsou správně odděleny prázdným znakem. Vezměte v úvahu následující výraz:

```
i+++j
```

V tomto příkladu kompilátor nejprve ze tří znamének plus utvoří nejdelší možný operátor (`++`) a poté zpracuje zbývající znaménko plus jako operátor sčítání (`+`). Výraz je proto interpretován jako výraz `(i++) + (j)`, nikoli `(i) + (++j)`. V tomto a podobných případech se použitím prázdných znaků a závorek vyhněte víceznačnosti a zajistěte správné vyhodnocení výrazu.

**Microsoft Specific**

Kompilátor jazyka C zpracovává znak CTRL+Z jako indikátor konce souboru. Veškerý text za znakem CTRL+Z je ignorován.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Tokeny jazyka C](../c-language/c-tokens.md)
