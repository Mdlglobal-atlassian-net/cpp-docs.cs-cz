---
title: .CODE
ms.date: 12/06/2019
f1_keywords:
- .CODE
helpviewer_keywords:
- .CODE directive
ms.assetid: 2b8c882c-c0d2-4fa3-8335-e6b12717a4f4
ms.openlocfilehash: 36d9c01d2a24b446ddc91fe73f3cb677067b3e4c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2019
ms.locfileid: "74987918"
---
# <a name="code-32-bit-masm"></a>. KÓD (32-bit MASM)

Při použití s nástrojem [. MODEL](../../assembler/masm/dot-model.md)označuje začátek segmentu kódu.

## <a name="syntax"></a>Syntaxe

> **.** *Název*⟦ kódu ⟧

### <a name="parameters"></a>Parametry

*název*\
Volitelný parametr, který určuje název segmentu kódu. Výchozí název je **_TEXT** pro malé, malé, kompaktní a ploché [modely](../../assembler/masm/dot-model.md). Výchozí název je *module*_TEXT pro jiné modely.

## <a name="see-also"></a>Viz také:

\ – [referenční informace o direktivách](../../assembler/masm/directives-reference.md)
[.DATA](../../assembler/masm/dot-data.md)
