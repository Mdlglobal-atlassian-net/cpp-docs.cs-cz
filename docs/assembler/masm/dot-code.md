---
title: .CODE
ms.date: 12/17/2019
f1_keywords:
- .CODE
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
ms.openlocfilehash: 7e53befcc46319d0ecf2287ab96a19a73a0b0b85
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076268"
---
# <a name="code"></a>.CODE

(jenom 32-bitová MASM.) Při použití s nástrojem [. MODEL](dot-model.md)označuje začátek segmentu kódu.

## <a name="syntax"></a>Syntaxe

> **.** *Název*⟦ kódu ⟧ \
> ⟦ *segmentItem* ⟧... \
> ⟦ *codesegmentnameId* **končí**;; ⟧\

### <a name="parameters"></a>Parametry

*název*\
Volitelný parametr, který určuje název segmentu kódu. Výchozí název je **_TEXT** pro malé, malé, kompaktní a ploché [modely](dot-model.md). Výchozí název je *module*_TEXT pro jiné modely.

## <a name="see-also"></a>Viz také

\ – [referenční informace o direktivách](directives-reference.md)
[.\ dat](dot-data.md)
[Gramatika BNF MASM](masm-bnf-grammar.md)
