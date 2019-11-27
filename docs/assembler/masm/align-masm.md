---
title: ALIGN (MASM)
ms.date: 01/02/2019
f1_keywords:
- align
helpviewer_keywords:
- ALIGN directive
ms.assetid: 1c386b23-439f-4ec3-a6de-74427b25e47f
ms.openlocfilehash: 22b18f2e238c780377b84fc2be3eb6678686bb73
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74399272"
---
# <a name="align-masm"></a>ALIGN (MASM)

Direktiva **align** zarovnává další datový prvek nebo instrukci na adrese, která je násobkem jeho parametru. Parametr musí být mocninou 2 (například 1, 2, 4 atd.), která je menší nebo rovna zarovnání segmentu.

## <a name="syntax"></a>Syntaxe

> **Zarovnat** ⟦*číslo*⟧

## <a name="remarks"></a>Poznámky

Direktiva **align** umožňuje zadat počáteční posun datového elementu nebo instrukce. Zarovnaná data mohou zvýšit výkon na úkor nevyužitého prostoru mezi datovými prvky. Velká vylepšení výkonu se dají zobrazit, když jsou přístup k datům na hranicích, která se vejdou do mezipamětí. Přístup k přirozeným hranicím pro nativní typy znamená méně času stráveného při vyžádal povolení mikrokódu interního přerovnávání hardwaru.

Nutnost zarovnaných instrukcí je u moderních procesorů, které používají model plochých adres, málo vzácná, ale může se vyžadovat pro cíle skoků ve starším kódu pro jiné modely adresování.

Když jsou data zarovnána, vynechané místo je doplněno nulami. Po zarovnávání instrukcí se vynechané místo vyplní vhodně NOP instrukcemi.

## <a name="see-also"></a>Viz také:

[I](even.md)\
[Odkazy na direktivy](directives-reference.md)
