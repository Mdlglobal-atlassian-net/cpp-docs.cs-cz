---
title: 'TN061: ON_NOTIFY a wm_notify – zprávy | Microsoft Docs'
ms.custom: ''
ms.date: 06/28/2018
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- ON_NOTIFY
- WM_NOTIFY
dev_langs:
- C++
helpviewer_keywords:
- ON_NOTIFY_EX message [MFC]
- TN061
- ON_NOTIFY message [MFC]
- ON_NOTIFY_EX_RANGE message [MFC]
- ON_NOTIFY_RANGE message [MFC]
- notification messages
- WM_NOTIFY message
ms.assetid: 04a96dde-7049-41df-9954-ad7bb5587caf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 74b5a6a8d072a0cea9c92b9766fbe3ffa7c84c4f
ms.sourcegitcommit: 208d445fd7ea202de1d372d3f468e784e77bd666
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37122507"
---
# <a name="tn061-onnotify-and-wmnotify-messages"></a>TN061: ON_NOTIFY a WM_NOTIFY – zprávy

> [!NOTE]
> Následující Technická poznámka nebyla aktualizována vzhledem k tomu, že byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata může být zastaralý nebo není správný. Nejnovější informace se doporučuje, vyhledejte téma týkající se v indexu online dokumentaci.

Tato technická poznámka obsahuje základní informace o nové wm_notify – zpráva a popisuje doporučené (a nejběžnější) způsob zpracování wm_notify – zprávy ve vaší aplikaci MFC.

**Zpráv s oznámením v systému Windows 3.x**

V systému Windows 3.x, ovládací prvky oznámit svých nadřazených složek událostí, jako je například kliknutí myší, změn v obsahu a výběr a vykreslování pozadí ovládacího prvku odesláním zprávy do nadřazené. Jednoduché oznámení se odesílají jako speciální wm_command – zprávy s kódem oznámení (například BN_CLICKED) a ID balí do ovládacího prvku *wParam* a popisovač tohoto ovládacího prvku v *lParam*. Všimněte si, že od *wParam* a *lParam* úplné, neexistuje žádný způsob, jak předat žádná další data jsou – tyto zprávy mohou být pouze jednoduché oznámení. Například v BN_CLICKED oznámení, neexistuje žádný způsob, jak odeslat informace o umístění ukazatele myši při označeného kliknutím na tlačítko.

Je-li ovládací prvky v systému Windows 3.x muset odeslat zprávu oznámení, která zahrnuje další data, využívají různé speciální zprávy, včetně WM_CTLCOLOR –, WM_VSCROLL, WM_HSCROLL, WM_DRAWITEM, WM_MEASUREITEM, WM_COMPAREITEM, WM_DELETEITEM, WM_ CHARTOITEM, WM_VKEYTOITEM a tak dále. Tyto zprávy můžete zobrazí zpět na ovládací prvek, který jim poslali. Další informace najdete v tématu [TN062: reflexe zprávy pro Windows prvky](../mfc/tn062-message-reflection-for-windows-controls.md).

**Zpráv s oznámením v Win32**

Pro ovládací prvky, které existovaly v systému Windows 3.1, používá rozhraní API Win32 většinu zprávy oznámení, které byly používány v systému Windows 3.x. Ale Win32 také přidá číslo sofistikované, komplexní ovládacích prvků těm, které jsou podporovány v systému Windows 3.x. Tyto ovládací prvky se často, nutné odeslat další data s jejich zpráv s oznámením. Místo přidávání nové **WM_\***  zprávy pro každé nové oznámení, že potřebuje další data, návrháři rozhraní Win32 API se rozhodnete přidat jenom jednu zprávu, wm_notify –, které můžete předat libovolného počtu dalších dat v standardizovaným způsobem.

Wm_notify – zprávy obsahovat ID ovládacího prvku odesílání zprávy v *wParam* a ukazatel na strukturu v *lParam*. Tato struktura je buď **NMHDR** struktura nebo některé větší struktury, která má **NMHDR** struktura jako první člena. Všimněte si, že od **NMHDR** člen je první, ukazatel na tato struktura slouží jako ukazatel na **NMHDR** nebo jako ukazatel na strukturu větší v závislosti na tom, jak převést.

Ve většině případů ukazatele bude odkazovat na větší struktury a budete muset vysílat, pokud ji používáte. V pouze několik oznámení, jako je například běžné oznámení (jejichž název začíná **NM_**) a nástroj tip TTN_SHOW a TTN_POP oznámení ovládacího prvku, je **NMHDR** struktura ve skutečnosti používaná.

**NMHDR** struktura nebo počátečního člena obsahuje popisovač a ID ovládacího prvku odesílání zprávy a kód oznámení (například TTN_SHOW). Formát **NMHDR** struktura je zobrazena níže:

```cpp
typedef struct tagNMHDR {
    HWND hwndFrom;
    UINT idFrom;
    UINT code;
} NMHDR;
```

Pro zprávu TTN_SHOW **kód** člen by byl nastaven na TTN_SHOW.

Většina oznámení předat větší struktury, která obsahuje ukazatel **NMHDR** struktura jako první člena. Zvažte strukturu používané ovládacího prvku zobrazení seznamu LVN_KEYDOWN oznámení zprávy, která je odeslána při stisknutí klávesy v ovládacím prvku zobrazení seznamu. Ukazatele odkazuje na **LV_KEYDOWN** struktura, která je definována, jak je uvedeno níže:

```cpp
typedef struct tagLV_KEYDOWN {
    NMHDR hdr;
    WORD wVKey;
    UINT flags;
} LV_KEYDOWN;
```

Všimněte si, že od **NMHDR** člen je první v této struktuře, ukazatel jste předaný oznámení lze převést na ukazatel na **NMHDR** nebo odkazy **LV_KEYDOWN** .

**Oznámení společná pro všechny nové ovládací prvky Windows**

Některá oznámení jsou společné pro všechny nové ovládací prvky Windows. Tato oznámení můžete předat ukazatel **NMHDR** struktury.

|Kód oznámení|Odeslat, protože|
|-----------------------|------------------|
|NM_CLICK –|Uživatel klikl na levé tlačítko myši v ovládacím prvku|
|NM_DBLCLK –|Uživatel neotevřou levým tlačítkem myši v ovládacím prvku|
|NM_RCLICK –|Uživatel klikli pravým tlačítkem myši v ovládacím prvku|
|NM_RDBLCLK –|Uživatel dvakrát kliknete pravým tlačítkem myši v ovládacím prvku|
|NM_RETURN –|Uživatel stisknutí klávesy ENTER při řízení má vstupu fokusu|
|NM_SETFOCUS –|Nebyla zadána řízení vstupního fokusu|
|NM_KILLFOCUS –|Řízení vstupního fokusu ztratil|
|NM_OUTOFMEMORY –|Ovládací prvek nelze dokončit operaci, protože nebyl k dispozici dostatek paměti k dispozici|

##  <a name="_mfcnotes_on_notify.3a_.handling_wm_notify_messages_in_mfc_applications"></a> On_notify –: Zpracování wm_notify – zprávy v aplikacích MFC

Funkce `CWnd::OnNotify` zpracovává zprávy s oznámením. Jeho výchozí implementace kontroluje mapy zpráv pro oznámení obslužné rutiny pro volání. Obecně platí, můžete přepsat `OnNotify`. Místo toho zadejte funkci obslužné rutiny a přidejte položku mapy zpráv pro tuto obslužnou rutinu do mapy zpráv nadřazené okno třídy.

ClassWizard prostřednictvím seznamu vlastností ClassWizard, můžete vytvořit položku mapování zpráv ON_NOTIFY a poskytují funkce kostru obslužné rutiny. Další informace týkající se použití ClassWizard pro tuto činnost usnadnit najdete v tématu [mapování zpráv do funkcí](../mfc/reference/mapping-messages-to-functions.md).

On_notify – makro map zpráv má následující syntaxi:

```cpp
ON_NOTIFY(wNotifyCode, id, memberFxn)
```

kde parametry jsou:

*wNotifyCode*  
 Kód pro oznámení zpracovávat, jako je například LVN_KEYDOWN.

*id*  
 Identifikátor podřízený ovládací prvek, pro které je odesláno oznámení.

*memberFxn*  
 Členská funkce, která se má volat, když toto oznámení se odesílá.

Členská funkce musí být deklarována s následující prototyp:

```cpp
afx_msg void memberFxn(NMHDR* pNotifyStruct, LRESULT* result);
```

kde parametry jsou:

*pNotifyStruct*  
 Ukazatel na strukturu oznámení, jak je popsáno výše v části.

*Výsledek*  
 Ukazatel na kód výsledku budete nastavit před vrácením.

## <a name="example"></a>Příklad

K určení, že chcete – členská funkce `OnKeydownList1` pro zpracování zprávy LVN_KEYDOWN z `CListCtrl` jehož ID je `IDC_LIST1`, ClassWizard byste použili k mapy zpráv přidat následující:

```cpp
ON_NOTIFY(LVN_KEYDOWN, IDC_LIST1, OnKeydownList1)
```

V předchozím příkladu je funkce poskytované ClassWizard:

```cpp
void CMessageReflectionDlg::OnKeydownList1(NMHDR* pNMHDR, LRESULT* pResult)
{
    LV_KEYDOWN* pLVKeyDow = (LV_KEYDOWN*)pNMHDR;
    
    // TODO: Add your control notification handler
    //       code here

    *pResult = 0;
}
```

Všimněte si, že ClassWizard poskytuje ukazatel správného automaticky. Struktura oznámení můžete přistupovat prostřednictvím buď *pNMHDR* nebo *pLVKeyDow*.

##  <a name="_mfcnotes_on_notify_range"></a> ON_NOTIFY_RANGE –

Pokud potřebujete ke zpracování stejné wm_notify – zprávy pro sadu ovládacích prvků, můžete použít on_notify_range – místo ON_NOTIFY. Například můžete mít sadu tlačítek, pro které chcete provádět stejné akce pro určité oznámení.

Při použití on_notify_range – zadáte souvislý rozsah podřízené identifikátory, pro které chcete zpracovat oznámení zadáním počáteční a koncová podřízené identifikátory rozsahu.

ClassWizard nezpracovává on_notify_range –; Pokud chcete použít, budete muset upravit mapu zpráva sami sebe.

Položka mapování zpráv a funkce prototypu pro on_notify_range – jsou následující:

```cpp
ON_NOTIFY_RANGE(wNotifyCode, id, idLast, memberFxn)
```

kde parametry jsou:

*wNotifyCode*  
 Kód pro oznámení zpracovávat, jako je například LVN_KEYDOWN.

*id*  
 První identifikátor v souvislý rozsah identifikátory.

*idLast*  
 Poslední identifikátor v souvislý rozsah identifikátory.

*memberFxn*  
 Členská funkce, která se má volat, když toto oznámení se odesílá.

Členská funkce musí být deklarována s následující prototyp:

```cpp
afx_msg void memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

kde parametry jsou:

*id*  
 Identifikátor podřízený ovládací prvek, který odesílá oznámení.

*pNotifyStruct*  
 Ukazatel na strukturu oznámení, jak je popsáno výše.

*Výsledek*  
 Ukazatel na kód výsledku budete nastavit před vrácením.

##  <a name="_mfcnotes_tn061_on_notify_ex.2c_.on_notify_ex_range"></a> ON_NOTIFY_EX –, ON_NOTIFY_EX_RANGE –

Pokud chcete více než jeden objekt v oznámení směrování pro zpracování zprávy, můžete použít on_notify_ex – (nebo on_notify_ex_range –) namísto ON_NOTIFY (nebo on_notify_range –). Jediným rozdílem mezi **EX** regulární a verze je, že – členská funkce volat pro **EX** vrátí verze **BOOL** určující, zda zpracování zpráv by měly pokračovat. Vrácení **FALSE** z tato funkce umožňuje zpracovávat stejnou zprávu ve více než jeden objekt.

ClassWizard nezpracovává on_notify_ex – nebo on_notify_ex_range –; Pokud chcete použít některou z nich, budete muset upravit mapu zpráva sami sebe.

Položka mapování zpráv a funkce prototypu pro on_notify_ex – a on_notify_ex_range – jsou následujícím způsobem. Významy parametry jsou stejné jako jinou hodnotu než**EX** verze.

```cpp
ON_NOTIFY_EX(nCode, id, memberFxn)
ON_NOTIFY_EX_RANGE(wNotifyCode, id, idLast, memberFxn)
```

Prototyp pro obě výše je stejný:

```cpp
afx_msg BOOL memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

V obou případech *id* obsahuje identifikátor podřízený ovládací prvek, který odesílá oznámení.

Funkce musí vracet **TRUE** Pokud zpráva oznámení byla úplně zpracována nebo **FALSE** Pokud další objekty směrování příkazů by měl mít možnost zpracování zprávy.

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)  
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)  
