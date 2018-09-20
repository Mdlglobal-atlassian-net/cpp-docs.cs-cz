---
title: Jednofázová a dvoufázová konstrukce objektů | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- objects [MFC], creating graphic objects
- object creation [MFC], graphic objects
- objects [MFC], graphic objects
- one-stage and two-stage construction of objects [MFC]
ms.assetid: 5a1c410c-4a4b-4dd9-a2ec-ced831aa7f21
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a6454e34830591eccb2b696948d02f74ad8cebfd
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46426572"
---
# <a name="one-stage-and-two-stage-construction-of-objects"></a>Jednofázová a dvoufázová konstrukce objektů

Máte možnost volby mezi dvěma techniky pro vytváření grafických objektů, jako je například pera a štětce:

- *Jednofázová konstrukce*: konstrukce a inicializovat objekt v jediném kroku, a to vše pomocí konstruktoru.

- *Dvoufázová konstrukce*: konstrukce a inicializovat objekt ve dvou samostatných fází. Konstruktor vytvoří objekt a inicializační funkce inicializuje ji.

Dvoufázová konstrukce je vždy bezpečnější. V konstrukci jednofázová konstruktor může vyvolat výjimku, pokud zadáte nesprávné argumenty nebo selhání přidělení paměti. Tento problém je zabránit dvoufázová konstrukce, i když mají zkontrolovat chyby. V obou případech je zničení objektu stejného procesu.

> [!NOTE]
>  Tyto postupy použijte k vytvoření všech objektů, pouze grafické objekty.

## <a name="example-of-both-construction-techniques"></a>Příklad obě tyto metody konstrukce

Následující příklad (BRIEF) ukazuje oba způsoby vytváření objekt pen:

[!code-cpp[NVC_MFCDocViewSDI#6](../mfc/codesnippet/cpp/one-stage-and-two-stage-construction-of-objects_1.cpp)]

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Grafické objekty](../mfc/graphic-objects.md)

- [Výběr grafického objektu v kontextu zařízení](../mfc/selecting-a-graphic-object-into-a-device-context.md)

- [Kontexty zařízení](../mfc/device-contexts.md)

- [Kreslení v zobrazení](../mfc/drawing-in-a-view.md)

## <a name="see-also"></a>Viz také

[Grafické objekty](../mfc/graphic-objects.md)

