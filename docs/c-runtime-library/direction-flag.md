---
title: Příznak směru
ms.date: 11/04/2016
f1_keywords:
- c.flags
helpviewer_keywords:
- direction flag
ms.assetid: 0836b4af-dbbb-4ab8-a4b2-156f2e2099e2
ms.openlocfilehash: ead32fa7f09e9dd98130855ecd87ba3b3d454ef5
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57740153"
---
# <a name="direction-flag"></a>Příznak směru

Příznak směru je specifické pro všechny procesory Intel x86 kompatibilní příznak procesoru. Platí pro všechny pokyny k sestavení, které používají předpona REP (opakování), například MOVS, MOVSD, MOVSW a dalších. Adresy, které jsou k dispozici na příslušné pokyny jsou zvýšena, pokud se vymaže příznak směru.

Běhové rutiny jazyka C předpokládá, že se vymaže příznak směru. Pokud používáte jiné funkce s funkcí jazyka C za běhu, musíte zajistit, že jiné funkce ponechat stávající příznak směru samostatně, nebo jej obnovit do původního stavu. Příznak směru, aby se nezapomnělo při vstupu je očekáván díky za běhu kódu rychlejší a efektivnější.

Příznak směru, aby se nezapomnělo očekávat, že funkce knihovny C Run-Time, jako je například rutiny zacházení s řetězci a zacházení s vyrovnávací pamětí.

## <a name="see-also"></a>Viz také:

[Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)
