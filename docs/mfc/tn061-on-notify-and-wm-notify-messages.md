---
title: 'TN061: ON_NOTIFY a WM_NOTIFY – zprávy'
ms.date: 06/28/2018
f1_keywords:
- ON_NOTIFY
- WM_NOTIFY
helpviewer_keywords:
- ON_NOTIFY_EX message [MFC]
- TN061
- ON_NOTIFY message [MFC]
- ON_NOTIFY_EX_RANGE message [MFC]
- ON_NOTIFY_RANGE message [MFC]
- notification messages
- WM_NOTIFY message
ms.assetid: 04a96dde-7049-41df-9954-ad7bb5587caf
ms.openlocfilehash: 74eb39a855da3ff3e6da7f14a76bf0804919826d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658845"
---
# <a name="tn061-onnotify-and-wmnotify-messages"></a>TN061: ON_NOTIFY a WM_NOTIFY – zprávy

> [!NOTE]
> Následující Technická poznámka nebyla aktualizována, protože byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata mohou být nesprávné nebo zastaralé. Nejnovější informace se doporučuje vyhledat téma zájmu v dokumentaci online index.

Tato technická poznámka obsahuje základní informace o nové wm_notify – zprávy a popisuje doporučené (a nejběžnější) způsob zpracování wm_notify – zprávy v aplikaci knihovny MFC.

**Zpráv s oznámením v Windows 3.x**

Ve Windows 3.x, ovládací prvky oznámit svých nadřazených složek událostí, jako je například kliknutí myší, změny v obsahu a výběr a barvení ovládacích prvků na pozadí odesláním zprávy na nadřazený prvek. Jednoduché oznámení se odesílají jako speciální wm_command – zprávy s kódem oznámení (například BN_CLICKED) a ID zkomprimována do ovládacího prvku *wParam* a popisovač tohoto ovládacího prvku v *lParam*. Všimněte si, že od *wParam* a *lParam* plný, neexistuje žádný způsob, jak předávat žádná další data jsou – tyto zprávy mohou být pouze jednoduché oznámení. Například v oznámení BN_CLICKED neexistuje žádný způsob, jak odesílat informace o umístění kurzoru myši, když došlo ke kliknutí na tlačítko.

Když ovládacích prvků ve Windows 3.x muset odeslat zprávu oznámení, která obsahuje další data, používají širokou škálu speciální zprávy, včetně WM_CTLCOLOR – WM_VSCROLL, WM_HSCROLL, WM_DRAWITEM, WM_MEASUREITEM, WM_COMPAREITEM, WM_DELETEITEM, WM_ CHARTOITEM WM_VKEYTOITEM a tak dále. Tyto zprávy můžete projeví zpět do ovládacího prvku, který jim poslali. Další informace najdete v tématu [TN062: reflexe zprávy pro Windows prvky](../mfc/tn062-message-reflection-for-windows-controls.md).

**Zprávy s oznámením v systému Win32**

Pro ovládací prvky, které existovaly ve Windows 3.1, rozhraní API systému Win32 používá většina zprávy oznámení, které byly použity ve Windows 3.x. Ale Win32 také přidá počet propracované, komplexní ovládací prvky, které jsou podporovány ve Windows 3.x. Tyto ovládací prvky často, třeba odeslání dalších dat s jejich zpráv s oznámením. Místo přidávání nového **WM_** <strong>\*</strong> zprávy pro každé nové oznámení, který potřebuje další data, návrhářů rozhraní Win32 API se rozhodnete přidat pouze jednu zpráva wm_notify –, který můžete projít žádnou objem dalších dat standardizované způsobem.

Wm_notify – zprávy obsahují ID ovládacího prvku odeslání zprávy *wParam* a ukazatel na strukturu v *lParam*. Tato struktura je buď **NMHDR** struktury nebo některé větší struktury, která má **NMHDR** strukturu jako jeho prvním členem. Všimněte si, že od **NMHDR** člen je první, ukazatel na tuto strukturu může sloužit jako ukazatel na **NMHDR** nebo jako ukazatel na strukturu větší v závislosti na tom, jak jej přetypovat.

Ve většině případů bude ukazatel přejděte na větší struktury a bude potřeba ji přetypujte, když ji použijete. V pouze několika oznámení, jako je například běžné oznámení (jejichž jména začínají **NM_**) a nástroj tip TTN_SHOW a TTN_POP oznámení ovládacího prvku, je **NMHDR** struktura skutečně spotřebujete.

**NMHDR** struktury nebo počátečního člena obsahuje popisovač a ID ovládacího prvku odesílání zprávy a oznámení kódu (například TTN_SHOW). Formát **NMHDR** struktury jsou uvedené níže:

```cpp
typedef struct tagNMHDR {
    HWND hwndFrom;
    UINT idFrom;
    UINT code;
} NMHDR;
```

Pro zprávu TTN_SHOW **kód** člen by byl nastaven na TTN_SHOW.

Většina oznámení předat větší struktury, který obsahuje ukazatel **NMHDR** strukturu jako jeho prvního člena. Zvažte například struktura používá zpráva s oznámením LVN_KEYDOWN ovládací prvek zobrazení seznamu, který se odešle, když se stiskne klávesa, v ovládacím prvku zobrazení seznamu. Ukazatel odkazuje na **LV_KEYDOWN** struktura, která je definována, jak je znázorněno níže:

```cpp
typedef struct tagLV_KEYDOWN {
    NMHDR hdr;
    WORD wVKey;
    UINT flags;
} LV_KEYDOWN;
```

Všimněte si, že od **NMHDR** člen je první v této struktuře, ukazatel se předaný zprávy oznámení může být převeden na ukazatel na **NMHDR** nebo ukazatel na **LV_KEYDOWN** .

**Oznámení společná pro všechny nové ovládací prvky Windows**

Některá oznámení jsou společné pro všechny nové ovládací prvky Windows. Tato oznámení můžete předat ukazatel **NMHDR** struktury.

|Kód upozornění|Odeslat, protože|
|-----------------------|------------------|
|NM_CLICK –|Uživatel klikl levým tlačítkem myši v ovládacím prvku|
|NM_DBLCLK –|Uživatel dvojitému kliknutí levým tlačítkem myši v ovládacím prvku|
|NM_RCLICK –|Uživatel klikl pravým tlačítkem myši v ovládacím prvku|
|NM_RDBLCLK –|Uživatel dvojitému kliknutí pravým tlačítkem myši v ovládacím prvku|
|NM_RETURN –|Uživatel stiskne klávesu ENTER, když ovládací prvek má vstupní fokus|
|NM_SETFOCUS –|Ovládací prvek se předala vstupní fokus.|
|NM_KILLFOCUS –|Ovládací prvek ztratil vstupní fokus.|
|NM_OUTOFMEMORY –|Ovládací prvek nemohl dokončit operaci, protože nebyl k dispozici dostatek paměti k dispozici|

##  <a name="_mfcnotes_on_notify.3a_.handling_wm_notify_messages_in_mfc_applications"></a> ON_NOTIFY: Zpracování wm_notify – zprávy v aplikacích MFC

Funkce `CWnd::OnNotify` zpracovává zprávy s oznámením. Jeho výchozí implementace kontroluje mapu zpráv pro obslužné rutiny oznamovacích volat. Obecně platí, které nesmí být přepsána `OnNotify`. Místo toho zadejte funkci obslužné rutiny a přidat položku mapy zpráv pro tuto obslužnou rutinu do mapy zprávu nadřazenému oknu třídy.

ClassWizard prostřednictvím ClassWizard seznam vlastností, můžete vytvořit položku mapování zpráv ON_NOTIFY a poskytují funkci kostru obslužné rutiny. Další informace o použití ClassWizard pro lepší pochopení, naleznete v tématu [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md).

Makra map zpráv ON_NOTIFY má následující syntaxi:

```cpp
ON_NOTIFY(wNotifyCode, id, memberFxn)
```

kde parametry jsou:

*funkci wNotifyCode*<br/>
Kód pro tuto zprávu zpracovat, jako je například LVN_KEYDOWN.

*id*<br/>
Identifikátor podřízené ovládací prvek, pro které je odesláno oznámení.

*memberFxn*<br/>
Členská funkce se volá, když toto oznámení se posílá.

Členská funkce musí být deklarován s následující prototyp:

```cpp
afx_msg void memberFxn(NMHDR* pNotifyStruct, LRESULT* result);
```

kde parametry jsou:

*pNotifyStruct*<br/>
Ukazatel na strukturu oznámení, jak je popsáno výše v části.

*výsledek*<br/>
Ukazatel na kód výsledku bude nastaven před vrácením.

## <a name="example"></a>Příklad

Chcete-li určit, který má členská funkce `OnKeydownList1` zpracovává zprávy LVN_KEYDOWN z `CListCtrl` jehož ID je `IDC_LIST1`, ClassWizard byste použili k přidejte následující mapování vaší zprávy:

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

Mějte na paměti, že ClassWizard poskytuje ukazatel vhodný typ automaticky. Struktura oznámení můžete přistupovat prostřednictvím buď *pNMHDR* nebo *pLVKeyDow*.

##  <a name="_mfcnotes_on_notify_range"></a> ON_NOTIFY_RANGE –

Pokud je potřeba zpracovat stejné wm_notify – zprávy pro sadu ovládacích prvků, můžete použít ON_NOTIFY_RANGE spíše než ON_NOTIFY. Například může mít sadu tlačítek, u kterého chcete provést stejnou akci pro určité zprávu s oznámením.

Když je ON_NOTIFY_RANGE použít, určíte souvislý rozsah podřízené identifikátory, pro které se mají zpracovávat zprávy oznámení určením počáteční a koncové podřízené identifikátory rozsahu.

ClassWizard nezpracovává ON_NOTIFY_RANGE; ho Pokud chcete použít, budete muset upravit mapu zpráv sami.

Položka mapování zpráv a prototyp funkce pro je on_notify_range – jsou následující:

```cpp
ON_NOTIFY_RANGE(wNotifyCode, id, idLast, memberFxn)
```

kde parametry jsou:

*funkci wNotifyCode*<br/>
Kód pro tuto zprávu zpracovat, jako je například LVN_KEYDOWN.

*id*<br/>
První identifikátor v souvislý rozsah identifikátory.

*idLast*<br/>
Poslední identifikátoru souvislý rozsah identifikátory.

*memberFxn*<br/>
Členská funkce se volá, když toto oznámení se posílá.

Členská funkce musí být deklarován s následující prototyp:

```cpp
afx_msg void memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

kde parametry jsou:

*id*<br/>
Identifikátor podřízeného ovládacího prvku, který poslat oznámení.

*pNotifyStruct*<br/>
Ukazatel na strukturu oznámení, jak je popsáno výše.

*výsledek*<br/>
Ukazatel na kód výsledku bude nastaven před vrácením.

##  <a name="_mfcnotes_tn061_on_notify_ex.2c_.on_notify_ex_range"></a> ON_NOTIFY_EX – ON_NOTIFY_EX_RANGE –

Pokud chcete více než jeden objekt v směrování pro zpracování zprávy oznámení, můžete použít on_notify_ex – (nebo on_notify_ex_range –) místo ON_NOTIFY (nebo ON_NOTIFY_RANGE). Jediným rozdílem mezi **EX** verzí a regulárních verzí je, že členská funkce volána pro **EX** vrátí verzi **BOOL** , která indikuje, jestli zpracování zpráv by měly pokračovat. Vrací **FALSE** z tato funkce umožňuje zpracovávat stejná zpráva ve více než jeden objekt.

ClassWizard nezpracovává on_notify_ex – nebo on_notify_ex_range –; Pokud chcete použít některou z nich, budete muset upravit mapu zpráv sami.

Položka mapování zpráv a prototyp funkce on_notify_ex – a on_notify_ex_range – jsou následující. Význam parametry jsou stejné jako u non -**EX** verze.

```cpp
ON_NOTIFY_EX(nCode, id, memberFxn)
ON_NOTIFY_EX_RANGE(wNotifyCode, id, idLast, memberFxn)
```

Prototyp pro oba z výše uvedených je stejný:

```cpp
afx_msg BOOL memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

V obou případech *id* obsahuje identifikátor podřízené ovládací prvek, který poslat oznámení.

Vaše funkce musí vracet **TRUE** Pokud zpráva oznámení byla zcela zpracována nebo **FALSE** Pokud ostatní objekty v směrování příkazů by měl mít možnost zpracování zprávy.

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
