---
title: 'MFC – ovládací prvky ActiveX: Události | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], events
- notifications [MFC], notifying containers of events
- custom events [MFC], adding to ActiveX controls
- events [MFC], mapping
- COleControl class [MFC], handling of events
- mappings [MFC], events
- stock events [MFC]
- container events [MFC]
- events [MFC], ActiveX controls
- OLE events [MFC]
ms.assetid: e1e57e0c-206b-4923-a0b5-682c26564f74
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a4c60c949832f03df6b7bb0e69cfdd95dfafc137
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46422867"
---
# <a name="mfc-activex-controls-events"></a>MFC – ovládací prvky ActiveX: Události

Ovládací prvky ActiveX do kontejneru, který se něco stalo do ovládacího prvku pomocí události. Běžné příklady událostí, které zahrnují kliknutí v ovládacím prvku dat zadané pomocí klávesnice a změny ve stavu ovládacího prvku. Pokud dojde k těmto akcím, ovládací prvek aktivuje událost výstrahy kontejneru.

Události jsou nazývány také zprávy.

MFC podporuje dva typy událostí: uložených a vlastních. Uložených událostí jsou události, které třídy [COleControl](../mfc/reference/colecontrol-class.md) zpracovává automaticky. Úplný seznam uložených událostí, najdete v článku [knihovny MFC – ovládací prvky ActiveX: přidání události akcie](../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md). Vlastní události umožnit ovládací prvek kontejneru upozornit, když dojde k akci specifické pro tento ovládací prvek. Některé příklady by změna vnitřní stav ovládacího prvku nebo přijetí určité zprávy okna.

Pro ovládací prvek k vyvolání události správně musí třídy vašeho ovládacího prvku mapy každou událost ovládacího prvku na členskou funkci, která by měla být volána, když dojde k související události. Tento mechanismus mapování (označované jako mapu událostí) centralizuje informace o události a umožňuje sadě Visual Studio snadno přístup k a manipulaci s události ovládacího prvku. Tato mapa událostí je deklarována pomocí následující makra, umístěn v záhlaví (. H) file deklarace třídy ovládacího prvku:

[!code-cpp[NVC_MFC_AxUI#2](../mfc/codesnippet/cpp/mfc-activex-controls-events_1.h)]

Po mapa událostí je deklarovaná, musí být definován v implementaci ovládacího prvku (. Soubor CPP). Následující řádky kódu definovat mapa událostí, což ovládacího prvku k vyvolání konkrétní události:

[!code-cpp[NVC_MFC_AxUI#3](../mfc/codesnippet/cpp/mfc-activex-controls-events_2.cpp)]
[!code-cpp[NVC_MFC_AxUI#4](../mfc/codesnippet/cpp/mfc-activex-controls-events_3.cpp)]

Pokud používáte průvodce ovládací prvek ActiveX knihovny MFC pro vytvoření projektu, automaticky přidá tyto řádky. Pokud je velmi riskantní používat průvodce ovládací prvek ActiveX knihovny MFC, musíte ručně přidejte tyto řádky.

Zobrazení tříd, můžete přidat uložených událostí třídou podporován `COleControl` nebo vlastní události, které definujete. Pro všechny nové události zobrazení tříd automaticky přidá správnou položku Mapa událostí ovládacího prvku a ovládacího prvku. Soubor IDL.

Dva další články popisují události podrobně:

- [MFC – ovládací prvky ActiveX: Přidání uložených událostí](../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)

- [MFC – ovládací prvky ActiveX: Přidání vlastních událostí](../mfc/mfc-activex-controls-adding-custom-events.md)

## <a name="see-also"></a>Viz také

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)<br/>
[MFC – ovládací prvky ActiveX: Metody](../mfc/mfc-activex-controls-methods.md)<br/>
[COleControl – třída](../mfc/reference/colecontrol-class.md)
