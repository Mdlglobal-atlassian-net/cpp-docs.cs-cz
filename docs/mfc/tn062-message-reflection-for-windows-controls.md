---
title: "TN062: Zpráva reflexe pro ovládací prvky Windows | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.controls.messages
dev_langs:
- C++
helpviewer_keywords:
- ON_WM_VKEYTOITEM_REFLECT macro [MFC]
- ON_WM_DRAWITEM_REFLECT macro [MFC]
- ON_WM_VSCROLL_REFLECT macro [MFC]
- ON_NOTIFY_REFLECT message [MFC]
- ON_CONTROL_REFLECT_EX macro [MFC]
- ON_UPDATE_COMMAND_UI_REFLECT macro [MFC]
- ON_NOTIFY_REFLECT_EX message [MFC]
- ON_WM_HSCROLL_REFLECT macro [MFC]
- message reflection [MFC]
- ON_WM_COMPAREITEM_REFLECT macro [MFC]
- ON_WM_MEASUREITEM_REFLECT macro [MFC]
- ON_NOTIFY message [MFC]
- WM_COMMAND [MFC]
- WM_CTLCOLOR message [MFC]
- TN062 [MFC]
- ON_WM_CHARTOITEM_REFLECT macro [MFC]
- ON_WM_CTLCOLOR_REFLECT macro [MFC]
- ON_WM_DELETEITEM_REFLECT macro [MFC]
- notification messages [MFC]
- ON_WM_PARENTNOTIFY_REFLECT macro [MFC]
- WM_NOTIFY message [MFC]
- ON_CONTROL_REFLECT macro
ms.assetid: 53efb0ba-fcda-4fa0-a3c7-14e0b78fb494
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: bdf9a0dd227cb54ba85c85901f706966326b1b66
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="tn062-message-reflection-for-windows-controls"></a>TN062: Reflexe zprávy pro ovládací prvky Windows
> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována vzhledem k tomu, že byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata může být zastaralý nebo není správný. Nejnovější informace se doporučuje, vyhledejte téma týkající se v indexu online dokumentaci.  
  
 Tato technická Poznámka popisuje reflexe zpráv, nová funkce v MFC 4.0. Obsahuje taky pokyny pro vytvoření jednoduché opakovaně použitelné ovládací prvek, který používá reflexe zpráv.  
  
 Tato technická Poznámka nezaměřuje reflexe zprávy, která se vztahuje na ovládací prvky ActiveX (dříve se označovaly jako ovládací prvky OLE). Podrobnosti najdete v článku [– ovládací prvky ActiveX: vytvoření podtřídy ovládacího prvku Windows](../mfc/mfc-activex-controls-subclassing-a-windows-control.md).  
  
 **Co je reflexe zpráv**  
  
 Ovládací prvky Windows často zasílání oznámení k jejich nadřazené systému windows. Například mnoho ovládacích prvků odeslat zprávu oznámení ovládacího prvku barvu (`WM_CTLCOLOR` nebo jednoho z jeho variant) k jejich nadřazené umožňující nadřazené k poskytování štětce pro vykreslování pozadí ovládacího prvku.  
  
 V systému Windows a v prostředí MFC před verze 4.0 nadřazené okno, často dialogového okna, je zodpovědná za zpracování těchto zpráv. To znamená, že kód pro zpracování zprávy musí být v třídě nadřazeného okna a že má zkopírovat do každá třída, kterou je zpracování této zprávy. V případě výše každých dialogu, který chtěli ovládacích prvků pomocí vlastní pozadí musel zpracování oznámení ovládacího prvku barev. Je mnohem jednodušší znovu použít kód, pokud lze zapsat třída ovládacích prvků, které se zpracovávají barvu pozadí.  
  
 V MFC 4.0, původní mechanismus stále funguje – windows nadřazené dokáže zpracovat zprávy s oznámením. Kromě toho však MFC 4.0 usnadňuje opakované použití tím, že poskytuje funkci "zpráva reflexe", který umožňuje zpracovávat v okně řízení podřízené nebo nadřazené okno, nebo v obou těchto zpráv s oznámením. V příkladu barvu pozadí ovládacího prvku, teď můžete napsat řízení třídu, která nastaví barvu pozadí ve zpracování reflektované `WM_CTLCOLOR` zpráva – aniž byste museli spoléhat na nadřazený. (Všimněte si, že vzhledem k tomu, že reflexe zpráv je implementováno modulem MFC, v systému Windows, nadřazené třídy okna nesmí být odvozen od `CWnd` pro reflexe zprávy pro práci.)  
  
 Starší verze knihovny MFC se něco podobného jako reflexe zpráv tím, že poskytuje virtuální funkce pro několik zprávy, jako je například zprávy pro seznamy vykreslovaných vlastníkem (`WM_DRAWITEM`a tak dále). Nového mechanismu reflexe zprávy je zobecněný a konzistentní.  
  
 Reflexe zpráv je zpětně kompatibilní s kódu napsaného pro verze knihovny MFC než 4.0.  
  
 Pokud jste zadali obslužnou rutinu pro konkrétní zprávou, nebo pro celou řadu zprávy do nadřazeného okna třídy, se přepíší projeví obslužné rutiny zpráv pro stejnou zprávu zadaný nemůžete volat základní třídu obslužné rutiny ve vaší vlastní obslužné rutiny. Například, pokud zpracováváte `WM_CTLCOLOR` ve vaší třídy dialogového okna, vaše zpracování přepíší všechny rutiny zrcadlené zprávy.  
  
 Pokud v okně vaší nadřazené třídy zadáte obslužnou rutinu pro konkrétní **wm_notify –** zpráva nebo rozsah **wm_notify –** zprávy, vaší obslužné rutiny bude volán, pouze pokud nemá podřízený ovládací prvek odesílání těchto zpráv není nutné obslužná rutina zrcadlené zprávy prostřednictvím **ON_NOTIFY_REFLECT()**. Pokud používáte **ON_NOTIFY_REFLECT_EX()** mapy zpráv vaší obslužné rutiny zpráv může nebo nemusí umožňovat nadřazeného okna pro zpracování zprávy. Pokud obslužná rutina vrátí **FALSE**, zpráva bude zpracován adresou nadřazené taky při volání, které vrátí **TRUE** neumožňuje nadřazené se nezdařilo. Upozorňujeme, že je před oznámení zajistit zrcadlené zprávy.  
  
 Když **wm_notify –** je odeslána zpráva, ovládacího prvku se nabízí první příležitosti se nezdařilo. Pokud se pošle další zrcadlené zprávy nadřazeného okna má první příležitosti se nezdařilo a ovládacího prvku obdrží zrcadlené zprávy. Uděláte to tak, bude je nutné funkce obslužné rutiny a odpovídající položku v mapy zpráv třídy ovládacího prvku.  
  
 Makra map zpráv pro zrcadlené zprávy se poněkud liší od pravidelných oznámení: má **_REFLECT** připojí k jeho obvyklé názvu. Například pro zpracování **wm_notify –** zpráva v nadřazené, použijte makro `ON_NOTIFY` v mapy zpráv nadřazeného objektu. Zpracování reflektovaných zpráv v ovládacím prvku podřízené, použijte **on_notify_reflect –** makro v mapy zpráv podřízeného ovládacího prvku. V některých případech parametry se liší, také. Všimněte si, ClassWizard můžete obvykle přidávat položky mapy zpráv pro vás a poskytovat implementace kostru funkce se správnými parametry.  
  
 V tématu [TN061: ON_NOTIFY a wm_notify – zprávy](../mfc/tn061-on-notify-and-wm-notify-messages.md) informace o nové **wm_notify –** zprávy.  
  
 **Mapy zpráv položek a prototypy funkcí obslužné rutiny pro Reflektované zprávy**  
  
 Zpracování oznámení reflektované řízení, použijte makra map zpráv a prototypy funkcí, které jsou uvedené v následující tabulce.  
  
 ClassWizard můžete obvykle přidejte tyto položky mapy zpráv pro vás a poskytovat implementace kostru funkce. V tématu [definování obslužné rutiny zpráv pro zprávu projeví](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md) informace o tom, jak definovat obslužné rutiny pro zrcadlené zprávy.  
  
 Převést z název zprávy k názvu reflektované makro, předřadit **ON_** a připojte **_REFLECT**. Například `WM_CTLCOLOR` stane **on_wm_ctlcolor_reflect –**. (Zprávy, které může projevit najdete proveďte převod opačně orientované na makro položky v následující tabulce.)  
  
 Tři výjimky pro výše uvedené pravidlo jsou následující:  
  
-   Makro pro **wm_command –** oznámení je **on_control_reflect –**.  
  
-   Makro pro **wm_notify –** odrazů je **on_notify_reflect –**.  
  
-   Makro pro `ON_UPDATE_COMMAND_UI` odrazů je **on_update_command_ui_reflect –**.  
  
 V každé z výše uvedených zvláštních případech musíte zadat název členské funkce obslužné rutiny. V ostatních případech musíte použít standardní název funkce obslužné rutiny.  
  
 Významy parametry a návratové hodnoty funkce popsané v části název funkce nebo název funkce s **na** přidá jako předpona. Například **CtlColor** je popsána v `OnCtlColor`. Obslužné rutiny několik zrcadlené zprávy potřebovat méně parametrů, než podobně jako obslužné rutiny v nadřazené okno. Právě odpovídat názvům v následující tabulce s názvy formální parametry v dokumentaci.  
  
|Položku mapování|Prototyp funkce|  
|---------------|------------------------|  
|**ON_CONTROL_REFLECT – (** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg void** `memberFxn` **();**|  
|**ON_NOTIFY_REFLECT – (** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg void** `memberFxn` **(NMHDR \***  `pNotifyStruct` **, LRESULT\***  *výsledek* **);**|  
|**ON_UPDATE_COMMAND_UI_REFLECT – (** `memberFxn` **)**|**afx_msg void** `memberFxn` **(CCmdUI\***  `pCmdUI` **);**|  
|**ON_WM_CTLCOLOR_REFLECT –)**|**afx_msg HBRUSH CtlColor (CDC\***  `pDC` **, UINT** `nCtlColor` **);**|  
|**ON_WM_DRAWITEM_REFLECT –)**|**DrawItem – void afx_msg (LPDRAWITEMSTRUCT** `lpDrawItemStruct` **);**|  
|**ON_WM_MEASUREITEM_REFLECT –)**|**measureitem – void afx_msg (LPMEASUREITEMSTRUCT** `lpMeasureItemStruct` **);**|  
|**ON_WM_DELETEITEM_REFLECT –)**|**afx_msg void DeleteItem (LPDELETEITEMSTRUCT** `lpDeleteItemStruct` **);**|  
|**ON_WM_COMPAREITEM_REFLECT –)**|**afx_msg int CompareItem (LPCOMPAREITEMSTRUCT** `lpCompareItemStruct` **);**|  
|**ON_WM_CHARTOITEM_REFLECT –)**|**afx_msg int CharToItem (Celé_číslo** `nKey` **, UINT** `nIndex` **);**|  
|**ON_WM_VKEYTOITEM_REFLECT –)**|**afx_msg int VKeyToItem (Celé_číslo** `nKey` **, UINT** `nIndex` **);**|  
|**ON_WM_HSCROLL_REFLECT –)**|**afx_msg void HScroll (Celé_číslo** `nSBCode` **, UINT** `nPos` **);**|  
|**ON_WM_VSCROLL_REFLECT –)**|**afx_msg void VScroll (Celé_číslo** `nSBCode` **, UINT** `nPos` **);**|  
|**ON_WM_PARENTNOTIFY_REFLECT –)**|**afx_msg void ParentNotify (Celé_číslo** `message` **, LPARAM** `lParam` **);**|  
  
 **On_notify_reflect –** a **on_control_reflect –** makra mají varianty, které umožňují více než jeden objekt (například ovládací prvek a jeho nadřazený objekt) pro zpracování danou zprávou.  
  
|Položku mapování|Prototyp funkce|  
|---------------|------------------------|  
|**ON_NOTIFY_REFLECT_EX – (** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg BOOL** `memberFxn` **(NMHDR \***  `pNotifyStruct` **, LRESULT\***  *výsledek* **);**|  
|**ON_CONTROL_REFLECT_EX – (** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg BOOL** `memberFxn` **();**|  
  
## <a name="handling-reflected-messages-an-example-of-a-reusable-control"></a>Zpracování zpráv Reflected: Příklad opakovaně použitelné ovládací prvek  
 Tento jednoduchý příklad vytvoří opakovaně použitelné ovládací prvek názvem `CYellowEdit`. Ovládací prvek funguje stejně jako regulární textové pole s tím rozdílem, že se zobrazí černý text na pozadí žluté. Je snadno přidat členské funkce, která umožňují `CYellowEdit` řízení k zobrazení různých barev.  
  
#### <a name="to-try-the-example-that-creates-a-reusable-control"></a>Pokusit příklad, který vytvoří opakovaně použitelné ovládací prvek  
  
1.  Vytvoření nového dialogového okna v existující aplikaci. Další informace najdete v tématu [editoru dialogového okna](../windows/dialog-editor.md) tématu.  
  
     Musíte mít aplikaci, ve kterém k vývoji opakovaně použitelné ovládací prvek. Pokud nemáte existující aplikaci používat, vytvořte aplikaci na základě dialogové okno pomocí objekty AppWizard.  
  
2.  V projektu načtena do Visual C++, použijte ClassWizard vytvořit novou třídu s názvem `CYellowEdit` na základě `CEdit`.  
  
3.  Přidejte tři členské proměnné na vaše `CYellowEdit` třídy. První dvě bude **COLORREF** proměnné, do kterých barvu textu a barvu pozadí. Třetí bude `CBrush` objekt, který bude obsahovat štětce pro vykreslování pozadí. `CBrush` Objekt vám umožní vytvořit štětce jednou, jenom odkazování poté a zrušení stopy automaticky při `CYellowEdit` řízení zničena.  
  
4.  Inicializace členské proměnné napsáním konstruktoru následujícím způsobem:  
  
 ```  
    CYellowEdit::CYellowEdit() 
 {  
    m_clrText = RGB(0,
    0,
    0);

    m_clrBkgnd = RGB(255,
    255,
    0);

    m_brBkgnd.CreateSolidBrush(m_clrBkgnd);

 }  
 ```  
  
5.  Pomocí ClassWizard, přidejte obslužnou rutinu pro reflektované `WM_CTLCOLOR` zprávy do vaší `CYellowEdit` třídy. Všimněte si, že rovná před název zprávy seznam zpráv, které lze zpracovat označuje tato zpráva se odrazí. To je popsáno v [definování obslužné rutiny zpráv pro zprávu projeví](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md).  
  
     ClassWizard přidá následující funkce makro a kostru mapy zpráv pro vás:  
  
 ```  
    ON_WM_CTLCOLOR_REFLECT() 
 *// Note: other code will be in between....  
 
    HBRUSH CYellowEdit::CtlColor(CDC* pDC, UINT nCtlColor)   
 { *// TODO: Change any attributes of the DC here  
 *// TODO: Return a non-NULL brush if the *//   parent's handler should not be called  
    return NULL;  
 }  
 ```  
  
6.  Nahraďte tělo funkce následujícím kódem. Kód určuje barvu textu, barvu pozadí textu a barvu pozadí pro zbytek ovládacího prvku.  
  
 ```  
    pDC->SetTextColor(m_clrText);
*// text  
    pDC->SetBkColor(m_clrBkgnd);
*// text bkgnd  
    return m_brBkgnd;            // ctl bkgnd  
 ```  
  
7.  Vytvoření ovládacího prvku úprav ve vašem dialogovém a připojte jej k členské proměnné poklepáním na ovládací prvek upravit stisknutým klíč ovládacího prvku. V dialogovém okně Přidat členské proměnné dokončit název proměnné a zvolte "Řízení" pro kategorii, pak "CYellowEdit" pro typ proměnné. Nezapomeňte nastavit pořadí prvků v dialogovém okně. Navíc je nutné zahrnout soubor hlaviček, pro `CYellowEdit` řízení ve vašem dialogovém hlavičkový soubor.  
  
8.  Sestavte a spusťte aplikaci. Textové pole bude mít žlutý pozadí.  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

