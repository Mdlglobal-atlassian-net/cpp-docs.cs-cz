---
title: 'TN062: Zpráva reflexe pro ovládací prvky Windows | Dokumentace Microsoftu'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 994095042dc473fda315b6d842d9ec9355ff3671
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055395"
---
# <a name="tn062-message-reflection-for-windows-controls"></a>TN062: Reflexe zprávy pro ovládací prvky Windows

> [!NOTE]
> Následující Technická poznámka nebyla aktualizována, protože byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata mohou být nesprávné nebo zastaralé. Nejnovější informace se doporučuje vyhledat téma zájmu v dokumentaci online index.

Tato technická Poznámka popisuje reflexe zprávy, nová funkce v knihovně MFC 4.0. Také obsahuje pokyny pro vytvoření jednoduché opakovaně použitelné ovládací prvek, který používá reflexi zprávy.

Tato technická Poznámka nezabývá reflexe zprávy, protože platí pro ovládací prvky ActiveX (dříve se označovaly jako ovládací prvky OLE). Podrobnosti najdete v článku [ovládací prvky ActiveX: vytvoření podtřídy ovládacího prvku Windows](../mfc/mfc-activex-controls-subclassing-a-windows-control.md).

**Co je reflexe zprávy**

Ovládací prvky Windows často odesílání oznámení do systému windows jejich nadřazené. Například mnoho ovládacích prvků odesílání zprávy oznámení barvu ovládacího prvku (WM_CTLCOLOR – nebo jeden z jeho variant) s jejich nadřazeným umožňující nadřazené slouží k poskytování štětec pro pozadí ovládacího prvku vykreslování.

Ve Windows a v prostředí MFC dříve než ve verzi 4.0 nadřazené okno, často dialogového okna, je zodpovědná za zpracování těchto zpráv. To znamená, že kód pro zpracování zprávy musí být ve třídě nadřazené okno a aby měla být duplicitní v každé třídě, kterou je potřeba zpracovat tuto zprávu. V případě výše by musel každý dialogové okno, které chtěli ovládací prvky s vlastní pozadí zpracování oznámení ovládacího prvku barvu. Bylo by mnohem jednodušší pro opětovné použití kódu, pokud ovládací prvek třídy může být napsaná, který by zpracovat barvu pozadí.

V MFC 4.0, původní mechanismus stále funguje – nadřazená windows může zpracovávat zprávy s oznámením. Kromě toho ale 4.0 knihovna MFC usnadňuje opakované použití tím, že poskytuje funkci s názvem "zpráva reflexe", která umožňuje zpracovávat v okně nadřazené nebo podřízené okno ovládacího prvku, nebo v obou těchto zpráv s oznámením. V příkladu barva pozadí ovládacího prvku, se teď dá zapisovat třídy ovládacího prvku, který nastavuje barvu pozadí zpracováním reflektovaný WM_CTLCOLOR – zpráva – vše bez nutnosti spoléhat se na nadřazený. (Všimněte si, že od reflexe zprávy je implementovaná pomocí knihovny MFC, ve Windows, nadřazené třídu okna nesmí být odvozen od `CWnd` pro účely reflexe zprávy pro práci.)

Starší verze knihovny MFC udělala něco podobný reflexe zprávy tím, že poskytuje virtuální funkce pro několik zpráv, jako jsou zprávy pro pole se seznamem vykreslovaných vlastníkem (WM_DRAWITEM a tak dále). Nový mechanismus reflexe zpráv je zobecněný a konzistentní vzhledem k aplikacím.

Reflexe zpráv je zpětně kompatibilní s kódem napsaným pro verze knihovny MFC než 4.0.

Pokud jste zadali obslužnou rutinu pro konkrétní zprávu, nebo pro celou řadu zprávy ve třídě nadřazené okno se přepíše projeví obslužné rutiny zpráv pro tutéž zprávu zadaný Nevolejte základní třídu obslužné rutiny ve vaší vlastní obslužné rutiny. Například pokud zpracovat WM_CTLCOLOR – ve vaší třídy dialogového okna, vaše zpracování se přepíšou všechny obslužné rutiny reflektovaných zpráv.

Pokud ve své třídě nadřazené okno, zadáte obslužnou rutinu pro konkrétní wm_notify – zprávy nebo rozsahu wm_notify – zprávy, bude vaše obslužná rutina volána pouze v případě, že odesílání zprávy podřízený ovládací prvek nemá žádné obslužné rutiny reflektovaných zpráv prostřednictvím `ON_NOTIFY_REFLECT()`. Pokud používáte `ON_NOTIFY_REFLECT_EX()` v mapě zpráv, vaše obslužná rutina zpráv může nebo nemusí umožňovat nadřazené okno pro zpracování zprávy. Pokud obslužná rutina vrátí **FALSE**, zpráva bude zpracován adresou nadřazené, při volání, které vrátí **TRUE** neumožňuje nadřazené, aby to zvládnul. Všimněte si, že zrcadlené zprávy se zpracovává před zprávy oznámení.

Při odeslání wm_notify – zprávy, ovládací prvek se nabízí první příležitosti, aby to zvládnul. Pokud se pošle další zrcadlené zprávy a nadřazené okno má první příležitosti, aby to zvládnul a ovládací prvek zobrazí zrcadlené zprávy. Uděláte to tak, bude je nutné funkce obslužné rutiny a odpovídající položku v mapování zprávy třídy ovládacího prvku.

Makra map zpráv pro zrcadlené zprávy se trochu liší od pro pravidelná oznámení: má *_REFLECT* připojeným k názvu obvyklé. Například aby se zpracovala zpráva wm_notify – v nadřazeném prvku, použijte makro ON_NOTIFY v mapování zprávy nadřazeného objektu. Zpracování reflektovaných zpráv v podřízený ovládací prvek, použijte makro on_notify_reflect – v mapování zprávy podřízený ovládací prvek. V některých případech parametry jsou různé, také. Mějte na paměti, že můžete ClassWizard obvykle můžete přidat položky mapování zpráv a poskytují implementace kostru funkce se správnými parametry.

Zobrazit [TN061: ON_NOTIFY a wm_notify – zprávy](../mfc/tn061-on-notify-and-wm-notify-messages.md) informace o nové wm_notify – zprávy.

**Mapování zpráv položky a funkce prototypy obslužných rutin pro zrcadlené zprávy**

Aby se zpracovala zpráva oznámení reflektovaný ovládacího prvku, použijte makra map zpráv a prototypy funkcí, které jsou uvedené v následující tabulce.

ClassWizard obvykle můžete přidat tyto položky mapy zpráv pro vás a poskytují implementace kostru funkce. Zobrazit [definování obslužné rutiny zpráv pro zprávy projeví](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md) informace o tom, jak definovat obslužné rutiny pro zrcadlené zprávy.

Pro převod z název zprávy na název reflektovaný makra, předřaďte *ON_* a připojit *_REFLECT*. WM_CTLCOLOR – například stane ON_WM_CTLCOLOR_REFLECT. (Zobrazíte zprávy, které můžete projeví proveďte opačný převod na – makro položky v tabulce níže.)

Tři výjimky z pravidla výše jsou následující:

- ON_CONTROL_REFLECT je makro wm_command – oznámení.

- On_notify_reflect – je makro pro odrazů WM_NOTIFY.

- Makra pro ON_UPDATE_COMMAND_UI odrazů je ON_UPDATE_COMMAND_UI_REFLECT.

V každé z výše uvedených zvláštní případy musíte zadat název členské funkce obslužné rutiny. V ostatních případech musíte použít standardní název funkce obslužné rutiny.

Významy parametry a návratové hodnoty funkce jsou popsány v části název funkce nebo název funkce *na* před. Například `CtlColor` je popsána v `OnCtlColor`. Několik obslužných rutin pro zrcadlené zprávy potřebovat méně parametrů než podobně jako obslužné rutiny v nadřazené okno. Právě odpovídat názvům v následující tabulce s názvy formálních parametrů v dokumentaci.

|Položka mapování|Prototyp funkce|
|---------------|------------------------|
|**ON_CONTROL_REFLECT (** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg void** `memberFxn` **();**|
|**ON_NOTIFY_REFLECT – (** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg void** `memberFxn` **(NMHDR** <strong>\*</strong> `pNotifyStruct` **, LRESULT** <strong>\*</strong> *výsledek* **);**|
|**ON_UPDATE_COMMAND_UI_REFLECT (** `memberFxn` **)**|**afx_msg void** `memberFxn` **(ccmdui –** <strong>\*</strong> `pCmdUI` **);**|
|**ON_WM_CTLCOLOR_REFLECT)**|**afx_msg HBRUSH CtlColor (CDC** <strong>\*</strong> `pDC` **, UINT** `nCtlColor` **);**|
|**ON_WM_DRAWITEM_REFLECT)**|**afx_msg void DrawItem (LPDRAWITEMSTRUCT** `lpDrawItemStruct` **);**|
|**ON_WM_MEASUREITEM_REFLECT)**|**measureitem – void afx_msg (LPMEASUREITEMSTRUCT** `lpMeasureItemStruct` **);**|
|**ON_WM_DELETEITEM_REFLECT)**|**afx_msg void DeleteItem (LPDELETEITEMSTRUCT** `lpDeleteItemStruct` **);**|
|**ON_WM_COMPAREITEM_REFLECT)**|**afx_msg int CompareItem (LPCOMPAREITEMSTRUCT** `lpCompareItemStruct` **);**|
|**ON_WM_CHARTOITEM_REFLECT)**|**afx_msg int CharToItem (UINT** `nKey` **, UINT** `nIndex` **);**|
|**ON_WM_VKEYTOITEM_REFLECT)**|**afx_msg int VKeyToItem (UINT** `nKey` **, UINT** `nIndex` **);**|
|**ON_WM_HSCROLL_REFLECT)**|**afx_msg void HScroll (UINT** `nSBCode` **, UINT** `nPos` **);**|
|**ON_WM_VSCROLL_REFLECT)**|**afx_msg void VScroll (UINT** `nSBCode` **, UINT** `nPos` **);**|
|**ON_WM_PARENTNOTIFY_REFLECT)**|**afx_msg void ParentNotify (UINT** `message` **, LPARAM** `lParam` **);**|

On_notify_reflect – a ON_CONTROL_REFLECT makra mají varianty, které umožňují více než jeden objekt (například ovládací prvek a jeho nadřazený objekt) pro zpracování danou zprávu.

|Položka mapování|Prototyp funkce|
|---------------|------------------------|
|**ON_NOTIFY_REFLECT_EX – (** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg BOOL** `memberFxn` **(NMHDR** <strong>\*</strong> `pNotifyStruct` **, LRESULT** <strong>\*</strong> *výsledek* **);**|
|**ON_CONTROL_REFLECT_EX (** `wNotifyCode` **,** `memberFxn` **)**|**afx_msg BOOL** `memberFxn` **();**|

## <a name="handling-reflected-messages-an-example-of-a-reusable-control"></a>Zpracování zpráv Reflected: Příklad opakovaně použitelné ovládací prvek

Tento jednoduchý příklad vytvoří ovládací prvek opakovaně volat `CYellowEdit`. Ovládací prvek funguje stejně jako regulární textové pole s výjimkou toho, aby zobrazil černý text na žlutým pozadím. To by bylo možné snadno přidat členské funkce, která by umožnila `CYellowEdit` ovládací prvek pro zobrazení různé barvy.

### <a name="to-try-the-example-that-creates-a-reusable-control"></a>Zkuste v příkladu, který vytvoří opakovaně použitelné ovládací prvek

1. Vytvoření nového dialogového okna v existující aplikaci. Další informace najdete v tématu [editoru dialogového okna](../windows/dialog-editor.md) tématu.

   Musí mít aplikace 00Z vyvíjet opakovaně použitelné ovládací prvek. Pokud nemáte stávající aplikace pro použití, vytvořte aplikace založené na dialogu pomocí AppWizard.

2. S projektem načtena do jazyka Visual C++, použijte ClassWizard vytvořte novou třídu s názvem `CYellowEdit` na základě `CEdit`.

3. Přidejte tři členské proměnné vaše `CYellowEdit` třídy. První dva budou *COLORREF* proměnné pro uložení barvou textu a barvou pozadí. Třetí bude `CBrush` objekt, který bude obsahovat štětec pro vykreslování na pozadí. `CBrush` Objektu umožňuje vytvořit štětec jednou, pouze na poté a zničit štětec automaticky při `CYellowEdit` ovládací prvek zničen.

4. Inicializace proměnné členů zápisem konstruktoru následujícím způsobem:

    ```cpp
    CYellowEdit::CYellowEdit()
    {
        m_clrText = RGB(0, 0, 0);
        m_clrBkgnd = RGB(255, 255, 0);
        m_brBkgnd.CreateSolidBrush(m_clrBkgnd);
    }
    ```

5. Pomocí ClassWizard, přidejte obslužnou rutinu pro reflektovaný WM_CTLCOLOR – zpráva k vaší `CYellowEdit` třídy. Všimněte si, že znaménka rovnosti před název zprávy v seznam zpráv, který dokáže zpracovat označuje, že zprávy se projeví. To je popsáno v [definování obslužné rutiny zpráv pro zprávy projeví](../mfc/reference/defining-a-message-handler-for-a-reflected-message.md).

   ClassWizard přidá následující funkce – makro a skeleton mapování zpráv za vás:

    ```cpp
    ON_WM_CTLCOLOR_REFLECT()
    // Note: other code will be in between....

    HBRUSH CYellowEdit::CtlColor(CDC* pDC, UINT nCtlColor)
    {
        // TODO: Change any attributes of the DC here
        // TODO: Return a non-NULL brush if the
        //       parent's handler should not be called
        return NULL;
    }
    ```

6. Tělo funkce nahraďte následujícím kódem. Kód určuje barvu textu, barvu pozadí textu a barvou pozadí pro zbývající část ovládacího prvku.

    ```cpp
    pDC->SetTextColor(m_clrText);   // text
    pDC->SetBkColor(m_clrBkgnd);    // text bkgnd
    return m_brBkgnd;               // ctl bkgnd
    ```

7. Vytvoření ovládacího prvku pro úpravy ve vašem dialogovém okně a připojte jej k členské proměnné když podržíte klávesu control dvojitým kliknutím na ovládací prvek pro úpravy. V dialogovém okně Přidat členskou proměnnou dokončit název proměnné a zvolte možnost "Control" kategorie, pak "CYellowEdit" pro typ proměnné. Nezapomeňte nastavit pořadí prvků v dialogovém okně. Také je potřeba zahrnout soubor hlaviček pro `CYellowEdit` řízení ve vašem dialogovém hlavičkový soubor.

8. Sestavte a spusťte aplikaci. Ovládací prvek pro úpravy budou mít žlutým pozadím.

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
