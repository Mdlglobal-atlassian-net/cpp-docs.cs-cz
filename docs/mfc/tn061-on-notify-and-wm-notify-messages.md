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
ms.openlocfilehash: 845558dad6b9f6e820c759cb83fce2c6cbceaa0c
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366602"
---
# <a name="tn061-on_notify-and-wm_notify-messages"></a>TN061: ON_NOTIFY a WM_NOTIFY – zprávy

> [!NOTE]
> Následující technická poznámka nebyla aktualizována od doby, kdy byla poprvé zahrnuta do online dokumentace. V důsledku toho mohou být některé postupy a témata zastaralé nebo nesprávné. Chcete-li získat nejnovější informace, doporučujeme vyhledat téma zájmu v online indexu dokumentace.

Tato technická poznámka obsahuje základní informace o nové zprávě WM_NOTIFY a popisuje doporučený (a nejběžnější) způsob zpracování zpráv WM_NOTIFY v aplikaci knihovny MFC.

**Oznámení ve Windows 3.x**

V systému Windows 3.x ovládací prvky upozorňují rodiče na události, jako je kliknutí myší, změny obsahu a výběru a řízení malování na pozadí odesláním zprávy nadřazené. Jednoduchá oznámení jsou odesílána jako speciální WM_COMMAND zprávy, s kódem oznámení (například BN_CLICKED) a ID ovládacího prvku zabaleným do *wParam* a popisovač ovládacího prvku v *lParam*. Všimněte si, že vzhledem k tomu, *wParam* a *lParam* jsou plné, neexistuje žádný způsob, jak předat další data – tyto zprávy mohou být pouze jednoduché oznámení. Například v oznámení BN_CLICKED neexistuje žádný způsob, jak odeslat informace o umístění kurzoru myši při klepnutí na tlačítko.

Pokud ovládací prvky ve Windows 3.x potřebují odeslat oznámení obsahující další data, používají různé zprávy pro speciální účely, včetně WM_CTLCOLOR, WM_VSCROLL, WM_HSCROLL, WM_DRAWITEM, WM_MEASUREITEM, WM_COMPAREITEM, WM_DELETEITEM, WM_CHARTOITEM, WM_VKEYTOITEM a tak dále. Tyto zprávy mohou být odrazí zpět do ovládacího prvku, který je odeslal. Další informace naleznete v [tématu TN062: Message Reflection for Windows Controls](../mfc/tn062-message-reflection-for-windows-controls.md).

**Oznámení zprávy v Win32**

Pro ovládací prvky, které existovaly v systému Windows 3.1, rozhraní API Win32 používá většinu zpráv s oznámením, které byly použity v systému Windows 3.x. Win32 však také přidává řadu sofistikovaných, složitých ovládacích prvků k těm, které jsou podporovány v systému Windows 3.x. Tyto ovládací prvky často potřebují odesílat další data s jejich oznámení. Místo přidání nové **WM_** <strong>\*</strong> zprávy pro každé nové oznámení, které potřebuje další data, návrháři rozhraní API Win32 se rozhodli přidat pouze jednu zprávu, WM_NOTIFY, která může standardizovaným způsobem předat libovolné množství dalších dat.

WM_NOTIFY zprávy obsahují ID ovládacího prvku odesílání zprávy v *wParam* a ukazatel na strukturu v *lParam*. Tato struktura je buď **NMHDR** struktury nebo některé větší struktury, která má **NMHDR** strukturu jako jeho první člen. Všimněte si, že vzhledem k tomu, že člen **NMHDR** je první, ukazatel na tuto strukturu lze použít jako ukazatel na **NMHDR** nebo jako ukazatel na větší strukturu v závislosti na tom, jak jej přetypovat.

Ve většině případů ukazatel bude ukazovat na větší strukturu a budete muset přetypovat při jeho použití. V několika oznámeních, jako jsou běžná oznámení (jejichž názvy začínají **NM_)** a TTN_SHOW a TTN_POP oznámení ovládacího prvku špičky nástroje, je skutečně použitá struktura **NMHDR.**

**NMHDR** struktura nebo počáteční člen obsahuje popisovač a ID ovládacího prvku odesílání zprávy a kód oznámení (například TTN_SHOW). Formát struktury **NMHDR** je uveden níže:

```cpp
typedef struct tagNMHDR {
    HWND hwndFrom;
    UINT idFrom;
    UINT code;
} NMHDR;
```

Pro TTN_SHOW zprávu by člen **kódu** nastavena na TTN_SHOW.

Většina oznámení předat ukazatel na větší strukturu, která obsahuje **nMHDR** strukturu jako jeho první člen. Zvažte například strukturu používanou LVN_KEYDOWN oznámení ovládacího prvku zobrazení seznamu, která je odeslána při stisknutí klávesy v ovládacím prvku zobrazení seznamu. Ukazatel ukazuje na **LV_KEYDOWN** strukturu, která je definována tak, jak je znázorněno níže:

```cpp
typedef struct tagLV_KEYDOWN {
    NMHDR hdr;
    WORD wVKey;
    UINT flags;
} LV_KEYDOWN;
```

Všimněte si, že vzhledem k tomu, že člen **NMHDR** je první v této struktuře, ukazatel, který jsou předány ve zprávě s oznámením může být přetypován buď ukazatel na **NMHDR** nebo ukazatel na **LV_KEYDOWN**.

**Oznámení společná pro všechny nové ovládací prvky systému Windows**

Některá oznámení jsou společná pro všechny nové ovládací prvky systému Windows. Tato oznámení předat ukazatel na strukturu **NMHDR.**

|Kód oznámení|Odesláno, protože|
|-----------------------|------------------|
|NM_CLICK|Uživatel kliknul levým tlačítkem myši v ovládacím prvku|
|NM_DBLCLK|Uživatel poklepal levým tlačítkem myši v ovládacím prvku|
|NM_RCLICK|Uživatel kliknul pravým tlačítkem myši v ovládacím prvku|
|NM_RDBLCLK|Uživatel poklepal pravým tlačítkem myši v ovládacím prvku|
|NM_RETURN|Uživatel stiskl klávesu ENTER, zatímco ovládací prvek má vstupní fokus|
|NM_SETFOCUS|Ovládacímu prvku bylo přiděleno vstupní zaměření|
|NM_KILLFOCUS|Ovládací prvek ztratil zaostření vstupu|
|NM_OUTOFMEMORY|Ovládací prvek nemohl dokončit operaci, protože nebylo k dispozici dostatek paměti.|

## <a name="on_notify-handling-wm_notify-messages-in-mfc-applications"></a><a name="_mfcnotes_on_notify.3a_.handling_wm_notify_messages_in_mfc_applications"></a>ON_NOTIFY: Zpracování zpráv WM_NOTIFY v aplikacích knihovny MFC

Funkce `CWnd::OnNotify` zpracovává oznámení. Jeho výchozí implementace zkontroluje mapu zpráv pro obslužné rutiny oznámení k volání. Obecně nelze přepsat `OnNotify`. Místo toho zadáte funkci obslužné rutiny a přidáte položku mapy zpráv pro tuto obslužnou rutinu do mapy zpráv třídy okna vlastníka.

ClassWizard, prostřednictvím classwizard seznamu vlastností, můžete vytvořit ON_NOTIFY položku mapy zprávy a poskytnout funkci obslužné rutiny kostry. Další informace o použití Průvodce třídou k usnadnění tohoto tématu naleznete [v tématu Mapování zpráv na funkce](../mfc/reference/mapping-messages-to-functions.md).

Makro ON_NOTIFY mapy zpráv má následující syntaxi:

```cpp
ON_NOTIFY(wNotifyCode, id, memberFxn)
```

kde parametry jsou:

*wNotifyCode*<br/>
Kód pro oznámení zprávy, které mají být zpracovány, například LVN_KEYDOWN.

*Id*<br/>
Podřízený identifikátor ovládacího prvku, pro který je odesláno oznámení.

*členFxn*<br/>
Členská funkce, která má být volána při odeslání tohoto oznámení.

Vaše členská funkce musí být deklarována následujícím prototypem:

```cpp
afx_msg void memberFxn(NMHDR* pNotifyStruct, LRESULT* result);
```

kde parametry jsou:

*pNotifyStruct*<br/>
Ukazatel na strukturu oznámení, jak je popsáno v části výše.

*Výsledek*<br/>
Ukazatel na kód výsledku, který nastavíte před návratem.

## <a name="example"></a>Příklad

Chcete-li určit, že `OnKeydownList1` chcete, aby `CListCtrl` členská funkce `IDC_LIST1`zpracovávala LVN_KEYDOWN zprávy z jehoIPříkaz, pomocí Průvodce třídou byste do mapy zpráv přidali následující:

```cpp
ON_NOTIFY(LVN_KEYDOWN, IDC_LIST1, OnKeydownList1)
```

Ve výše uvedeném příkladu je funkce poskytovaná ClassWizard:

```cpp
void CMessageReflectionDlg::OnKeydownList1(NMHDR* pNMHDR, LRESULT* pResult)
{
    LV_KEYDOWN* pLVKeyDow = (LV_KEYDOWN*)pNMHDR;

    // TODO: Add your control notification handler
    //       code here

    *pResult = 0;
}
```

Všimněte si, že ClassWizard poskytuje ukazatel správného typu automaticky. Ke struktuře oznámení můžete přistupovat buď prostřednictvím *pNMHDR* nebo *pLVKeyDow*.

## <a name="on_notify_range"></a><a name="_mfcnotes_on_notify_range"></a>ON_NOTIFY_RANGE

Pokud potřebujete zpracovat stejnou WM_NOTIFY zprávu pro sadu ovládacích prvků, můžete použít ON_NOTIFY_RANGE, nikoli ON_NOTIFY. Můžete mít například sadu tlačítek, pro které chcete provést stejnou akci pro určitou oznámení.

Při použití ON_NOTIFY_RANGE zadáte souvislý rozsah podřízených identifikátorů, pro které se má zpracovat zpráva s oznámením, zadáním počátečních a koncových podřízených identifikátorů oblasti.

ClassWizard nezpracovává ON_NOTIFY_RANGE; chcete-li jej použít, musíte upravit mapu zpráv sami.

Prototyp položky a funkce mapy zpráv pro ON_NOTIFY_RANGE jsou následující:

```cpp
ON_NOTIFY_RANGE(wNotifyCode, id, idLast, memberFxn)
```

kde parametry jsou:

*wNotifyCode*<br/>
Kód pro oznámení zprávy, které mají být zpracovány, například LVN_KEYDOWN.

*Id*<br/>
První identifikátor v souvislém rozsahu identifikátorů.

*idPoslední*<br/>
Poslední identifikátor v souvislém rozsahu identifikátorů.

*členFxn*<br/>
Členská funkce, která má být volána při odeslání tohoto oznámení.

Vaše členská funkce musí být deklarována následujícím prototypem:

```cpp
afx_msg void memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

kde parametry jsou:

*Id*<br/>
Podřízený identifikátor ovládacího prvku, který odeslal oznámení.

*pNotifyStruct*<br/>
Ukazatel na strukturu oznámení, jak je popsáno výše.

*Výsledek*<br/>
Ukazatel na kód výsledku, který nastavíte před návratem.

## <a name="on_notify_ex-on_notify_ex_range"></a><a name="_mfcnotes_tn061_on_notify_ex.2c_.on_notify_ex_range"></a>ON_NOTIFY_EX, ON_NOTIFY_EX_RANGE

Pokud chcete, aby více než jeden objekt ve směrování oznámení ke zpracování zprávy, můžete použít ON_NOTIFY_EX (nebo ON_NOTIFY_EX_RANGE) spíše než ON_NOTIFY (nebo ON_NOTIFY_RANGE). Jediný rozdíl mezi **ex** verze a běžné verze je, že členská funkce volaná pro verzi **EX** vrátí **BOOL,** který označuje, zda by mělo pokračovat zpracování zpráv. Vrácení **NEPRAVDA** z této funkce umožňuje zpracovat stejnou zprávu ve více než jednom objektu.

ClassWizard nezpracovává ON_NOTIFY_EX nebo ON_NOTIFY_EX_RANGE; Pokud chcete použít některou z nich, musíte upravit mapu zpráv sami.

Prototyp položky a funkce mapy zpráv pro ON_NOTIFY_EX a ON_NOTIFY_EX_RANGE jsou následující. Význam parametrů je stejný jako u verzí bez**EX.**

```cpp
ON_NOTIFY_EX(nCode, id, memberFxn)
ON_NOTIFY_EX_RANGE(wNotifyCode, id, idLast, memberFxn)
```

Prototyp pro oba výše uvedené je stejný:

```cpp
afx_msg BOOL memberFxn(UINT id, NMHDR* pNotifyStruct, LRESULT* result);
```

V obou případech *id* obsahuje podřízený identifikátor ovládacího prvku, který odeslal oznámení.

Funkce musí vrátit **hodnotu TRUE,** pokud byla zpráva s oznámením zcela zpracována, nebo **NEPRAVDA,** pokud by ostatní objekty v směrování příkazů měly mít možnost zprávu zpracovat.

## <a name="see-also"></a>Viz také

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
