---
title: Vyhodnocení tokenů
ms.date: 11/04/2016
helpviewer_keywords:
- tokens, evaluating
ms.assetid: 28870b62-dff6-4644-8b75-d58f340b48d2
ms.openlocfilehash: c54b497464d68a9e6c6048a93119726e14ef4718
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482053"
---
# <a name="evaluation-of-tokens"></a>Vyhodnocení tokenů

Při interpretaci tokenů kompilátor před přechodem na další token zahrne do jednoho tokenu co nejvíce znaků. Vlivem tohoto chování kompilátor možná nebude interpretovat tokeny zamýšleným způsobem, pokud nejsou správně odděleny prázdným znakem. Vezměte v úvahu následující výraz:

```
i+++j
```

V tomto příkladu kompilátor nejprve ze tří znamének plus utvoří nejdelší možný operátor (`++`) a poté zpracuje zbývající znaménko plus jako operátor sčítání (`+`). Výraz je proto interpretován jako výraz `(i++) + (j)`, nikoli `(i) + (++j)`. V tomto a podobných případech se použitím prázdných znaků a závorek vyhněte víceznačnosti a zajistěte správné vyhodnocení výrazu.

**Specifické pro Microsoft**

Kompilátor jazyka C zpracovává znak CTRL+Z jako indikátor konce souboru. Veškerý text za znakem CTRL+Z je ignorován.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Tokeny jazyka C](../c-language/c-tokens.md)