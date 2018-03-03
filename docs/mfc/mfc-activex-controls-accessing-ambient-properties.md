---
title: "Ovládací prvky MFC ActiveX: Přístup k vedlejším vlastnostem | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX controls [MFC], accessing ambient properties
- properties [MFC], accessing ambient
ms.assetid: fdc9db29-e6b0-45d2-a879-8bd60e2058a7
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b05e6d37a0550cf157dcd43a22689c9db029b51f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="mfc-activex-controls-accessing-ambient-properties"></a>MFC – ovládací prvky ActiveX: Přístup k vedlejším vlastnostem
Tento článek popisuje, jak ovládacího prvku ActiveX má přístup k vedlejším vlastnostem svého kontejneru ovládacího prvku.  
  
 Ovládací prvek můžete získat informace o jeho kontejneru přístup k vedlejším vlastnostem kontejneru. Tyto vlastnosti vystavit visual charakteristiky, jako je například barva pozadí kontejneru, aktuální písmo použité k kontejneru a provozní charakteristiky, jako jestli kontejneru je aktuálně v režimu uživatele nebo návrháře. Ovládací prvek lze přizpůsobit její vzhled a chování konkrétním kontejneru, ve kterém je integrovaný vedlejším vlastnostem. Však ovládacího prvku by nikdy Předpokládejme, že jeho kontejner bude podporovat všechny konkrétní vedlejším vlastnosti. Některé kontejnery ve skutečnosti nemusí podporovat všechny vedlejším vlastnostem vůbec. Chybí vedlejší vlastnost musí ovládacího prvku předpokládají přiměřené výchozí hodnotu.  
  
 Pro přístup k vedlejším vlastnost, ujistěte se, volání [COleControl::GetAmbientProperty](../mfc/reference/colecontrol-class.md#getambientproperty). Tato funkce očekává ID odesílání pro vlastnost vedlejším jako první parametr (soubor OLECTL. Odesílání ID pro standardní sadu vedlejším vlastnostem definuje H).  
  
 Parametry `GetAmbientProperty` funkce jsou odesílání ID, variant značku označující typ očekávaný vlastností a ukazatel na paměti, kde má být vrácen hodnota. Typ dat, na který odkazuje tento ukazatel se bude lišit v závislosti na typu variant značky. Funkce vrátí hodnotu **TRUE** Pokud kontejner podporuje vlastnost, jinak vrátí **FALSE**.  
  
 Následující příklad kódu získá hodnotu vedlejším vlastnosti s názvem "Uživatelského režimu." Pokud je vlastnost nepodporuje kontejneru, výchozí hodnota je **TRUE** se předpokládá, že:  
  
 [!code-cpp[NVC_MFC_AxUI#30](../mfc/codesnippet/cpp/mfc-activex-controls-accessing-ambient-properties_1.cpp)]  
  
 Pro usnadnění vaší práce `COleControl` poskytuje pomocných funkcí, které přístup k mnoha běžně používané vedlejším vlastnostem a vracet vhodné výchozí nastavení vlastnosti nejsou k dispozici. Tyto pomocné funkce jsou následující:  
  
-   [COleControl::AmbientBackColor](../mfc/reference/colecontrol-class.md#ambientbackcolor)  
  
-   [AmbientDisplayName](../mfc/reference/colecontrol-class.md#ambientdisplayname)  
  
-   [AmbientFont](../mfc/reference/colecontrol-class.md#ambientfont)  
  
    > [!NOTE]
    >  Volající musí volat **verze ()** na vrácený písmo.  
  
-   [AmbientForeColor](../mfc/reference/colecontrol-class.md#ambientforecolor)  
  
-   [AmbientLocaleID](../mfc/reference/colecontrol-class.md#ambientlocaleid)  
  
-   [AmbientScaleUnits](../mfc/reference/colecontrol-class.md#ambientscaleunits)  
  
-   [AmbientTextAlign](../mfc/reference/colecontrol-class.md#ambienttextalign)  
  
-   [AmbientUserMode](../mfc/reference/colecontrol-class.md#ambientusermode)  
  
-   [AmbientUIDead](../mfc/reference/colecontrol-class.md#ambientuidead)  
  
-   [AmbientShowHatching](../mfc/reference/colecontrol-class.md#ambientshowhatching)  
  
-   [AmbientShowGrabHandles](../mfc/reference/colecontrol-class.md#ambientshowgrabhandles)  
  
 Pokud se změní hodnota vedlejším vlastnosti (prostřednictvím některé akce kontejneru), **OnAmbientPropertyChanged** členské funkce ovládacího prvku. Člen funkci pro zpracování toto oznámení přepište. Parametr pro **OnAmbientPropertyChanged** je odesílání ID ovlivněných vedlejší vlastnost. Může být hodnota parametru toto ID odesílání **DISPID_UNKNOWN**, což naznačuje, že jeden nebo více vedlejším vlastnostem došlo ke změně, ale není k dispozici informace o tom, které situace měla vliv na vlastnosti.  
  
## <a name="see-also"></a>Viz také  
 [MFC – ovládací prvky ActiveX](../mfc/mfc-activex-controls.md)

