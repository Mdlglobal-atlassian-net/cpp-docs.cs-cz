---
title: 'MFC – ovládací prvky ActiveX: Vlastnosti'
ms.date: 11/04/2016
helpviewer_keywords:
- properties [MFC], ActiveX controls
- MFC ActiveX controls [MFC], properties
- properties [MFC]
ms.assetid: b678a53c-0d9e-476f-8aa0-23b80baaba46
ms.openlocfilehash: 5e01854e7ae7acdc33275351d0d26a76dfeabc9b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324321"
---
# <a name="mfc-activex-controls-properties"></a>MFC – ovládací prvky ActiveX: Vlastnosti

Ovládací prvek ActiveX aktivuje události ke komunikaci s jejím kontejnerem ovládacího prvku. Kontejner, používá ke komunikaci s ovládacím prvkem na oplátku metody a vlastnosti. Metody a vlastnosti jsou podobné jako u použití a účel, v uvedeném pořadí, členské funkce a proměnné členů třídy jazyka C++. Vlastnosti jsou datové členy ovládacího prvku ActiveX, které jsou vystaveny pro každý kontejner. Vlastnosti poskytují rozhraní pro aplikace, které obsahují ovládací prvky ActiveX, jako je například klienti automatizace a ActiveX – kontejnery ovládacích prvků.

Atributy se také označují jako vlastnosti.

Další informace o metodách ovládací prvek ActiveX, najdete v článku [knihovny MFC – ovládací prvky ActiveX: Metody](../mfc/mfc-activex-controls-methods.md).

Ovládací prvky ActiveX lze implementovat stock a vlastních metod a vlastností. Třída `COleControl` poskytuje implementaci pro základní vlastnosti. (Úplný seznam uložených vlastností, najdete v článku [knihovny MFC – ovládací prvky ActiveX: Přidání uložených vlastností](../mfc/mfc-activex-controls-adding-stock-properties.md).) Vlastní vlastnosti definované pro vývojáře, přidejte specializované funkce do ovládacího prvku ActiveX. Další informace najdete v tématu [knihovny MFC – ovládací prvky ActiveX: Přidání vlastních vlastností](../mfc/mfc-activex-controls-adding-custom-properties.md).

Vlastní a uložené vlastnosti, jako jsou metody, jsou podporovány mechanismus, který se skládá z mapa odeslání, který zpracovává vlastnosti a metody existující členských funkcí třídy `COleControl` třídy. Kromě toho tyto vlastnosti můžou mít parametry, které vývojář používá k předání dalších informací do ovládacího prvku.

Následující články popisují vlastnosti ovládacího prvku ActiveX podrobněji:

- [MFC – ovládací prvky ActiveX: Přidání uložených vlastností](../mfc/mfc-activex-controls-adding-stock-properties.md)

- [MFC – ovládací prvky ActiveX: Přidání vlastních vlastností](../mfc/mfc-activex-controls-adding-custom-properties.md)

- [MFC – ovládací prvky ActiveX: Implementace rozšířených vlastností](../mfc/mfc-activex-controls-advanced-property-implementation.md)

- [MFC – ovládací prvky ActiveX: Přístup k vedlejším vlastnostem](../mfc/mfc-activex-controls-accessing-ambient-properties.md)

## <a name="see-also"></a>Viz také:

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)
