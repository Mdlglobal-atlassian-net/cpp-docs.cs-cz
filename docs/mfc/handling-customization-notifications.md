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
ms.openlocfilehash: 67f40d0dc50a853a39cb9b60a938d8eafe8293c4
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370485"
---
# <a name="handling-customization-notifications"></a>Zpracování oznámení o přizpůsobení

Společný ovládací prvek panelu nástrojů systému Windows obsahuje integrované funkce vlastního nastavení, včetně dialogového okna přizpůsobení definovaného systémem, které uživateli umožňuje vložit, odstranit nebo uspořádat tlačítka panelu nástrojů. Aplikace určuje, zda jsou k dispozici funkce vlastního nastavení, a určuje, do jaké míry může uživatel přizpůsobit panel nástrojů.

Tyto funkce vlastního nastavení můžete zpřístupnit uživateli tak, že panelu nástrojů poskytnete **CCS_ADJUSTABLE** stylu. Funkce vlastního nastavení umožňují uživateli přetáhnout tlačítko na novou pozici nebo odstranit tlačítko jeho přetažením z panelu nástrojů. Kromě toho může uživatel poklepat na panel nástrojů a zobrazit dialogové okno **Přizpůsobit panel nástrojů,** které uživateli umožňuje přidávat, odstraňovat a měnit uspořádání tlačítek panelu nástrojů. Aplikace může zobrazit dialogové okno pomocí funkce [Přizpůsobit](../mfc/reference/ctoolbarctrl-class.md#customize) členy.

Ovládací prvek panelu nástrojů odesílá oznámení do nadřazeného okna v každém kroku procesu vlastního nastavení. Pokud uživatel podrží klávesu SHIFT dolů a začne přetahovat tlačítko, panel nástrojů automaticky zřídí operaci přetažení. Panel nástrojů odešle **zprávu o TBN_QUERYDELETE** oznámení do nadřazeného okna, aby zjistil, zda může být tlačítko odstraněno. Operace přetažení končí, pokud nadřazené okno vrátí **hodnotu NEPRAVDA**. V opačném případě panel nástrojů zachytí vstup myši a čeká na uživatele uvolnit tlačítko myši.

Když uživatel uvolní tlačítko myši, ovládací prvek panelu nástrojů určuje umístění kurzoru myši. Pokud je kurzor mimo panel nástrojů, tlačítko se odstraní. Pokud je kurzor na jiném tlačítku panelu nástrojů, panel nástrojů odešle **zprávu TBN_QUERYINSERT** oznámení do nadřazeného okna, aby zjistil, zda může být tlačítko vloženo nalevo od daného tlačítka. Tlačítko se vloží, pokud nadřazené okno vrátí **hodnotu PRAVDA**; v opačném případě tomu tak není. Panel nástrojů odešle **TBN_TOOLBARCHANGE** oznámení, které signalizuje konec operace přetažení.

Pokud uživatel zahájí operaci přetažení bez podržení klávesy SHIFT, ovládací prvek panelu nástrojů odešle **TBN_BEGINDRAG** oznámení do okna vlastníka. Aplikace, která implementuje vlastní kód přetažení tlačítka můžete použít tuto zprávu jako signál k zahájení operace přetažení. Panel nástrojů odešle **TBN_ENDDRAG** oznámení, které signalizuje konec operace přetažení.

Ovládací prvek panelu nástrojů odesílá oznámení, když uživatel přizpůsobí panel nástrojů pomocí dialogového okna **Přizpůsobit panel nástrojů.** Panel nástrojů odešle **TBN_BEGINADJUST** oznámení poté, co uživatel poklepe na panel nástrojů, ale před vytvořením dialogového okna. Dále panel nástrojů začne odesílat řadu **zpráv TBN_QUERYINSERT** oznámení k určení, zda panel nástrojů umožňuje vkládání tlačítek. Pokud nadřazené okno vrátí **hodnotu PRAVDA**, panel nástrojů přestane odesílat **TBN_QUERYINSERT** oznámení. Pokud nadřazené okno nevrátí **hodnotu TRUE** pro žádné tlačítko, panel nástrojů dialogové okno zničí.

Ovládací prvek panelu nástrojů dále určuje, zda mohou být z panelu nástrojů odstraněna některá tlačítka odesláním jedné **TBN_QUERYDELETE** oznámení pro každé tlačítko na panelu nástrojů. Nadřazené okno vrátí **hodnotu TRUE,** která označuje, že tlačítko může být odstraněno. v opačném případě vrátí **hodnotu NEPRAVDA**. Panel nástrojů přidá do dialogového okna všechna tlačítka panelu nástrojů, ale zšedé ty, které nelze odstranit.

Vždy, když ovládací prvek panelu nástrojů potřebuje informace o tlačítku v dialogovém okně Přizpůsobit panel nástrojů, odešle **TBN_GETBUTTONINFO** oznámení s určením indexu tlačítka, pro které potřebuje informace, a adresu struktury **TBNOTIFY.** Nadřazené okno musí vyplnit strukturu s příslušnými informacemi.

Dialogové okno **Přizpůsobit panel nástrojů** obsahuje tlačítko Nápověda a tlačítko Obnovit. Když uživatel zvolí tlačítko Nápověda, ovládací prvek panelu nástrojů odešle **TBN_CUSTHELP** oznámení. Nadřazené okno by mělo reagovat zobrazením informací nápovědy. Dialogové okno odešle **TBN_RESET** oznámení, když uživatel vybere tlačítko Obnovit. Tato zpráva signalizuje, že panel nástrojů se chystá znovu inicializovat dialogové okno.

Všechny tyto zprávy jsou **WM_NOTIFY** a mohou být zpracovány v okně vlastníka přidáním položek mapy zpráv následujícího formuláře do mapy zpráv v okně vlastníka:

```cpp
ON_NOTIFY( wNotifyCode, idControl, memberFxn )
```

- **wNotifyCode**

   Identifikační kód oznamovací zprávy, například **TBN_BEGINADJUST**.

- **idControl**

   Identifikátor ovládacího prvku odesílání oznámení.

- **členFxn**

   Členská funkce, která má být volána při přijetí tohoto oznámení.

Vaše členská funkce by byla deklarována s následujícím prototypem:

```cpp
afx_msg void memberFxn( NMHDR * pNotifyStruct, LRESULT * result );
```

Pokud obslužná rutina zprávy oznámení vrátí hodnotu, měla by ji vložit do **pole LRESULT,** na kterou se vztahuje *zpráva .*

Pro každou `pNotifyStruct` zprávu odkazuje buď **nmhdr** struktury nebo **TBNOTIFY** struktury. Tyto struktury jsou popsány níže:

Struktura **NMHDR** obsahuje následující členy:

```cpp
typedef struct tagNMHDR {
    HWND hwndFrom;  // handle of control sending message
    UINT idFrom;// identifier of control sending message
    UINT code;  // notification code; see below
} NMHDR;
```

- **hwndFrom**

   Okno popisovač ovládacího prvku, který odesílá oznámení. Chcete-li převést `CWnd` tento popisovač na ukazatel, použijte [CWnd::FromHandle](../mfc/reference/cwnd-class.md#fromhandle).

- **idFrom**

   Identifikátor ovládacího prvku odesílajícího oznámení.

- **Kód**

   Kód oznámení. Tento člen může být hodnota specifická pro typ ovládacího prvku, například **TBN_BEGINADJUST** nebo **TTN_NEEDTEXT**, nebo může být jednou z níže uvedených běžných hodnot oznámení:

  - **NM_CLICK** Uživatel klepnul na levé tlačítko myši v ovládacím prvku.

  - **NM_DBLCLK** Uživatel poklepe levým tlačítkem myši v ovládacím prvku.

  - **NM_KILLFOCUS** Ovládací prvek ztratil vstupní fokus.

  - **NM_OUTOFMEMORY** Ovládací prvek nemohl dokončit operaci, protože není k dispozici dostatek paměti.

  - **NM_RCLICK** Uživatel klepnul pravým tlačítkem myši v ovládacím prvku.

  - **NM_RDBLCLK** Uživatel má poklepáním pravé tlačítko myši v ovládacím prvku.

  - **NM_RETURN** Ovládací prvek má vstupní fokus a uživatel stiskl klávesu ENTER.

  - **NM_SETFOCUS** Ovládací prvek obdržel vstupní fokus.

Struktura **TBNOTIFY** obsahuje následující členy:

```cpp
typedef struct {
    NMHDR hdr; // information common to all WM_NOTIFY messages
    int iItem; // index of button associated with notification
    TBBUTTON tbButton; // info about button associated withnotification
    int cchText;   // count of characters in button text
    LPSTR lpszText;// address of button text
} TBNOTIFY, FAR* LPTBNOTIFY;
```

- **Hdr**

   Informace společné pro všechny **WM_NOTIFY** zprávy.

- **iPoložka**

   Index tlačítka přidruženého k oznámení.

- **tbButton**

   **TBBUTTON** strukturu, která obsahuje informace o tlačítko panelu nástrojů spojené s oznámením.

- **cchText**

   Počet znaků v textu tlačítka.

- **lpszText**

   Ukazatel na text tlačítka.

Oznámení, která panel nástrojů odesílá, jsou následující:

- **TBN_BEGINADJUST**

   Odesláno, když uživatel začne přizpůsobovat ovládací prvek panelu nástrojů. Ukazatel odkazuje na strukturu **NMHDR,** která obsahuje informace o oznámení. Obslužná rutina nemusí vracet žádnou konkrétní hodnotu.

- **TBN_BEGINDRAG**

   Odesláno, když uživatel začne přetahovat tlačítko v ovládacím prvku panelu nástrojů. Ukazatel odkazuje na **tbnotify** struktury. Člen **iItem** obsahuje nulový index přetahovaného tlačítka. Obslužná rutina nemusí vracet žádnou konkrétní hodnotu.

- **TBN_CUSTHELP**

   Odesláno, když uživatel zvolí tlačítko Nápověda v dialogovém okně Přizpůsobit panel nástrojů. Žádná vrácená hodnota. Ukazatel odkazuje na strukturu **NMHDR,** která obsahuje informace o oznámení. Obslužná rutina nemusí vracet žádnou konkrétní hodnotu.

- **TBN_ENDADJUST**

   Odesláno, když uživatel přestane přizpůsobovat ovládací prvek panelu nástrojů. Ukazatel odkazuje na strukturu **NMHDR,** která obsahuje informace o oznámení. Obslužná rutina nemusí vracet žádnou konkrétní hodnotu.

- **TBN_ENDDRAG**

   Odesláno, když uživatel přestane přetahovat tlačítko v ovládacím prvku panelu nástrojů. Ukazatel odkazuje na **tbnotify** struktury. Člen **iItem** obsahuje nulový index přetahovaného tlačítka. Obslužná rutina nemusí vracet žádnou konkrétní hodnotu.

- **TBN_GETBUTTONINFO**

   Odesláno, když uživatel přizpůsobí ovládací prvek panelu nástrojů. Panel nástrojů používá tuto oznamovací zprávu k načtení informací potřebných v dialogovém okně Přizpůsobit panel nástrojů. Ukazatel odkazuje na **tbnotify** struktury. Člen **iItem** určuje nulový index tlačítka. Členové **pszText** a **cchText** určují adresu a délku aktuálního textu tlačítka ve znacích. Aplikace by měla vyplnit strukturu s informacemi o tlačítku. Vrátí **hodnotu PRAVDA,** pokud byly informace o tlačítku zkopírovány do struktury, jinak **nepravda.**

- **TBN_QUERYDELETE**

   Odesláno v době, kdy uživatel přizpůsobí panel nástrojů a určí, zda lze tlačítko odstranit z ovládacího prvku panelu nástrojů. Ukazatel odkazuje na **tbnotify** struktury. Člen **iItem** obsahuje nulový index tlačítka, které má být odstraněno. Vrátit **hodnotu PRAVDA,** aby bylo tlačítko odstraněno, nebo **nepravda,** aby se zabránilo odstranění tlačítka.

- **TBN_QUERYINSERT**

   Odesláno v době, kdy uživatel přizpůsobí ovládací prvek panelu nástrojů, aby zjistil, zda může být tlačítko vloženo nalevo od daného tlačítka. Ukazatel odkazuje na **tbnotify** struktury. Člen **iItem** obsahuje nulový index tlačítka, které má být vloženo. Vrátit **hodnotu PRAVDA,** aby bylo možné tlačítko vložit před dané tlačítko nebo **NEPRAVDA,** aby se zabránilo vložení tlačítka.

- **TBN_RESET**

   Odesláno, když uživatel resetuje obsah dialogového okna Přizpůsobit panel nástrojů. Ukazatel odkazuje na strukturu **NMHDR,** která obsahuje informace o oznámení. Obslužná rutina nemusí vracet žádnou konkrétní hodnotu.

- **TBN_TOOLBARCHANGE**

   Odesláno poté, co uživatel přizpůsobil ovládací prvek panelu nástrojů. Ukazatel odkazuje na strukturu **NMHDR,** která obsahuje informace o oznámení. Obslužná rutina nemusí vracet žádnou konkrétní hodnotu.

## <a name="see-also"></a>Viz také

[Používání atributu CToolBarCtrl](../mfc/using-ctoolbarctrl.md)<br/>
[Ovládací prvky](../mfc/controls-mfc.md)
