---
title: 'Ovládací prvky MFC ActiveX: Události | Microsoft Docs'
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
ms.openlocfilehash: e6c8ee059b4136ce1504117246abd12ac74a6233
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33348387"
---
# <a name="mfc-activex-controls-events"></a>MFC – ovládací prvky ActiveX: Události
Ovládací prvky ActiveX do kontejneru, který má se něco stalo do ovládacího prvku pomocí události. Běžné události příklady klikne na ovládací prvek, data zadaná pomocí klávesnice a změny ve stavu ovládacího prvku. Pokud dojde k těmto akcím, aktivuje se ovládacího prvku událost upozorní kontejneru.  
  
 Události se také označují jako zprávy.  
  
 MFC podporuje dva typy událostí: uložených a vlastní. Uložené události jsou události, které třídy [COleControl](../mfc/reference/colecontrol-class.md) zpracovává automaticky. Úplný seznam uložených událostí, najdete v článku [MFC – ovládací prvky ActiveX: přidání události Stock](../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md). Vlastní události povolit možnost kontejneru upozornit, když dojde k akci specifické pro tuto kontrolu ovládacího prvku. Některé příklady by změnu vnitřní stav ovládacího prvku nebo příjem určité okno zprávy.  
  
 Pro ovládací prvek k vyvolání události správně musí třídě ovládacího mapovat všechny události ovládacího prvku členské funkce, která by měla být volána, když dojde k související události. Tento mechanismus mapování (nazývá mapa událostí) centralizuje informace o události a umožňuje sadě Visual Studio snadno přistupovat a manipulovat s události ovládacího prvku. Tato mapa událostí je deklarovaná následující makro, umístěný v hlavičce (. H) soubor deklarace třídy ovládacího prvku:  
  
 [!code-cpp[NVC_MFC_AxUI#2](../mfc/codesnippet/cpp/mfc-activex-controls-events_1.h)]  
  
 Poté, co bylo deklarováno mapa událostí, musí být definován v implementaci ovládacího prvku (. Soubor CPP). Následující řádky kódu definovat mapa událostí, což ovládacího prvku k vyvolání konkrétní události:  
  
 [!code-cpp[NVC_MFC_AxUI#3](../mfc/codesnippet/cpp/mfc-activex-controls-events_2.cpp)]  
[!code-cpp[NVC_MFC_AxUI#4](../mfc/codesnippet/cpp/mfc-activex-controls-events_3.cpp)]  
  
 Pokud používáte Průvodce ovládacím prvkem ActiveX knihovny MFC a vytvořte tak projekt, automaticky přidá tyto řádky. Pokud použijete Průvodce ovládacím prvkem ActiveX knihovny MFC, je nutné ručně přidat tyto řádky.  
  
 Zobrazení tříd, můžete přidat uložených událostí podporovaných třídou `COleControl` nebo uživatelské události, které definujete. Pro všechny nové události zobrazení tříd automaticky přidá položku správná mapa událostí ovládacího prvku a ovládacího prvku. IDL soubor.  
  
 Dva další články popisují události podrobně:  
  
-   [Ovládací prvky MFC ActiveX: Přidání uložených událostí](../mfc/mfc-activex-controls-adding-stock-events-to-an-activex-control.md)  
  
-   [MFC – ovládací prvky ActiveX: Přidání vlastních událostí](../mfc/mfc-activex-controls-adding-custom-events.md)  
  
## <a name="see-also"></a>Viz také  
 [Ovládací prvky MFC ActiveX](../mfc/mfc-activex-controls.md)   
 [MFC – ovládací prvky ActiveX: metody](../mfc/mfc-activex-controls-methods.md)   
 [COleControl – třída](../mfc/reference/colecontrol-class.md)
