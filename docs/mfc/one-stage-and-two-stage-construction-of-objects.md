---
title: Jednofázová a dvoufázová konstrukce objektů
ms.date: 11/04/2016
helpviewer_keywords:
- objects [MFC], creating graphic objects
- object creation [MFC], graphic objects
- objects [MFC], graphic objects
- one-stage and two-stage construction of objects [MFC]
ms.assetid: 5a1c410c-4a4b-4dd9-a2ec-ced831aa7f21
ms.openlocfilehash: 8f221ac6b63a06c65f932a695dfbf7b93ae7ac96
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81375970"
---
# <a name="one-stage-and-two-stage-construction-of-objects"></a>Jednofázová a dvoufázová konstrukce objektů

Máte na výběr mezi dvěma technikami vytváření grafických objektů, jako jsou pera a stopy:

- *Jednostupňová konstrukce*: Zkonstruujte a inicializujte objekt v jedné fázi, vše s konstruktorem.

- *Dvoustupňová konstrukce*: Zkonstruuj a inicializuje objekt ve dvou samostatných fázích. Konstruktor vytvoří objekt a inicializační funkce jej inicializuje.

Dvoustupňová konstrukce je vždy bezpečnější. V jednofázové konstrukci může konstruktor vyvolat výjimku, pokud zadáte nesprávné argumenty nebo se nezdaří přidělení paměti. Tomuto problému se vyhýbá dvoustupňová konstrukce, i když musíte zkontrolovat selhání. V obou případech zničení objektu je stejný proces.

> [!NOTE]
> Tyto techniky platí pro vytváření libovolných objektů, nejen grafických objektů.

## <a name="example-of-both-construction-techniques"></a>Příklad obou stavebních technik

Následující stručný příklad ukazuje obě metody konstrukce objektu pera:

[!code-cpp[NVC_MFCDocViewSDI#6](../mfc/codesnippet/cpp/one-stage-and-two-stage-construction-of-objects_1.cpp)]

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o

- [Grafické objekty](../mfc/graphic-objects.md)

- [Výběr grafického objektu do kontextu zařízení](../mfc/selecting-a-graphic-object-into-a-device-context.md)

- [Kontexty zařízení](../mfc/device-contexts.md)

- [Kreslení v zobrazení](../mfc/drawing-in-a-view.md)

## <a name="see-also"></a>Viz také

[Grafické objekty](../mfc/graphic-objects.md)
