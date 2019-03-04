---
title: Zpracování oznámení o přizpůsobení
ms.date: 11/04/2016
f1_keywords:
- TBN_CUSTHELP
- TBN_QUERYINSERT
- TBNOTIFY
- NMHDR
- TBN_TOOLBARCHANGE
- TBN_ENDDRAG
- NM_SETFOCUS
- TBN_RESET
- NM_RETURN
- NM_ENDWAIT
- NM_STARTWAIT
- TBN_BEGINDRAG
- NM_OUTOFMEMORY
- TBN_QUERYDELETE
- NM_DBLCLK
- TBN_ENDADJUST
- NM_KILLFOCUS
- NM_RCLICK
- TBN_BEGINADJUST
- NM_CLICK
helpviewer_keywords:
- TBN_ENDADJUST notification [MFC]
- TBNOTIFY notification [MFC]
- TBN_BEGINDRAG notification [MFC]
- TBN_TOOLBARCHANGE notification [MFC]
- NM_CLICK notification [MFC]
- NM_RETURN notification [MFC]
- NM_RCLICK notification [MFC]
- TBN_ENDDRAG notification [MFC]
- TBN_BEGINADJUST notification [MFC]
- NM_ENDWAIT notification [MFC]
- NM_KILLFOCUS notification [MFC]
- NM_SETFOCUS notification [MFC]
- NM_OUTOFMEMORY notification [MFC]
- TBN_QUERYINSERT notification [MFC]
- NMHDR [MFC]
- NM_STARTWAIT notification [MFC]
- CToolBarCtrl class [MFC], handling notifications
- TBN_CUSTHELP notification [MFC]
- TBN_RESET notification [MFC]
- NM_DBLCLK notification [MFC]
- TBN_QUERYDELETE notification [MFC]
- NM_RDBLCLK notification [MFC]
- TBN_GETBUTTONINFO notification [MFC]
ms.assetid: 219ea08e-7515-4b98-85cb-47120f08c0a2
ms.openlocfilehash: dc34f3eaa4b085b9d8acbaf47b21cf1825627100
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57303647"
---
# <a name="handling-customization-notifications"></a>Zpracování oznámení o přizpůsobení

Windows nástrojů běžného ovládacího prvku má integrované funkce, včetně dialogového okna vlastního nastavení definovaná systémem, který umožní uživateli vkládat, odstranit nebo přeuspořádat tlačítka na panelu nástrojů. Aplikace určuje, zda funkce jsou k dispozici a ovládací prvky v rozsahu, do kterého může uživatel přizpůsobit panel nástrojů.

Můžete provádět tyto možnosti přizpůsobení dostupné uživatele tím, že panelu nástrojů **CCS_ADJUSTABLE** style. Funkce umožní uživateli přetáhněte tlačítko na jiné místo nebo odebrat tlačítka podle jeho přetažením z panelu nástrojů. Kromě toho uživatel můžete dvakrát kliknout na panelu nástrojů zobrazte zobrazení **upravit panel nástrojů** dialogové okno, které umožňuje uživateli přidat, odstranit a změna uspořádání tlačítek panelu nástrojů. Aplikace může zobrazit dialogové okno s použitím [vlastní](../mfc/reference/ctoolbarctrl-class.md#customize) členskou funkci.

Ovládací prvek panelu nástrojů odesílá zprávy s oznámením do nadřazeného okna v každém kroku v procesu vlastního nastavení. Pokud uživatel obsahuje klávesu SHIFT a zahájí přetahování tlačítko panelu nástrojů automaticky zpracovává operaci přetažení. Odešle panelu nástrojů **tbn_querydelete –** oznámení do nadřazeného okna k určení, jestli se dá tlačítko Odstranit. Operace přetažení končí, když nadřazené okno vrátí **FALSE**. V opačném případě panel nástrojů zaznamenává vstup z myši a čeká na uživatele k uvolnění tlačítka myši.

Když uživatel uvolní tlačítko myši, určuje ovládací prvek panelu nástrojů umístění kurzoru myši. Pokud je kurzor mimo panelu nástrojů, na tlačítko se odstraní. Pokud je kurzor na další tlačítka panelu nástrojů, odešle panelu nástrojů **tbn_queryinsert –** oznámení do nadřazeného okna k určení, pokud se dá tlačítko Vložit vlevo od daného tlačítko. Tlačítko je vložen, pokud vrací nadřazené okno **TRUE**; v opačném případě není. Odešle panelu nástrojů **tbn_toolbarchange –** zprávy oznámení, který signalizuje konec operace přetažení.

Pokud uživatel začne operace přetažení bez podržení klávesy SHIFT, odešle ovládací prvek panelu nástrojů **tbn_begindrag –** oznámení zprávu nadřazenému oknu. Aplikace, která implementuje vlastní kód přetažením tlačítko můžete tuto zprávu jako signál spustit operaci přetažení. Odešle panelu nástrojů **tbn_enddrag –** zprávy oznámení, který signalizuje konec operace přetažení.

Ovládacího prvku toolbar odesílá zprávy oznámení, když uživatel přizpůsobuje panel nástrojů s použitím **upravit panel nástrojů** dialogové okno. Odešle panelu nástrojů **tbn_beginadjust –** upozornění, jakmile uživatel dvakrát klikne panelu nástrojů, ale před dialogového okna se pole vytvoří. V dalším kroku panelu začne odesílání řadu **tbn_queryinsert –** zpráv s oznámením k určení, zda panelu nástrojů umožňuje tlačítka, která se má vložit. Při vrácení nadřazené okno **TRUE**, panelu nástrojů zastaví odesílání **tbn_queryinsert –** zpráv s oznámením. Pokud nadřazené okno nezobrazí **TRUE** pro jakékoli tlačítko panelu nástrojů zničí dialogových oken.

V dalším kroku ovládacím prvkem panel nástrojů určuje Pokud tlačítka budou odstraněny z panelu nástrojů odesláním jeden **tbn_querydelete –** oznámení pro každé tlačítko na panelu nástrojů. Vrací nadřazené okno **TRUE** označíte, že tlačítko mohou být odstraněné; v opačném případě vrátí **FALSE**. Panelu nástrojů přidá všechny tlačítka na panelu nástrojů do dialogového okna, ale ty, které se možná neodstranily šedě.

Vždy, když je ovládací prvek panelu nástrojů o tlačítko v dialogovém okně Upravit panel nástrojů, odešle **tbn_getbuttoninfo –** zpráva s oznámením, určení indexu tlačítko, pro kterou potřebuje informace a Adresa **tbnotify –** struktury. Nadřazené okno musí vyplní strukturu pomocí příslušné informace.

**Upravit panel nástrojů** dialogové okno obsahuje tlačítko Nápověda a tlačítko pro obnovení. Když uživatel klikne na tlačítko Nápověda, odešle ovládací prvek panelu nástrojů **tbn_custhelp –** zprávy oznámení. Nadřazené okno by měl odpovědět zobrazením informace nápovědy. Dialogové okno odešle **tbn_reset –** zprávy oznámení, když uživatel vybere tlačítko Obnovit. Tato zpráva signalizuje, že panelu nástrojů se chystá znovu inicializovat dialogové okno.

Tyto zprávy jsou všechny **WM_NOTIFY** zprávy a mohou být zpracovány v nadřazenému oknu tak, že přidáte do mapy zprávu nadřazenému oknu položky mapování zpráv v následujícím formátu:

```cpp
ON_NOTIFY( wNotifyCode, idControl, memberFxn )
```

- **wNotifyCode**

   Identifikátor kód, zprávy oznámení, jako **tbn_beginadjust –**.

- **idControl**

   Identifikátor ovládacího prvku odesílání oznámení.

- **memberFxn**

   Členská funkce, která se má volat po přijetí tohoto oznámení.

Členská funkce by být deklarována pomocí následující prototyp:

```cpp
afx_msg void memberFxn( NMHDR * pNotifyStruct, LRESULT * result );
```

Pokud obslužná rutina zprávy oznámení vrací hodnotu, ho měli umístit do **LRESULT** odkazované *výsledek*.

Pro každou zprávu `pNotifyStruct` odkazuje na buď **NMHDR** struktury nebo **tbnotify –** struktury. Tyto struktury jsou popsané níže:

**NMHDR** struktura obsahuje následující členy:

```cpp
typedef struct tagNMHDR {
    HWND hwndFrom;  // handle of control sending message
    UINT idFrom;// identifier of control sending message
    UINT code;  // notification code; see below
} NMHDR;
```

- **hwndFrom**

   Popisovač okna ovládacího prvku, který odesílá oznámení. Pro tento popisovač pro převod `CWnd` ukazatel, použít [CWnd::FromHandle](../mfc/reference/cwnd-class.md#fromhandle).

- **idFrom**

   Identifikátor ovládacího prvku odesílání oznámení.

- **code**

   Kód upozornění. Tento člen může být hodnota specifické pro typ ovládacího prvku, jako například **tbn_beginadjust –** nebo **TTN_NEEDTEXT**, nebo může být jedna z běžných notification hodnot uvedených níže:

   - **NM_CLICK** uživatel klikl levým tlačítkem myši v ovládacím prvku.

   - **Nm_dblclk –** že uživatel poklikal levým tlačítkem myši v ovládacím prvku.

   - **Nm_killfocus –** ovládací prvek ztratil vstupní fokus.

   - **Nm_outofmemory –** ovládací prvek nemohl dokončit operace, protože není k dispozici dostatek paměti.

   - **Nm_rclick –** uživatel klikl pravým tlačítkem myši v ovládacím prvku.

   - **Nm_rdblclk –** že uživatel poklikal pravým tlačítkem myši v ovládacím prvku.

   - **Nm_return –** ovládací prvek má vstupní fokus a uživatel stiskne klávesu ENTER.

   - **Nm_setfocus –** ovládací prvek přijal zaměření pro vstup.

**Tbnotify –** struktura obsahuje následující členy:

```cpp
typedef struct {
    NMHDR hdr; // information common to all WM_NOTIFY messages
    int iItem; // index of button associated with notification
    TBBUTTON tbButton; // info about button associated withnotification
    int cchText;   // count of characters in button text
    LPSTR lpszText;// address of button text
} TBNOTIFY, FAR* LPTBNOTIFY;
```

- **hdr**

   Informace, které jsou společné pro všechny **WM_NOTIFY** zprávy.

- **Položky**

   Index tlačítko přidružené k oznámení.

- **tbButton**

   **TBBUTTON** strukturu, která obsahuje informace o panelu nástrojů spojené s oznámením.

- **cchText**

   Počet znaků v textu tlačítka.

- **lpszText**

   Ukazatel na text na tlačítku.

Oznámení, která odešle panelu nástrojů jsou následující:

- **TBN_BEGINADJUST**

   Odesílá se, když uživatel začne přizpůsobení ovládacího prvku toolbar. Ukazatel odkazuje na **NMHDR** strukturu, která obsahuje informace o oznámení. Obslužná rutina nemusí vracet žádné konkrétní hodnotu.

- **TBN_BEGINDRAG**

   Odesílá se, když uživatel zahájí přetahování tlačítka v ovládacím prvku panel nástrojů. Ukazatel odkazuje **tbnotify –** struktury. **Položky** člena obsahuje index založený na nule tlačítko právě přetáhli. Obslužná rutina nemusí vracet žádné konkrétní hodnotu.

- **TBN_CUSTHELP**

   Odesílá se, když uživatel klikne na tlačítko Nápověda v dialogovém okně Upravit panel nástrojů. Žádnou návratovou hodnotu. Ukazatel odkazuje na **NMHDR** strukturu, která obsahuje informace o oznámení. Obslužná rutina nemusí vracet žádné konkrétní hodnotu.

- **TBN_ENDADJUST**

   Odesílá se, když uživatel zastaví přizpůsobení ovládacího prvku toolbar. Ukazatel odkazuje na **NMHDR** strukturu, která obsahuje informace o oznámení. Obslužná rutina nemusí vracet žádné konkrétní hodnotu.

- **TBN_ENDDRAG –**

   Odesílá se, když uživatel přestane přetahovat tlačítka v ovládacím prvku panel nástrojů. Ukazatel odkazuje **tbnotify –** struktury. **Položky** člena obsahuje index založený na nule tlačítko právě přetáhli. Obslužná rutina nemusí vracet žádné konkrétní hodnotu.

- **TBN_GETBUTTONINFO**

   Odesílá se, když uživatel přizpůsobuje ovládacím prvku panel nástrojů. Panelu nástrojů používá k načtení informací potřebných v dialogovém okně Upravit panel nástrojů. Tato oznámení. Ukazatel odkazuje **tbnotify –** struktury. **Položky** člen Určuje index založený na nule tlačítko. **PszText** a **cchText** členy zadejte adresu a délka ve znacích, aktuální text tlačítka. Aplikace by měla zaplnit struktura s informacemi o tlačítka. Vrátí **TRUE** Pokud informace o tlačítku byl zkopírován do struktury, nebo **FALSE** jinak.

- **TBN_QUERYDELETE**

   Odešle, když uživatel přizpůsobuje panel nástrojů k určení, zda tlačítko mohou být odstraněny z ovládacího prvku toolbar. Ukazatel odkazuje **tbnotify –** struktury. **Položky** člena obsahuje index založený na nule tlačítko Odstranit. Vrátí **TRUE** povolit tlačítko Odstranit nebo **FALSE** zabránit na tlačítko Odstranit.

- **TBN_QUERYINSERT**

   Odešle, když uživatel přizpůsobuje ovládacím prvku panel nástrojů k určení, zda se dá tlačítko Vložit vlevo od daného tlačítko. Ukazatel odkazuje **tbnotify –** struktury. **Položky** člena obsahuje index založený na nule tlačítko Vložit. Vrátí **TRUE** povolit tlačítko má být vložen před dané tlačítko nebo **FALSE** zabránit vloženého na tlačítko.

- **TBN_RESET**

   Odesílá se, když uživatel obnoví obsah dialogového okna Upravit panel nástrojů. Ukazatel odkazuje na **NMHDR** strukturu, která obsahuje informace o oznámení. Obslužná rutina nemusí vracet žádné konkrétní hodnotu.

- **TBN_TOOLBARCHANGE**

   Odesílá poté, co uživatel přizpůsobil ovládacím prvku panel nástrojů. Ukazatel odkazuje na **NMHDR** strukturu, která obsahuje informace o oznámení. Obslužná rutina nemusí vracet žádné konkrétní hodnotu.

## <a name="see-also"></a>Viz také:

[Používání atributu CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
