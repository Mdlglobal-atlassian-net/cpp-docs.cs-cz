---
title: 'MFC – ovládací prvky ActiveX: Metody'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], methods
ms.assetid: e20271de-6ffa-4ba0-848b-bafe6c9e510c
ms.openlocfilehash: 71c4cdd5ea07b3468b7878a221129a0de5eb4974
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57268405"
---
# <a name="mfc-activex-controls-methods"></a>MFC – ovládací prvky ActiveX: Metody

Ovládací prvek ActiveX aktivuje události ke komunikaci mezi samostatně a jeho kontejneru ovládacího prvku. Kontejner můžete také komunikovat s ovládacím prvkem prostřednictvím metody a vlastnosti. Metody jsou také volat funkce.

Metody a vlastnosti poskytují exportovaného rozhraní pro použití jiné aplikace, jako je například klienti automatizace a ActiveX – kontejnery ovládacích prvků. Další informace o vlastnosti ovládacích prvků ActiveX naleznete v článku [knihovny MFC – ovládací prvky ActiveX: Vlastnosti](../mfc/mfc-activex-controls-properties.md).

Metody jsou podobné v použití a účel členské funkce třídy jazyka C++. Existují dva typy metod můžete implementovat ovládacího prvku: uložených a vlastních. Podobné události zásob, stock metody jsou tyto metody pro kterou [COleControl](../mfc/reference/colecontrol-class.md) poskytuje implementaci. Další informace o uložených metod najdete v článku [knihovny MFC – ovládací prvky ActiveX: Přidání uložených metod](../mfc/mfc-activex-controls-adding-stock-methods.md). Vlastní metody, určené pro vývojáře, umožní líp přizpůsobte ovládacího prvku. Další informace najdete v článku [knihovny MFC – ovládací prvky ActiveX: Přidání vlastních metod](../mfc/mfc-activex-controls-adding-custom-methods.md).

Třídy knihovny MFC (Microsoft Foundation) implementuje mechanismus, který umožňuje ovládacího prvku pro podporu stock a vlastních metod. První část je třída `COleControl`. Odvozené od `CWnd`, `COleControl` členské funkce podporují uložených metod, které jsou společné pro všechny ovládací prvky ActiveX. Druhá část tento mechanismus je mapa odeslání. Mapa odeslání je podobný mapy zpráv; však namísto funkce mapování na ID zprávy Windows, mapuje mapa odbavení virtuální členské funkce na ID rozhraní IDispatch.

Pro ovládací prvek pro podporu různých metodách správně musí deklarovat své třídy mapa odeslání. Toho lze dosáhnout následující řádek kódu, na které se nachází v záhlaví třídy ovládacího prvku (. H) file:

[!code-cpp[NVC_MFC_AxUI#13](../mfc/codesnippet/cpp/mfc-activex-controls-methods_1.h)]

Hlavním účelem mapa odeslání je a tím vytvoří vztah mezi názvy metod používaných externích volající (jako je například kontejner) a členské funkce třídy ovládacího prvku, které implementují. Po mapa odeslání je deklarovaná, musí být definován v implementaci ovládacího prvku (. Soubor CPP). Následující řádky kódu definovat mapa odeslání:

[!code-cpp[NVC_MFC_AxUI#14](../mfc/codesnippet/cpp/mfc-activex-controls-methods_2.cpp)]
[!code-cpp[NVC_MFC_AxUI#15](../mfc/codesnippet/cpp/mfc-activex-controls-methods_3.cpp)]

Pokud jste použili [Průvodce ovládacím prvkem MFC ActiveX](../mfc/reference/mfc-activex-control-wizard.md) pro vytvoření projektu byly automaticky přidány tyto řádky. Pokud nebyl použit průvodce ovládací prvek ActiveX knihovny MFC, musíte ručně přidejte tyto řádky.

Následující články popisují metody podrobně:

- [MFC – ovládací prvky ActiveX: Přidání uložených metod](../mfc/mfc-activex-controls-adding-stock-methods.md)

- [MFC – ovládací prvky ActiveX: Přidání vlastních metod](../mfc/mfc-activex-controls-adding-custom-methods.md)

- [MFC – ovládací prvky ActiveX: Vrácení chybových kódů z metody](../mfc/mfc-activex-controls-returning-error-codes-from-a-method.md)

## <a name="see-also"></a>Viz také:

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)
