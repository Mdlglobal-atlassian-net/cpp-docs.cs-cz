---
title: Nastavení ovládacího prvku, Průvodce ovládacím prvkem ActiveX knihovny MFC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- vc.appwiz.mfc.ctl.settings
dev_langs:
- C++
helpviewer_keywords:
- MFC ActiveX Control Wizard, control settings
ms.assetid: 2ccaa4fc-0d52-413e-afa3-ecd474c3f6f0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2161cea739d918bc0f5772a6cb08c29082a6e670
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33371859"
---
# <a name="control-settings-mfc-activex-control-wizard"></a>Nastavení ovládacího prvku, Průvodce ovládacím prvkem ActiveX v prostředí MFC
Na této stránce průvodce můžete určit způsob řízení chovat. Můžete například základní ovládacího prvku na standardní typy ovládacích prvků Windows, optimalizaci chování a vzhled nebo znamenat, že ovládací prvek může fungovat jako kontejner pro další ovládací prvky.  
  
 Další informace o tom, jak vybrat možnosti na této stránce maximalizovat efektivitu ovládacího prvku najdete v tématu [MFC – ovládací prvky ActiveX: optimalizace](../../mfc/mfc-activex-controls-optimization.md).  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **Vytvoření ovládacího prvku na základě**  
 V tomto seznamu můžete vybrat typ ovládacího prvku, ze kterého mají přebírat vlastního ovládacího prvku. V seznamu je podmnožinou třídy ovládacích prvků, které jsou k dispozici pro `CreateWindowEx` a další běžné ovládací prvky, které jsou určené v commctrl.h. Výběr určuje styl ovládacího prvku `PreCreateWindow` v fungovat *ProjName*Ctrl.cpp souboru. Další informace najdete v tématu [MFC – ovládací prvky ActiveX: vytvoření podtřídy ovládacího prvku Windows](../../mfc/mfc-activex-controls-subclassing-a-windows-control.md).  
  
|Ovládací prvek|Popis|  
|-------------|-----------------|  
|**TLAČÍTKO**|Tlačítko ovládacího prvku Windows|  
|**POLE SE SEZNAMEM**|Ovládací prvek Windows pole se seznamem|  
|**UPRAVIT**|Ovládací prvek Windows úpravy|  
|**LISTBOX**|Ovládací prvek Windows seznam|  
|**SCROLLBAR**|Ovládací prvek Windows posuvníku|  
|**STATICKÉ**|Statické ovládacího prvku Windows|  
|**msctls_hotkey32**|Běžné ovládacího prvku klávesová zkratka|  
|**msctls_progress32**|Průběh panelu běžného ovládacího prvku|  
|**msctls_statusbar32**|Stavový řádek běžného ovládacího prvku|  
|**msctls_trackbar32**|Sledování panelu běžného ovládacího prvku|  
|**msctls_updown32**|Tlačítko typu číselník (nebo obousměrný číselník) běžného ovládacího prvku|  
|**SysAnimate32**|Běžné ovládacího prvku animace|  
|**SysHeader32**|Běžného ovládacího prvku záhlaví|  
|**SysListView32**|Seznam zobrazení běžného ovládacího prvku|  
|**SysTabControl32**|Běžné ovládacího prvku karta|  
|**SysTreeView32**|Stromové zobrazení běžného ovládacího prvku|  
  
 **Aktivuje, když viditelné**  
 Určuje, zda okno vytvořit pro ovládací prvek při přístupu. Ve výchozím nastavení **aktivuje, když viditelné** je vybraná možnost. Pokud chcete odložení aktivace ovládacího prvku, dokud kontejneru vyžaduje (například když uživatel klikne na tlačítko myši), zrušte tuto možnost. Když tato funkce je vypnutá, ovládacího prvku nedojde nákladů na vytvoření oken dokud je vyžadována. Další informace najdete v tématu [vypnutí aktivovat při viditelné možnost](../../mfc/turning-off-the-activate-when-visible-option.md).  
  
 **Neviditelné za běhu**  
 Určuje, že ovládací prvek nemá žádné uživatelské rozhraní za běhu. Časovač je druh ovládací prvek, který můžete chtít byla neviditelná.  
  
 **Má to o pole dialog**  
 Určuje, že ovládací prvek je standardní Windows **o** dialogové okno, které zobrazuje číslo verze a informace o autorských právech.  
  
> [!NOTE]
>  Jak uživatel přistupuje k nápovědy pro ovládací prvek závisí na tom, jak jste implementovali v nápovědě a jestli mají integrované Nápověda ovládacího prvku kontejner pomocí. Další informace o tom, jak integrovat nápovědy, na [knihovně MSDN](http://go.microsoft.com/fwlink/p/?linkid=150542) webu, vyhledejte "Přidání Context-Sensitive pomoci pro MFC ovládací prvek ActiveX".  
  
 Když vyberete tuto možnost, vloží `AboutBox` řídit metodu v třídě řízení projektu (C*ProjName*Ctrl.cpp) a přidá AboutBox do mapy odeslání projektu. Ve výchozím nastavení je tato možnost vybrána.  
  
 **Optimalizovaný kód kreslení**  
 Určuje, že kontejner obnoví původní objekty GDI automaticky po všechny ovládací prvky kontejneru, které jsou vykreslovány stejné kontextu zařízení, byly. Další informace o této funkci najdete v tématu [optimalizace vykreslování ovládacích prvků](../../mfc/optimizing-control-drawing.md).  
  
 **Aktivace bez oken**  
 Určuje, že ovládací prvek nevytváří okno při aktivaci. Umožňuje aktivace bez oken pro ovládací prvky nepravoúhlý nebo transparentní a vyžaduje menší nároky na systému než ovládací prvek, který má okno vyžaduje ovládacího prvku bez oken. Bez oken ovládací prvek pro neoříznutého kontextu zařízení nebo aktivace bez blikání nepovoluje. Kontejnery, které byly vytvořeny před 1996 nepodporují aktivace bez oken. Další informace o tom, jak použít tuto možnost najdete v tématu [zajištění aktivace bez oken](../../mfc/providing-windowless-activation.md).  
  
 **Neoříznutého kontextu zařízení**  
 Přepsání [COleControl::GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags) v ovládacího prvku záhlaví (*projname*ctrl.h) Chcete-li zakázat volání `IntersectClipRect` provedené `COleControl`. Když vyberete tuto možnost, poskytuje výhody malé rychlost. Pokud vyberete **aktivace bez oken**, tato funkce není k dispozici. Další informace najdete v tématu [použití Neoříznutého kontextu zařízení](../../mfc/using-an-unclipped-device-context.md).  
  
 **Aktivace bez blikání**  
 Eliminuje kreslení operace a doprovodné visual blikání, ke kterým dochází mezi stavy aktivní i neaktivní ovládacího prvku. Pokud vyberete **aktivace bez oken**, tato funkce není k dispozici. Pokud nastavíte tuto možnost `noFlickerActivate` příznak je příznaky, které se vrátí pomocí [COleControl::GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags). Další informace najdete v tématu [zajištění aktivace bez blikání](../../mfc/providing-flicker-free-activation.md).  
  
 **K dispozici v dialogovém okně Vložit objekt**  
 Určuje, že bude k dispozici v ovládacím prvku **vložit objekt** dialogové okno pro kontejnery povoleno. Když vyberete tuto možnost, `afxRegInsertable` příznak je příznaky, které se vrátí pomocí `AfxOleRegisterControlClass`. Pomocí **vložit objekt** dialogové okno, může uživatel vkládat nově vytvořený nebo existující objekty do složeného dokumentu.  
  
 **Oznámení ukazatele myši při neaktivní**  
 Umožňuje řízení pro proces oznámení ukazatel myši, zda řízení je aktivní, nebo ne. Když vyberete tuto možnost, `pointerInactive` příznak je příznaky, které se vrátí pomocí [COleControl::GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags). Další informace o tom, jak použít tuto možnost najdete v tématu [poskytování myši interakce při neaktivní](../../mfc/providing-mouse-interaction-while-inactive.md).  
  
 **Jednání jako jednoduchý rámeček ovládací prvek**  
 Určuje, že ovládací prvek je kontejner pro další ovládací prvky podle nastavení `OLEMISC_SIMPLEFRAME` bit pro ovládací prvek. Další informace najdete na [knihovny MSDN](http://go.microsoft.com/fwlink/p/?linkid=150542) webu, vyhledejte "Jednoduché rámce lokality omezení".  
  
 **Asynchronně načte vlastnosti**  
 Umožňuje provést obnovení žádná předchozí asynchronní data a zahájí nového zatížení asynchronní vlastnosti ovládacího prvku.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce ovládacím prvkem ActiveX knihovny MFC](../../mfc/reference/mfc-activex-control-wizard.md)   
 [Nastavení aplikace, Průvodce ovládacím prvkem ActiveX knihovny MFC](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)   
 [Názvy ovládacích prvků, Průvodce ovládacím prvkem ActiveX v prostředí MFC](../../mfc/reference/control-names-mfc-activex-control-wizard.md)

