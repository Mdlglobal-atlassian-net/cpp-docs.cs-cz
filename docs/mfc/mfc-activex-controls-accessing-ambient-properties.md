---
title: 'MFC – ovládací prvky ActiveX: Přístup k vedlejším vlastnostem'
ms.date: 11/04/2016
helpviewer_keywords:
- MFC ActiveX controls [MFC], accessing ambient properties
- properties [MFC], accessing ambient
ms.assetid: fdc9db29-e6b0-45d2-a879-8bd60e2058a7
ms.openlocfilehash: 585ec8720a654bbcb728330d70ddb914f2543e41
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62239736"
---
# <a name="mfc-activex-controls-accessing-ambient-properties"></a>MFC – ovládací prvky ActiveX: Přístup k vedlejším vlastnostem

Tento článek popisuje, jak ovládací prvek ActiveX lze získat přístup k vedlejším vlastnostem jeho kontejneru ovládacího prvku.

Ovládací prvek můžete získat informace o jeho kontejneru přístup k vedlejším vlastnostem kontejneru. Tyto vlastnosti zpřístupnit vizuální vlastnosti, například barvu pozadí kontejneru, aktuální písmo použité kontejneru a provozních charakteristik, například, jestli je kontejner právě v uživatelském režimu nebo režimu návrháře. Ovládací prvek můžete přizpůsobit její vzhled a chování pro konkrétní kontejner, ve kterém se vloží vedlejším vlastnostem. Nicméně ovládací prvek by měl Nikdy nepředpokládejte, že její kontejner bude podporovat všechny konkrétní vedlejší vlastnost. Některé kontejnery ve skutečnosti nemusí podporovat všechny vedlejším vlastnostem vůbec. Chybí vlastnost ambient ovládací prvek by měl předpokládat rozumnou výchozí hodnotu.

Pro přístup k vlastnosti ambient. Ujistěte se, volání [COleControl::GetAmbientProperty](../mfc/reference/colecontrol-class.md#getambientproperty). Tato funkce očekává, že dispatch ID pro vlastnost okolí jako první parametr (soubor OLECTL. Dispatch ID pro standardní sadu vedlejším vlastnostem definuje H).

Parametry `GetAmbientProperty` funkce jsou Identifikátor odeslání variant značky označující očekávaný typ vlastnosti a ukazatel na paměť, kde má být vrácen hodnoty. Typ dat, na který odkazuje tento ukazatel se liší v závislosti na typu variant značky. Funkce vrátí **TRUE** Pokud kontejner podporuje vlastnost, v opačném případě vrátí **FALSE**.

Následující příklad kódu získá hodnotu okolí vlastnosti s názvem "Přesměrovač." Pokud vlastnost není podporována v kontejneru, výchozí hodnota **TRUE** se předpokládá, že:

[!code-cpp[NVC_MFC_AxUI#30](../mfc/codesnippet/cpp/mfc-activex-controls-accessing-ambient-properties_1.cpp)]

Pro usnadnění práce `COleControl` poskytuje pomocné funkce, které přístup k mnoha běžně používaných vlastnosti prostředí a vracet vhodné výchozí nastavení vlastnosti nejsou k dispozici. Tyto pomocné funkce jsou následující:

- [COleControl::AmbientBackColor](../mfc/reference/colecontrol-class.md#ambientbackcolor)

- [AmbientDisplayName](../mfc/reference/colecontrol-class.md#ambientdisplayname)

- [AmbientFont](../mfc/reference/colecontrol-class.md#ambientfont)

    > [!NOTE]
    >  Volající musí volat `Release( )` na vrácené písma.

- [AmbientForeColor](../mfc/reference/colecontrol-class.md#ambientforecolor)

- [AmbientLocaleID](../mfc/reference/colecontrol-class.md#ambientlocaleid)

- [AmbientScaleUnits](../mfc/reference/colecontrol-class.md#ambientscaleunits)

- [AmbientTextAlign](../mfc/reference/colecontrol-class.md#ambienttextalign)

- [AmbientUserMode](../mfc/reference/colecontrol-class.md#ambientusermode)

- [AmbientUIDead](../mfc/reference/colecontrol-class.md#ambientuidead)

- [AmbientShowHatching](../mfc/reference/colecontrol-class.md#ambientshowhatching)

- [AmbientShowGrabHandles](../mfc/reference/colecontrol-class.md#ambientshowgrabhandles)

Pokud se změní hodnotu k vlastnosti ambient. (přes určitou akci kontejneru), `OnAmbientPropertyChanged` volat členské funkce ovládacího prvku. Potlačí tuto členskou funkci pro zpracování takové oznámení. Parametr `OnAmbientPropertyChanged` je ID odbavení ovlivněné vedlejší vlastnost. Hodnota tuto hodnotu dispatch ID může být DISPID_UNKNOWN, což znamená, že došlo ke změně vlastnosti jednoho nebo více prostředí, ale není k dispozici informace o tom, které měla vliv na vlastnosti.

## <a name="see-also"></a>Viz také:

[MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)
