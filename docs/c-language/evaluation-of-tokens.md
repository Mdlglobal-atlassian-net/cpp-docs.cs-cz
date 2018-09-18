---
title: Vyhodnocení tokenů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- tokens, evaluating
ms.assetid: 28870b62-dff6-4644-8b75-d58f340b48d2
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5d5c79ac043b2131df7a876f2de63922c45c9ead
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035276"
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