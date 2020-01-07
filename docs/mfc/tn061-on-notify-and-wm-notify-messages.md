---
title: 'TN061: ON_NOTIFY a WM_NOTIFY – zprávy'
ms.date: 06/28/2018
helpviewer_keywords:
- ON_NOTIFY_EX message [MFC]
- TN061
- ON_NOTIFY message [MFC]
- ON_NOTIFY_EX_RANGE message [MFC]
- ON_NOTIFY_RANGE message [MFC]
- notification messages
- WM_NOTIFY message
ms.assetid: 04a96dde-7049-41df-9954-ad7bb5587caf
ms.openlocfilehash: aa1efb628ee45be3dfaee320cf64c4b2cbb91f04
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302234"
---
# <a name="tn061-on_notify-and-wm_notify-messages"></a>TN061: ON_NOTIFY a WM_NOTIFY – zprávy

> [!NOTE]
> Následující technická Poznámka nebyla od prvního zařazení do online dokumentace aktualizována. V důsledku toho mohou být některé postupy a témata neaktuální nebo nesprávné. Nejnovější informace najdete v tématu informace o tom, co je důležité v online katalogu dokumentace najít.

Tato technická Poznámka obsahuje základní informace o nové zprávě WM_NOTIFY a popisuje doporučený (a nejběžnější) způsob zpracování WM_NOTIFY zpráv v aplikaci MFC.

**Oznamovací zprávy ve Windows 3. x**

V systému Windows 3. x řídí ovládací prvky své nadřazené události, jako je kliknutí myší, změny v obsahu a výběru, a ovládání vykreslování na pozadí odesláním zprávy nadřazenému objektu. Jednoduchá oznámení se odesílají jako speciální WM_COMMAND zprávy s kódem oznámení (například BN_CLICKED) a ID ovládacího prvku zabaleno do *wParam* a popisovačem ovládacího prvku v *lParam*. Všimněte si, že vzhledem k tomu, že *wParam* a *lParam* jsou úplné, neexistuje způsob, jak předat žádná další data – tyto zprávy mohou být pouze jednoduché oznámení. Například v oznámení BN_CLICKED neexistuje způsob, jak odesílat informace o umístění ukazatele myši při kliknutí na tlačítko.

Když ovládací prvky ve Windows 3. x potřebují poslat zprávu s oznámením, která obsahuje další data, využije nejrůznější zprávy pro zvláštní účely, včetně WM_CTLCOLOR, WM_VSCROLL, WM_HSCROLL, WM_DRAWITEM, WM_MEASUREITEM, WM_COMPAREITEM, WM_DELETEITEM, WM_ CHARTOITEM, WM_VKEYTOITEM a tak dále. Tyto zprávy lze odrážet zpět do ovládacího prvku, který je odeslal. Další informace naleznete v tématu [TN062: reflexe zprávy pro ovládací prvky systému Windows](../mfc/tn062-message-reflection-for-windows-controls.md).

**Zprávy s oznámením v systému Win32**

Pro ovládací prvky, které existovaly ve Windows 3,1, používá Win32 API většinu oznamovacích zpráv, které se používaly ve Windows 3. x. Win32 ale také přidává řadu propracovaných a komplexních ovládacích prvků, které jsou podporované ve Windows 3. x. Tyto ovládací prvky jsou často potřeba k odeslání dalších dat s jejich oznamovacími zprávami. Místo přidání nové zprávy\***WM_** pro každé nové oznámení, které potřebuje další data, návrháři Win32 API zvolili, že se má přidat jenom jedna zpráva, WM_NOTIFY, která může pomocí standardizovaného způsobu předat jakékoli množství dalších dat.

WM_NOTIFY zprávy obsahují ID ovládacího prvku odesílajícího zprávu v *wParam* a ukazatel na strukturu v *lParam*. Tato struktura je buď strukturou **NMHDR** , nebo jinou větší strukturou, která má jako první člen strukturu **NMHDR** . Všimněte si, že vzhledem k tomu, že je nejdříve člen **NMHDR** , ukazatel na tuto strukturu lze použít jako ukazatel na **NMHDR** nebo jako ukazatel na větší strukturu v závislosti na způsobu přetypování.

Ve většině případů ukazatel odkazuje na větší strukturu a při jeho použití bude nutné ho přetypovat. Pouze v několika oznámeních, jako jsou například běžná oznámení (jejichž názvy začínají **NM_** ) a TTN_SHOW a TTN_POP oznámení ovládacího prvku popis tlačítka, je **NMHDR** struktura, která je skutečně používána.

Struktura **NMHDR** nebo počáteční člen obsahuje popisovač a ID ovládacího prvku odesílajícího zprávu a kód oznámení (například TTN_SHOW). Formát struktury **NMHDR** je zobrazený níže:

```cpp
typedef struct tagNMHDR {
    HWND hwndFrom;
    UINT idFrom;
    UINT code;
} NMHDR;
```

Pro TTN_SHOWovou zprávu by byl člen **kódu** nastaven na hodnotu TTN_SHOW.

Většina oznámení předá ukazatel na větší strukturu, která obsahuje strukturu **NMHDR** jako svůj první člen. Představte si například strukturu, kterou používá LVN_KEYDOWN zpráva s oznámením ovládacího prvku seznamu, která se pošle při stisknutí klávesy v ovládacím prvku zobrazení seznamu. Ukazatel ukazuje na strukturu **LV_KEYDOWN** , která je definována tak, jak je znázorněno níže:

```cpp
typedef struct tagLV_KEYDOWN {
    NMHDR hdr;
    WORD wVKey;
    UINT flags;
} LV_KEYDOWN;
```

Všimněte si, že vzhledem k tomu, že je člen **NMHDR** nejprve v této struktuře, ukazatel, který jste předáváte do zprávy oznámení, lze přetypovat na ukazatel na **NMHDR** nebo na ukazatel na **LV_KEYDOWN**.

**Společná oznámení pro všechny nové ovládací prvky Windows**

Některá oznámení jsou společná pro všechny nové ovládací prvky Windows. Tato oznámení předejte ukazatel na strukturu **NMHDR** .

|Kód oznámení|Odesílá se, protože|
|-----------------------|------------------|
|NM_CLICK|Uživatel klikl levým tlačítkem myši v ovládacím prvku|
|NM_DBLCLK|Uživatel poklikal na levé tlačítko myši v ovládacím prvku|
|NM_RCLICK|Uživatel klikl pravým tlačítkem myši v ovládacím prvku|
|NM_RDBLCLK|Uživatel poklikal na pravé tlačítko myši v ovládacím prvku|
|NM_RETURN|Uživatel stiskl klávesu ENTER, zatímco ovládací prvek má vstupní fokus.|
|NM_SETFOCUS|Ovládací prvek dostal fokus vstupu.|
|NM_KILLFOCUS|Ovládací prvek ztratil vstupní fokus.|
|NM_OUTOFMEMORY|Ovládací prvek nemohl dokončit operaci, protože není k dispozici dostatek paměti.|

##  <a name="_mfcnotes_on_notify.3a_.handling_wm_notify_messages_in_mfc_applications"></a>ON_NOTIFY: zpracování zpráv WM_NOTIFY v aplikacích MFC

`CWnd::OnNotify` funkce zpracovává zprávy s oznámením. Jeho výchozí implementace kontroluje mapu zprávy pro volání obslužných rutin oznámení. Obecně nepřepisujete `OnNotify`. Místo toho zadáte funkci obslužné rutiny a přidáte položku mapování zpráv pro tuto obslužnou rutinu do mapy zpráv třídy vašeho okna vlastníka.

ClassWizard prostřednictvím seznamu vlastností ClassWizard může vytvořit položku mapování zpráv ON_NOTIFY a poskytnout funkci kostry obslužné rutiny. Další informace o tom, jak to usnadňuje, najdete v tématu [mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md).

Makro ON_NOTIFY – mapování zpráv má následující syntaxi:

```cpp
ON_NOTIFY(wNotifyCode, id, memberFxn)
```

kde parametry jsou:

*wNotifyCode*<br/>
Kód pro zprávu oznámení, která má být zpracována, například LVN_KEYDOWN.

*id*<br/>
Podřízený identifikátor ovládacího prvku, pro který je odesláno oznámení.

*memberFxn*<br/>
Členská funkce, která se má volat při odeslání tohoto oznámení

Vaše členská funkce musí být deklarována s následujícím prototypem:

```cpp
afx_msg void memberFxn(NMHDR* pNotifyStruct, LRESULT* result);
```

kde parametry jsou:

*pNotifyStruct*<br/>
Ukazatel na strukturu oznámení, jak je popsáno v části výše.

*vyústit*<br/>
Ukazatel na kód výsledku, který nastavíte před vrácením.

## <a name="example"></a>Příklad

Chcete-li určit, že má členská funkce `OnKeydownList1` zpracovávat LVN_KEYDOWN zprávy z `CListCtrl`, jejichž ID `IDC_LIST1`, použijte ClassWizard k přidání následujícího kódu do mapy zpráv:

```cpp
ON_NOTIFY(LVN_KEYDOWN, IDC_LIST1, OnKeydownList1)
```

Ve výše uvedeném příkladu funkce, kterou poskytuje ClassWizard, je:

```cpp
void CMessageReflectionDlg::OnKeydownList1(NMHDR* pNMHDR, LRESULT* pResult)
{
    LV_KEYDOWN* pLVKeyDow = (LV_KEYDOWN*)pNMHDR;

    // TODO: Add your control notification handler
    //       code here

    *pResult = 0;
}
```

Všimněte si, že ClassWizard poskytuje automaticky ukazatel správného typu. Ke struktuře oznámení můžete přistupovat buď pomocí *pNMHDR* , nebo *pLVKeyDow*.

##  <a name="_mfcnotes_on_notify_range"></a>ON_NOTIFY_RANGE

Pokud potřebujete zpracovat stejnou WM_NOTIFYovou zprávu pro sadu ovládacích prvků, můžete místo ON_NOTIFY použít ON_NOTIFY_RANGE. Například můžete mít sadu tlačítek, pro které chcete provést stejnou akci pro určitou zprávu oznámení.

Při použití ON_NOTIFY_RANGE zadáte souvislý rozsah podřízených identifikátorů, pro které chcete zpracovat zprávu s oznámením zadáním počátečních a koncových podřízených identifikátorů rozsahu.

ClassWizard nezpracovává ON_NOTIFY_RANGE; Pokud ho chcete použít, je nutné upravit mapu zprávy sami.

Položka mapování zpráv a prototyp funkce pro ON_NOTIFY_RANGE jsou následující:

```cpp
ON_NOTIFY_RANGE(wNotifyCode, id, idLast, memberFxn)
```

kde parametry jsou:

*wNotifyCode*<br/>
Kód pro zprávu oznámení, která má být zpracována, například LVN_KEYDOWN.

*id*<br/>
První identifikátor v souvislém rozsahu identifikátorů.

*idLast*<br/>
Poslední identifikátor v souvislém rozsahu identifikátorů.

*memberFxn*<br/>
Členská funkce, která se má volat při odeslání tohoto oznámení

Vaše členská funkce musí být deklarována s následujícím prototypem:

```cpp
afx_msg void memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

kde parametry jsou:

*id*<br/>
Podřízený identifikátor ovládacího prvku, který odeslal oznámení

*pNotifyStruct*<br/>
Ukazatel na strukturu oznámení, jak je popsáno výše.

*vyústit*<br/>
Ukazatel na kód výsledku, který nastavíte před vrácením.

##  <a name="_mfcnotes_tn061_on_notify_ex.2c_.on_notify_ex_range"></a>ON_NOTIFY_EX ON_NOTIFY_EX_RANGE

Pokud chcete, aby směrování oznámení zpracovalo více než jeden objekt, můžete místo ON_NOTIFY (nebo ON_NOTIFY_RANGE) použít ON_NOTIFY_EX (nebo ON_NOTIFY_EX_RANGE). Jediný rozdíl mezi verzí **ex** a běžnou verzí je, že členská funkce volaná pro **ex** Version vrátí hodnotu **bool** , která označuje, zda má pokračovat zpracování zprávy. Vrácení **hodnoty false** z této funkce umožňuje zpracovat stejnou zprávu ve více než jednom objektu.

ClassWizard nezpracovává ON_NOTIFY_EX ani ON_NOTIFY_EX_RANGE; Pokud chcete použít některou z těchto z nich, je nutné upravit mapu zprávy sami.

Položka mapování zpráv a prototyp funkce pro ON_NOTIFY_EX a ON_NOTIFY_EX_RANGE jsou následující. Význam parametrů je stejný jako u jiných než**ex** Versions.

```cpp
ON_NOTIFY_EX(nCode, id, memberFxn)
ON_NOTIFY_EX_RANGE(wNotifyCode, id, idLast, memberFxn)
```

Prototyp obou z výše uvedených je stejný:

```cpp
afx_msg BOOL memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

V obou případech *ID* obsahuje podřízený identifikátor ovládacího prvku, který odeslal oznámení.

Funkce musí vracet **hodnotu true** , pokud byla zpráva oznámení zcela zpracována, nebo **false** , pokud jiné objekty ve směrování příkazu mají mít možnost zprávu zpracovat.

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
