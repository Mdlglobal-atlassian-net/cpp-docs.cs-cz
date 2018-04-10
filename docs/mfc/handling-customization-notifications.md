---
title: Zpracování oznámení o přizpůsobení | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
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
dev_langs:
- C++
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
caps.latest.revision: 11
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ec4561fda34ba2b20f7fe46aea52f272eed3b9ab
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="handling-customization-notifications"></a>Zpracování oznámení o přizpůsobení
Běžné prvku panel nástrojů systému Windows obsahuje integrované funkce přizpůsobení, včetně definovaná systémem přizpůsobení dialogové okno, umožnit uživatelům vložit, odstranit nebo změna uspořádání tlačítek panelu nástrojů. Aplikace určuje, zda jsou k dispozici funkce přizpůsobení a ovládací prvky v rozsahu, ke kterému se uživatel může přizpůsobit panelu nástrojů.  
  
 Můžete provádět tyto možnosti přizpůsobení dostupné uživatele tím, že panelu nástrojů `CCS_ADJUSTABLE` stylu. Přizpůsobení funkcí povolí uživateli tlačítko přetáhněte na jiné místo nebo přetažením z panelu nástrojů tlačítko Odebrat. Kromě toho může uživatel poklikejte na panelu nástrojů **přizpůsobení panelu nástrojů** dialogové okno, které umožňuje uživatelům přidání, odstranění a změna uspořádání tlačítek panelu nástrojů. Aplikace můžete zobrazit dialogové okno pomocí [přizpůsobit](../mfc/reference/ctoolbarctrl-class.md#customize) – členská funkce.  
  
 Ovládací prvek panelu nástrojů odešle zprávy s oznámením do nadřazeného okna na každý krok v procesu přizpůsobení. Pokud uživatel obsahuje klávesu SHIFT a zahájí přetahování tlačítka, panelu nástrojů automaticky zpracuje operaci přetažení. Odešle panelu nástrojů **tbn_querydelete –** oznámení do nadřazeného okna k určení, zda může být odstraněny tlačítko. Operaci přetažení končí nadřazeného okna vrátí-li **FALSE**. Panel nástrojů, jinak hodnota zaznamená vstup z myši a čeká na uvolnění tlačítka myši uživateli.  
  
 Když uživatel uvolní tlačítko myši, ovládacím prvkem panel nástrojů Určuje umístění myší. Pokud je kurzor mimo panelu nástrojů, je tlačítko Odstranit. Pokud je kurzor na další tlačítka panelu nástrojů, odešle panelu nástrojů **tbn_queryinsert –** oznámení do nadřazeného okna k určení, pokud může tlačítko Vložit směrem doleva od daného tlačítko. Tlačítko je vložený, pokud nadřazeného okna vrátí **TRUE**, jinak hodnota není. Odešle panelu nástrojů **tbn_toolbarchange –** oznámení signál konci operace přetažení.  
  
 Pokud uživatel zahájí operaci přetažení bez podržíte stisknutou klávesu SHIFT, odešle ovládací prvek panelu nástrojů **tbn_begindrag –** oznámení do okna vlastníka. Aplikace, která implementuje vlastní tlačítko přetahování kód můžete použít tuto zprávu jako signál má začít operace přetažení. Odešle panelu nástrojů **tbn_enddrag –** oznámení signál konci operace přetažení.  
  
 Ovládacím prvku panel nástrojů odešle zprávy oznámení, když uživatel upravuje pomocí panelu nástrojů **přizpůsobení panelu nástrojů** dialogové okno. Odešle panelu nástrojů **tbn_beginadjust –** oznámení po poklepání panelu nástrojů, ale před dialogové okno se vytvoří pole. V dalším kroku panelu nástrojů začne odesílání řadu **tbn_queryinsert –** oznámení zprávy a určete, zda panelu nástrojů umožňuje tlačítka má být vložen. Při vrácení nadřazeného okna **TRUE**, panelu nástrojů zastaví odesílání **tbn_queryinsert –** zpráv s oznámením. Pokud nadřazeného okna nevrátí **TRUE** pro žádné tlačítko panelu nástrojů zničí dialogové okno.  
  
 Ovládací prvek panelu nástrojů v dalším kroku určuje, pokud žádné tlačítka budou odstraněny z panelu nástrojů odesláním jeden **tbn_querydelete –** zpráva oznámení pro každé tlačítko na panelu nástrojů. Vrací nadřazeného okna **TRUE** označíte, tlačítko můžou být odstraněné; jinak vrátí **FALSE**. Panelu nástrojů přidá všechny tlačítka panelu nástrojů do dialogového okna, ale šedě ty, které nemusí být odstraněny.  
  
 Vždy, když je ovládací prvek panelu nástrojů informace o tlačítka v dialogovém okně Upravit panel nástrojů, odešle **tbn_getbuttoninfo –** zprávy oznámení, zadání index tlačítko, pro kterou je informace a Adresa **tbnotify –** struktura. Nadřazené okno musíte vyplnit strukturu příslušné informace.  
  
 **Přizpůsobení panelu nástrojů** dialogové okno obsahuje tlačítko Nápověda a tlačítko pro obnovení. Když uživatel vybere na tlačítko Nápověda, odešle ovládací prvek panelu nástrojů **tbn_custhelp –** oznámení. Nadřazené okno by měl odpovídat tak, že zobrazení informace nápovědy. Dialogové okno odešle **tbn_reset –** oznámení, když uživatel vybere na tlačítko Obnovit. Tato zpráva signalizuje, že panelu nástrojů se chystá znovu inicializovat dialogové okno.  
  
 Tyto zprávy jsou všechny **wm_notify –** zprávy a mohou být ošetřeny v okně vlastníka přidáním položky map zpráv má následující formu do nadřazené okno mapy zpráv:  
  
 `ON_NOTIFY( wNotifyCode, idControl, memberFxn )`  
  
 `wNotifyCode`  
 Oznámení zprávy identifikačního kódu, například **tbn_beginadjust –**.  
  
 `idControl`  
 Identifikátor ovládacího prvku odesílání oznámení.  
  
 `memberFxn`  
 Členské funkce, která se má volat při příjmu tohoto oznámení.  
  
 Členská funkce by deklarovat s následující prototyp:  
  
 `afx_msg void memberFxn( NMHDR * pNotifyStruct, LRESULT * result );`  
  
 Pokud obslužná rutina zpráv oznámení vrátí hodnotu, se musí uvést do **LRESULT** na kterou odkazuje *výsledek*.  
  
 Pro každou zprávu `pNotifyStruct` odkazuje na buď **NMHDR** struktura nebo **tbnotify –** struktura. Tyto struktury jsou následující:  
  
 **NMHDR** struktura obsahuje následující členy:  
  
 `typedef struct tagNMHDR {`  
  
 `HWND hwndFrom;  // handle of control sending message`  
  
 `UINT idFrom;// identifier of control sending message`  
  
 `UINT code;  // notification code; see below`  
  
 `} NMHDR;`  
  
 **hwndFrom**  
 Popisovač okna ovládacího prvku, který odesílá oznámení. Tento popisovač pro převod `CWnd` ukazatelů, použití [CWnd::FromHandle](../mfc/reference/cwnd-class.md#fromhandle).  
  
 **idFrom**  
 Identifikátor ovládacího prvku odesílání oznámení.  
  
 **kód**  
 Kód oznámení. Tento člen může být hodnota specifické pro typ ovládacího prvku, jako například **tbn_beginadjust –** nebo **TTN_NEEDTEXT**, nebo je můžete použít jeden z běžných níže uvedené hodnoty oznámení:  
  
-   **Nm_click –** uživatel klikne levé tlačítko myši v ovládacím prvku.  
  
-   **Nm_dblclk –** uživatel má dvakrát kliknuli levým tlačítkem myši v ovládacím prvku.  
  
-   **Nm_killfocus –** ovládacího prvku došlo ke ztrátě zaměření pro vstup.  
  
-   **Nm_outofmemory –** ovládacího prvku nelze dokončit operaci, protože není k dispozici dostatek paměti.  
  
-   **Nm_rclick –** uživatel klikne pravým tlačítkem myši v ovládacím prvku.  
  
-   **Nm_rdblclk –** uživatel má dvakrát kliknuli pravým tlačítkem myši v ovládacím prvku.  
  
-   **Nm_return –** ovládací prvek má zaměření pro vstup a uživatel má stisknutí klávesy ENTER.  
  
-   **Nm_setfocus –** ovládacího prvku přijal zaměření pro vstup.  
  
 **Tbnotify –** struktura obsahuje následující členy:  
  
 `typedef struct {`  
  
 `NMHDR hdr; // information common to all WM_NOTIFY messages`  
  
 `int iItem; // index of button associated with notification`  
  
 `TBBUTTON tbButton; // info about button associated withnotification`  
  
 `int cchText;   // count of characters in button text`  
  
 `LPSTR lpszText;// address of button text`  
  
 `} TBNOTIFY, FAR* LPTBNOTIFY;`  
  
## <a name="remarks"></a>Poznámky  
 **záhlaví**  
 Informace, které jsou společné pro všechny **wm_notify –** zprávy.  
  
 **Položky**  
 Index tlačítko přidružená oznámení.  
  
 **tbButton**  
 `TBBUTTON`Struktura, která obsahuje informace o tlačítka panelu nástrojů, které jsou přidružené k oznámení.  
  
 **cchText**  
 Počet znaků v textu tlačítka.  
  
 **lpszText**  
 Ukazatel na text tlačítka.  
  
 Oznámení, které odesílá panelu nástrojů jsou následující:  
  
-   **Tbn_beginadjust –** odeslat v případě, že uživatel začne přizpůsobení ovládacím prvku panel nástrojů. Ukazatele odkazuje na **NMHDR** struktura, která obsahuje informace o oznámení. Obslužná rutina nemusí vrátit žádnou konkrétní hodnotu.  
  
-   **Tbn_begindrag –** odeslány v případě, že uživatel zahájí přetahování tlačítka v ovládacím prvku panel nástrojů. Ukazatele odkazuje na **tbnotify –** struktura. **Položky** člen obsahuje index tlačítka přetažen založený na nule. Obslužná rutina nemusí vrátit žádnou konkrétní hodnotu.  
  
-   **Tbn_custhelp –** odeslána, když uživatel vybere v dialogovém okně přizpůsobení panelu nástrojů na tlačítko Nápověda. Žádnou návratovou hodnotu. Ukazatele odkazuje na **NMHDR** struktura, která obsahuje informace o oznámení. Obslužná rutina nemusí vrátit žádnou konkrétní hodnotu.  
  
-   **Tbn_endadjust –** odeslána, když uživatel přestane přizpůsobení ovládacím prvku panel nástrojů. Ukazatele odkazuje na **NMHDR** struktura, která obsahuje informace o oznámení. Obslužná rutina nemusí vrátit žádnou konkrétní hodnotu.  
  
-   **Tbn_enddrag –** odeslány v případě, že uživatel přestane přetahovat tlačítka v ovládacím prvku panel nástrojů. Ukazatele odkazuje na **tbnotify –** struktura. **Položky** člen obsahuje index tlačítka přetažen založený na nule. Obslužná rutina nemusí vrátit žádnou konkrétní hodnotu.  
  
-   **Tbn_getbuttoninfo –** odeslat v případě, že uživatel je přizpůsobení v ovládacím prvku panel nástrojů. Panelu nástrojů používá tato oznámení se načíst informace potřebné pro dialogové okno Přizpůsobit panel nástrojů. Ukazatele odkazuje na **tbnotify –** struktura. **Položky** člen Určuje index založený na nule tlačítka. **PszText** a **cchText** členové zadat adresu a délku ve znacích aktuální text tlačítka. Aplikace by měl vyplnit struktura s informacemi o tlačítko. Vrátí **TRUE** Pokud tlačítko informace byl zkopírován do struktury nebo **FALSE** jinak.  
  
-   **Tbn_querydelete –** odeslaných během uživatele je přizpůsobení panelu nástrojů k určení, zda tlačítko budou odstraněny z ovládacího prvku panel nástrojů. Ukazatele odkazuje na **tbnotify –** struktura. **Položky** člen obsahuje index založený na nule tlačítko Odstranit. Vrátí **TRUE** umožňující na tlačítko Odstranit nebo **FALSE** zabránit tlačítko Probíhá odstraňování.  
  
-   **Tbn_queryinsert –** odeslaných během uživatele je přizpůsobení v ovládacím prvku panel nástrojů k určení, zda může tlačítko Vložit směrem doleva od daného tlačítko. Ukazatele odkazuje na **tbnotify –** struktura. **Položky** člen obsahuje index založený na nule tlačítka, která má být vložen. Vrátí **TRUE** umožňující tlačítko má být vložen před dané tlačítko nebo **FALSE** zabránit tlačítko vkládání.  
  
-   **Tbn_reset –** odeslat v případě, že uživatel obnoví obsah dialogového okna přizpůsobení panelu nástrojů. Ukazatele odkazuje na **NMHDR** struktura, která obsahuje informace o oznámení. Obslužná rutina nemusí vrátit žádnou konkrétní hodnotu.  
  
-   **Tbn_toolbarchange –** odesílá poté, co uživatel má přizpůsobit ovládacím prvku panel nástrojů. Ukazatele odkazuje na **NMHDR** struktura, která obsahuje informace o oznámení. Obslužná rutina nemusí vrátit žádnou konkrétní hodnotu.  
  
## <a name="see-also"></a>Viz také  
 [Používání atributu CToolBarCtrl](../mfc/using-ctoolbarctrl.md)   
 [Ovládací prvky](../mfc/controls-mfc.md)

