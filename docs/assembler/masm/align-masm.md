---
title: ALIGN (MASM)
ms.date: 12/17/2019
f1_keywords:
- align
helpviewer_keywords:
- ALIGN directive
ms.assetid: 1c386b23-439f-4ec3-a6de-74427b25e47f
ms.openlocfilehash: 700721768deaf92e88b32a97e68c6e017219d19d
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316587"
---
# <a name="align"></a>ALIGN

Direktiva **align** zarovnává další datový prvek nebo instrukci na adrese, která je násobkem jeho parametru. Parametr musí být mocninou 2 (například 1, 2, 4 atd.), která je menší nebo rovna zarovnání segmentu.

## <a name="syntax"></a>Syntaxe

> **Zarovnat** ⟦*constantExpression*⟧

## <a name="remarks"></a>Poznámky

Direktiva **align** umožňuje zadat počáteční posun datového elementu nebo instrukce. Zarovnaná data mohou zvýšit výkon na úkor nevyužitého prostoru mezi datovými prvky. Velká vylepšení výkonu se dají zobrazit, když jsou přístup k datům na hranicích, která se vejdou do mezipamětí. Přístup k přirozeným hranicím pro nativní typy znamená méně času stráveného při vyžádal povolení mikrokódu interního přerovnávání hardwaru.

Nutnost zarovnaných instrukcí je u moderních procesorů, které používají model plochých adres, málo vzácná, ale může se vyžadovat pro cíle skoků ve starším kódu pro jiné modely adresování.

Když jsou data zarovnána, vynechané místo je doplněno nulami. Po zarovnávání instrukcí se vynechané místo vyplní vhodně NOP instrukcemi.

## <a name="see-also"></a>Viz také:

[I](even.md)\
\ – [referenční informace o direktivách](directives-reference.md)
[Gramatika BNF MASM](masm-bnf-grammar.md)
