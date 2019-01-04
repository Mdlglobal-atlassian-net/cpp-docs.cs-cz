---
title: ALIGN (MASM)
ms.date: 01/02/2019
f1_keywords:
- align
helpviewer_keywords:
- ALIGN directive
ms.assetid: 1c386b23-439f-4ec3-a6de-74427b25e47f
ms.openlocfilehash: eb42b1952b3fd59438f0dd4c29d48c91c4d8864d
ms.sourcegitcommit: cce52b2232b94ce8fd8135155b86e2d38a4e4562
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/04/2019
ms.locfileid: "54031223"
---
# <a name="align-masm"></a>ALIGN (MASM)

**ZAROVNAT** – direktiva zarovná další prvek dat nebo instrukce na adrese, která je násobkem jeho parametru. Parametr musí být mocninou čísla 2 (například 1, 2, 4 a tak dále), který je menší než nebo rovno zarovnání segmentu.

## <a name="syntax"></a>Syntaxe

> ZAROVNAT [[*číslo*]]

## <a name="remarks"></a>Poznámky

**ZAROVNAT** – direktiva umožňuje určit posun od datového elementu nebo instrukci. Zarovnané datové může zlepšit výkon za cenu nevyužité místo mezi datové prvky. Velká vylepšení výkonu můžete zobrazit, když jsou data přístupy na hranicích, které se vejdou do mezipaměti řádky. Přístup na přirozené hranice pro nativní typy znamená méně času stráveného mikrokód nové zarovnání interní hardwaru.

Potřebu zarovnané pokyny není obvyklé u moderní procesorů, které používají plochý adresování model, ale může být nezbytné pro cíle jump ve starším kódu pro ostatní modely adresování.

Když data jsou zarovnána, přeskočené místo doplněno nulami. Když jsou zarovnány pokyny, přeskočené prostor zaplněný s odpovídajícím způsobem velikosti NOP pokyny.

## <a name="see-also"></a>Viz také:

[EVEN](even.md)<br/>
[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>