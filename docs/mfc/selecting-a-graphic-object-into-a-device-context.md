---
title: Výběr grafického objektu v kontextu zařízení
ms.date: 11/04/2016
helpviewer_keywords:
- graphic objects [MFC], selecting into device context
- SelectObject method [MFC]
- GDI objects [MFC], device contexts
- lifetime, graphic objects [MFC]
- device contexts, selecting graphic objects into
- device contexts, graphic objects [MFC]
ms.assetid: cf54a330-63ef-421f-83eb-90ec7bd82eef
ms.openlocfilehash: c879369d445a9330139eff89be4ad8153252bfa1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50438818"
---
# <a name="selecting-a-graphic-object-into-a-device-context"></a>Výběr grafického objektu v kontextu zařízení

Toto téma se týká použití grafických objektů v kontextu zařízení okna. Poté co [vytvořit kresby](../mfc/one-stage-and-two-stage-construction-of-objects.md), je nutné vybrat do kontextu zařízení místo výchozí objekt uložených:

[!code-cpp[NVC_MFCDocViewSDI#7](../mfc/codesnippet/cpp/selecting-a-graphic-object-into-a-device-context_1.cpp)]

## <a name="lifetime-of-graphic-objects"></a>Doba života grafických objektů

Grafický objekt vrácený rutinou [SelectObject –](../mfc/reference/cdc-class.md#selectobject) je "dočasné." To znamená, že bude odstraněna podle [OnIdle](../mfc/reference/cwinapp-class.md#onidle) členské funkce třídy `CWinApp` čas při příštím program získá nečinnosti. Za předpokladu, použijte objekt vrácený rutinou `SelectObject` v jedné funkci bez vrácení ovládacího prvku hlavní smyčka zpráv, budete mít žádný problém.

### <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací

- [Grafické objekty](../mfc/graphic-objects.md)

- [Jednofázová a dvoufázová konstrukce objektů grafiky](../mfc/one-stage-and-two-stage-construction-of-objects.md)

- [Kontexty zařízení](../mfc/device-contexts.md)

- [Kreslení v zobrazení](../mfc/drawing-in-a-view.md)

## <a name="see-also"></a>Viz také

[Grafické objekty](../mfc/graphic-objects.md)

