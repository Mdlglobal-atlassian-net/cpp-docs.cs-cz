---
title: .CODE
ms.date: 12/17/2019
f1_keywords:
- .CODE
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
ms.openlocfilehash: 0975e96e670400b7fa221ae2d1b9982b5cee613b
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75314143"
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

## <a name="see-also"></a>Viz také:

\ – [referenční informace o direktivách](directives-reference.md)
[.\ dat](dot-data.md)
[Gramatika BNF MASM](masm-bnf-grammar.md)

