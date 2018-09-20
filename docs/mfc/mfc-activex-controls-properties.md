---
title: 'MFC – ovládací prvky ActiveX: Vlastnosti | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
- properties [MFC]
ms.assetid: b678a53c-0d9e-476f-8aa0-23b80baaba46
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 27cdbd548366bcf02e2d6282b309402cf25af2d1
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46401612"
---
# <a name="mfc-activex-controls-properties"></a>MFC – ovládací prvky ActiveX: Vlastnosti

Ovládací prvek ActiveX aktivuje události ke komunikaci s jejím kontejnerem ovládacího prvku. Kontejner, používá ke komunikaci s ovládacím prvkem na oplátku metody a vlastnosti. Metody a vlastnosti jsou podobné jako u použití a účel, v uvedeném pořadí, členské funkce a proměnné členů třídy jazyka C++. Vlastnosti jsou datové členy ovládacího prvku ActiveX, které jsou vystaveny pro každý kontejner. Vlastnosti poskytují rozhraní pro aplikace, které obsahují ovládací prvky ActiveX, jako je například klienti automatizace a ActiveX – kontejnery ovládacích prvků.

Atributy se také označují jako vlastnosti.

Další informace o metodách ovládací prvek ActiveX, najdete v článku [knihovny MFC – ovládací prvky ActiveX: metody](../mfc/mfc-activex-controls-methods.md).

Ovládací prvky ActiveX lze implementovat stock a vlastních metod a vlastností. Třída `COleControl` poskytuje implementaci pro základní vlastnosti. (Úplný seznam uložených vlastností, najdete v článku [knihovny MFC – ovládací prvky ActiveX: Přidání uložené vlastnosti](../mfc/mfc-activex-controls-adding-stock-properties.md).) Vlastní vlastnosti definované pro vývojáře, přidejte specializované funkce do ovládacího prvku ActiveX. Další informace najdete v tématu [knihovny MFC – ovládací prvky ActiveX: Přidání vlastních vlastností](../mfc/mfc-activex-controls-adding-custom-properties.md).

Vlastní a uložené vlastnosti, jako jsou metody, jsou podporovány mechanismus, který se skládá z mapa odeslání, který zpracovává vlastnosti a metody existující členských funkcí třídy `COleControl` třídy. Kromě toho tyto vlastnosti můžou mít parametry, které vývojář používá k předání dalších informací do ovládacího prvku.

Následující články popisují vlastnosti ovládacího prvku ActiveX podrobněji:

- [MFC – ovládací prvky ActiveX: Přidání uložených vlastností](../mfc/mfc-activex-controls-adding-stock-properties.md)

- [MFC – ovládací prvky ActiveX: Přidání přizpůsobených vlastností](../mfc/mfc-activex-controls-adding-custom-properties.md)

- [MFC – ovládací prvky ActiveX: Implementace rozšířených vlastností](../mfc/mfc-activex-controls-advanced-property-implementation.md)

- [MFC – ovládací prvky ActiveX: Přístup k vedlejším vlastnostem](../mfc/mfc-activex-controls-accessing-ambient-properties.md)

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)

