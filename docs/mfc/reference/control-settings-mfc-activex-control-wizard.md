---
title: Nastavení ovládacího prvku, Průvodce ovládacím prvkem ActiveX knihovny MFC | Dokumentace Microsoftu
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
ms.openlocfilehash: db62ce0770199b3a928e3f01c04b7f0600ad2dcd
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/05/2018
ms.locfileid: "37853712"
---
# <a name="control-settings-mfc-activex-control-wizard"></a>Nastavení ovládacího prvku, Průvodce ovládacím prvkem ActiveX v prostředí MFC
Tato stránka průvodce slouží k určení způsobu chování ovládacího prvku. Například můžete založit na ovládací prvek na standardní typy ovládacích prvků Windows, optimalizace jeho chování a vzhledu nebo označuje, zda ovládací prvek může sloužit jako kontejner pro ostatní ovládací prvky.  
  
 Další informace o tom, jak vybrat možnosti na této stránce pro maximalizaci efektivity ovládacího prvku, naleznete v tématu [knihovny MFC – ovládací prvky ActiveX: optimalizace](../../mfc/mfc-activex-controls-optimization.md).  
  
## <a name="uielement-list"></a>Seznam prvků uživatelského rozhraní  
 **Vytvoření ovládacího prvku na základě**  
 V tomto seznamu můžete vybrat typ ovládacího prvku, ze kterého by měla dědit ovládacího prvku. V seznamu je podmnožinou třídy ovládacích prvků, které jsou k dispozici pro `CreateWindowEx` a další běžné ovládací prvky, které jsou určené v commctrl.h. Váš výběr určuje styl ovládacího prvku `PreCreateWindow` fungovat v *název_projektu*Ctrl.cpp souboru. Další informace najdete v tématu [knihovny MFC – ovládací prvky ActiveX: vytvoření podtřídy ovládacího prvku Windows](../../mfc/mfc-activex-controls-subclassing-a-windows-control.md).  
  
|Ovládací prvek|Popis|  
|-------------|-----------------|  
|**TLAČÍTKO**|Ovládací prvek tlačítka Windows|  
|**POLE SE SEZNAMEM**|Ovládací prvek pole se seznamem Windows|  
|**UPRAVIT**|Ovládací prvek Windows upravit pole|  
|**LISTBOX**|Ovládací prvek Windows seznam|  
|**POSUVNÍK**|Ovládací prvek posuvníku Windows|  
|**STATICKÁ**|Statický ovládací prvek Windows|  
|**msctls_hotkey32**|Výměně klíčů běžného ovládacího prvku|  
|**msctls_progress32**|Indikátor běžný ovládací prvek|  
|**msctls_statusbar32**|Stavový řádek běžný ovládací prvek|  
|**msctls_trackbar32**|Sledování panelu běžný ovládací prvek|  
|**msctls_updown32**|Tlačítko typu číselník (nebo nahoru dolů) běžný ovládací prvek|  
|**SysAnimate32**|Běžné ovládacího prvku animace|  
|**SysHeader32**|Běžného ovládacího prvku záhlaví|  
|**SysListView32**|Seznam zobrazení běžného ovládacího prvku|  
|**SysTabControl32**|Běžné ovládací prvek karty|  
|**SysTreeView32**|Běžné stromovém zobrazení|  
  
 **Aktivuje se, když je viditelné**  
 Určuje, že okno při přístupu k vytvoření ovládacího prvku. Ve výchozím nastavení **aktivuje, když je viditelné** je vybraná možnost. Pokud budete chtít odložit Aktivace ovládacího prvku, dokud kontejneru vyžaduje (například když uživatel klikne myší), zrušte tuto možnost. Když tato funkce je vypnutá, nejsou spojené ovládací prvek vynakládat vytvoření oken, dokud je povinný. Další informace najdete v tématu [vypnutí možnosti Activate When viditelné](../../mfc/turning-off-the-activate-when-visible-option.md).  
  
 **Neviditelné při spuštění**  
 Určuje, zda ovládací prvek nemá žádné uživatelské rozhraní v době běhu. Časovač je druh ovládacího prvku, který může být vhodné byla neviditelná.  
  
 **Má dialogové okno o**  
 Určuje, zda ovládací prvek má standardní Windows **o** dialogové okno, které se zobrazuje číslo verze a informace o autorských právech.  
  
> [!NOTE]
>  Jak uživatel přistupuje k nápovědu pro ovládací prvek závisí na tom, jak jste implementovali nápovědy a určuje, zda jste integrovali Nápověda ovládacího prvku pomocí kontejneru. Další informace o tom, jak integrovat nápovědy, na [knihovny MSDN](http://go.microsoft.com/fwlink/p/?linkid=150542) webu, vyhledejte "Přidání Context-Sensitive nápovědy pro MFC ovládací prvek ActiveX".  
  
 Když vyberete tuto možnost, vloží `AboutBox` řídit metody ve třídě ovládacího prvku projektu (C*název_projektu*Ctrl.cpp) a přidá AboutBox mapa odeslání projektu. Ve výchozím nastavení je tato možnost vybrána.  
  
 **Optimalizovaný kód pro vykreslování.**  
 Určuje, že kontejner obnoví původní objekty GDI automaticky všechny ovládací prvky kontejneru, které jsou vykreslovány stejný kontext zařízení, byl nakreslen diagram. Další informace o této funkci najdete v tématu [optimalizace vykreslování ovládacích prvků](../../mfc/optimizing-control-drawing.md).  
  
 **Aktivace bez oken**  
 Určuje, že ovládací prvek nevytváří okno při aktivaci. Aktivace bez oken umožňuje vytvoření nepravoúhlého nebo transparentní ovládacích prvků a ovládací prvek bez oken vyžaduje méně režie systému než ovládací prvek, který se má okno vyžaduje. Ovládací prvek bez oken neoříznutého kontextu zařízení nebo aktivace bez blikání nepovoluje. Kontejnery, které byly vytvořeny před 1996 nepodporují aktivace bez oken. Další informace o tom, jak použít tuto možnost najdete v tématu [zajištění aktivace bez oken](../../mfc/providing-windowless-activation.md).  
  
 **Neoříznutého kontextu zařízení**  
 Přepíše [COleControl::GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags) v záhlaví ovládacího prvku (*název_projektu*ctrl.h) Chcete-li zakázat volání `IntersectClipRect` provedené `COleControl`. Když vyberete tuto možnost, poskytuje výhody malé rychlost. Pokud vyberete **aktivace bez oken**, tato funkce není k dispozici. Další informace najdete v tématu [použití Neoříznutého kontextu zařízení](../../mfc/using-an-unclipped-device-context.md).  
  
 **Aktivace bez blikání**  
 Eliminuje výkresu operace a související vizuální blikání, ke kterým dochází mezi aktivní a neaktivní stavy ovládacího prvku. Pokud vyberete **aktivace bez oken**, tato funkce není k dispozici. Když nastavíte tuto možnost, `noFlickerActivate` příznak je jedním z příznaky, které jsou vrácené [COleControl::GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags). Další informace najdete v tématu [zajištění aktivace bez blikání](../../mfc/providing-flicker-free-activation.md).  
  
 **K dispozici v dialogu vložit objekt**  
 Určuje, že bude k dispozici v ovládacím prvku **vložit objekt** dialogové okno pro povolené kontejnery. Když vyberete tuto možnost `afxRegInsertable` příznak je jedním z příznaky, které jsou vrácené `AfxOleRegisterControlClass`. S použitím **vložit objekt** dialogovém okně můžete vložit nově vytvořený uživatel nebo existujících objektů do složeného dokumentu.  
  
 **Oznámení ukazatel myši, pokud je neaktivní.**  
 Umožňuje řízení zpracovat oznámení ukazatel myši, zda ovládací prvek je nebo není aktivní. Když vyberete tuto možnost `pointerInactive` příznak je jedním z příznaky, které jsou vrácené [COleControl::GetControlFlags](../../mfc/reference/colecontrol-class.md#getcontrolflags). Další informace o tom, jak použít tuto možnost najdete v tématu [poskytuje myši interakce při neaktivní](../../mfc/providing-mouse-interaction-while-inactive.md).  
  
 **Funguje jako jednoduchý rámečku ovládacího prvku**  
 Určuje, zda ovládací prvek kontejneru pro ostatní ovládací prvky tak, že nastavíte OLEMISC_SIMPLEFRAME bit ovládacího prvku. Další informace najdete v [knihovny MSDN](http://go.microsoft.com/fwlink/p/?linkid=150542) webu, vyhledejte "Jednoduché rámeček webu členství ve skupině".  
  
 **Asynchronně načte vlastnosti**  
 Umožňuje obnovit všechny předchozí asynchronní dat a zahájí nového zatížení asynchronní vlastnosti ovládacího prvku.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce ovládacím prvkem ActiveX knihovny MFC](../../mfc/reference/mfc-activex-control-wizard.md)   
 [Nastavení aplikace, Průvodce ovládacím prvkem ActiveX knihovny MFC](../../mfc/reference/application-settings-mfc-activex-control-wizard.md)   
 [Názvy ovládacích prvků, Průvodce ovládacím prvkem ActiveX v prostředí MFC](../../mfc/reference/control-names-mfc-activex-control-wizard.md)

