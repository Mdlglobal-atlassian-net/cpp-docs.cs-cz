---
title: Cbasetabbedpane – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CBaseTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane::AddTab
- AFXBASETABBEDPANE/CBaseTabbedPane::AllowDestroyEmptyTabbedPane
- AFXBASETABBEDPANE/CBaseTabbedPane::ApplyRestoredTabInfo
- AFXBASETABBEDPANE/CBaseTabbedPane::CanFloat
- AFXBASETABBEDPANE/CBaseTabbedPane::CanSetCaptionTextToTabName
- AFXBASETABBEDPANE/CBaseTabbedPane::ConvertToTabbedDocument
- AFXBASETABBEDPANE/CBaseTabbedPane::DetachPane
- AFXBASETABBEDPANE/CBaseTabbedPane::EnableSetCaptionTextToTabName
- AFXBASETABBEDPANE/CBaseTabbedPane::FillDefaultTabsOrderArray
- AFXBASETABBEDPANE/CBaseTabbedPane::FindBarByTabNumber
- AFXBASETABBEDPANE/CBaseTabbedPane::FindPaneByID
- AFXBASETABBEDPANE/CBaseTabbedPane::FloatTab
- AFXBASETABBEDPANE/CBaseTabbedPane::GetDefaultTabsOrder
- AFXBASETABBEDPANE/CBaseTabbedPane::GetFirstVisibleTab
- AFXBASETABBEDPANE/CBaseTabbedPane::GetMinSize
- AFXBASETABBEDPANE/CBaseTabbedPane::GetPaneIcon
- AFXBASETABBEDPANE/CBaseTabbedPane::GetPaneList
- AFXBASETABBEDPANE/CBaseTabbedPane::GetTabArea
- AFXBASETABBEDPANE/CBaseTabbedPane::GetTabsNum
- AFXBASETABBEDPANE/CBaseTabbedPane::GetUnderlyingWindow
- AFXBASETABBEDPANE/CBaseTabbedPane::GetVisibleTabsNum
- AFXBASETABBEDPANE/CBaseTabbedPane::HasAutoHideMode
- AFXBASETABBEDPANE/CBaseTabbedPane::IsHideSingleTab
- AFXBASETABBEDPANE/CBaseTabbedPane::RecalcLayout
- AFXBASETABBEDPANE/CBaseTabbedPane::RemovePane
- AFXBASETABBEDPANE/CBaseTabbedPane::SetAutoDestroy
- AFXBASETABBEDPANE/CBaseTabbedPane::SetAutoHideMode
- AFXBASETABBEDPANE/CBaseTabbedPane::ShowTab
dev_langs:
- C++
helpviewer_keywords:
- CBaseTabbedPane [MFC], AddTab
- CBaseTabbedPane [MFC], AllowDestroyEmptyTabbedPane
- CBaseTabbedPane [MFC], ApplyRestoredTabInfo
- CBaseTabbedPane [MFC], CanFloat
- CBaseTabbedPane [MFC], CanSetCaptionTextToTabName
- CBaseTabbedPane [MFC], ConvertToTabbedDocument
- CBaseTabbedPane [MFC], DetachPane
- CBaseTabbedPane [MFC], EnableSetCaptionTextToTabName
- CBaseTabbedPane [MFC], FillDefaultTabsOrderArray
- CBaseTabbedPane [MFC], FindBarByTabNumber
- CBaseTabbedPane [MFC], FindPaneByID
- CBaseTabbedPane [MFC], FloatTab
- CBaseTabbedPane [MFC], GetDefaultTabsOrder
- CBaseTabbedPane [MFC], GetFirstVisibleTab
- CBaseTabbedPane [MFC], GetMinSize
- CBaseTabbedPane [MFC], GetPaneIcon
- CBaseTabbedPane [MFC], GetPaneList
- CBaseTabbedPane [MFC], GetTabArea
- CBaseTabbedPane [MFC], GetTabsNum
- CBaseTabbedPane [MFC], GetUnderlyingWindow
- CBaseTabbedPane [MFC], GetVisibleTabsNum
- CBaseTabbedPane [MFC], HasAutoHideMode
- CBaseTabbedPane [MFC], IsHideSingleTab
- CBaseTabbedPane [MFC], RecalcLayout
- CBaseTabbedPane [MFC], RemovePane
- CBaseTabbedPane [MFC], SetAutoDestroy
- CBaseTabbedPane [MFC], SetAutoHideMode
- CBaseTabbedPane [MFC], ShowTab
ms.assetid: f22c0080-5b29-4a0a-8f74-8f0a4cd2dbcf
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: addbc7c81c8cd38f44b7b1004c0b4e23ca183ecb
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50067317"
---
# <a name="cbasetabbedpane-class"></a>Cbasetabbedpane – třída

Rozšiřuje funkce [CDockablePane – třída](../../mfc/reference/cdockablepane-class.md) pro podporu vytváření oken s kartami.

## <a name="syntax"></a>Syntaxe

```
class CBaseTabbedPane : public CDockablePane
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|`CBaseTabbedPane::CBaseTabbedPane`|Výchozí konstruktor.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CBaseTabbedPane::AddTab](#addtab)|Přidá novou kartu do podokna s kartami.|
|[CBaseTabbedPane::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|Určuje, zda lze zničit prázdné podokno s kartami.|
|[CBaseTabbedPane::ApplyRestoredTabInfo](#applyrestoredtabinfo)|Použije nastavení karet, které jsou načteny z registru, do podokna s kartami.|
|[CBaseTabbedPane::CanFloat](#canfloat)|Určuje, zda v podokně můžete uvolnit. (Přepíše [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).)|
|[CBaseTabbedPane::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|Určuje, zda Titulek podokna s kartami by měl zobrazit stejný text jako na aktivní kartě.|
|[CBaseTabbedPane::ConvertToTabbedDocument](#converttotabbeddocument)|(Přepíše [CDockablePane::ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument).)|
|[CBaseTabbedPane::DetachPane](#detachpane)|Převede jednu nebo více ukotvitelná podokna do dokumentů s kartami MDI.|
|[CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)|Povolí nebo zakáže možnost podokna s kartami pro synchronizaci text titulku se text popisku na aktivní kartě.|
|[CBaseTabbedPane::FillDefaultTabsOrderArray](#filldefaulttabsorderarray)|Interní pořadí obnoví do výchozího stavu.|
|[CBaseTabbedPane::FindBarByTabNumber](#findbarbytabnumber)|Vrátí podokno, které se nachází na kartě, když na kartě je identifikován index založený na nule karty.|
|||
|[CBaseTabbedPane::FindPaneByID](#findpanebyid)|Vrátí podokno, které se identifikují pomocí ID podokně.|
|[CBaseTabbedPane::FloatTab](#floattab)|Podokno, ale pouze čísel s plovoucí čárkou, pokud se v podokně se aktuálně nachází odpojitelných kartě.|
|[CBaseTabbedPane::GetDefaultTabsOrder](#getdefaulttabsorder)|Vrátí výchozí pořadí karet na panelu.|
|[CBaseTabbedPane::GetFirstVisibleTab](#getfirstvisibletab)|Načte ukazatel na první kartě zobrazené.|
|[CBaseTabbedPane::GetMinSize](#getminsize)|Získá minimální povolená velikost podokna. (Přepíše [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).)|
|[CBaseTabbedPane::GetPaneIcon](#getpaneicon)|Vrátí popisovač do ikony podokna. (Přepíše [CBasePane::GetPaneIcon](../../mfc/reference/cbasepane-class.md#getpaneicon).)|
|[CBaseTabbedPane::GetPaneList](#getpanelist)|Vrátí seznam podoken, které jsou obsaženy v podokně s kartami.|
|[CBaseTabbedPane::GetTabArea](#gettabarea)|Vrací ohraničující rámečky pro horní a dolní části karty.|
|[CBaseTabbedPane::GetTabsNum](#gettabsnum)|Vrátí počet karty v okně kartu.|
|[CBaseTabbedPane::GetUnderlyingWindow](#getunderlyingwindow)|Získá základní okna Karta (zabalená).|
|[CBaseTabbedPane::GetVisibleTabsNum](#getvisibletabsnum)|Vrátí počet zobrazených karty.|
|[CBaseTabbedPane::HasAutoHideMode](#hasautohidemode)|Určuje, zda podokno s kartami můžete přepnout do režimu automatického skrytí.|
|[CBaseTabbedPane::IsHideSingleTab](#ishidesingletab)|Určuje, zda je skrytý podokna s kartami, pokud pouze jedna karta se zobrazí.|
|`CBaseTabbedPane::LoadSiblingPaneIDs`|Používat interně během serializace.|
|[CBaseTabbedPane::RecalcLayout](#recalclayout)|Přepočítá rozložení informace o podokně. (Přepíše [CPane::RecalcLayout](../../mfc/reference/cpane-class.md#recalclayout).)|
|[CBaseTabbedPane::RemovePane](#removepane)|Podokno se odebere z podokna s kartami.|
|`CBaseTabbedPane::SaveSiblingBarIDs`|Používat interně během serializace.|
|`CBaseTabbedPane::Serialize`|(Přepíše [CDockablePane::Serialize](cdockablepane-class.md).)|
|`CBaseTabbedPane::SerializeTabWindow`|Používat interně během serializace.|
|[CBaseTabbedPane::SetAutoDestroy](#setautodestroy)|Určuje, zda s kartami ovládací panel zničí automaticky.|
|[CBaseTabbedPane::SetAutoHideMode](#setautohidemode)|Přepíná mezi zobrazí ukotvené podokno a v režimu automatického skrytí. (Přepíše [CDockablePane::SetAutoHideMode](../../mfc/reference/cdockablepane-class.md#setautohidemode).)|
|[CBaseTabbedPane::ShowTab](#showtab)|Zobrazí nebo skryje na kartě.|

## <a name="remarks"></a>Poznámky

Tato třída je abstraktní třída a nelze vytvořit instanci. Implementuje služby, které jsou společné pro všechny druhy podokně s kartami.

V současné době knihovny obsahuje dvě třídy odvozené podokna s kartami: [ctabbedpane – třída](../../mfc/reference/ctabbedpane-class.md) a [CMFCOutlookBar – třída](../../mfc/reference/cmfcoutlookbar-class.md).

A `CBaseTabbedPane` zabalí ukazatel na objekt [cmfcbasetabctrl – třída](../../mfc/reference/cmfcbasetabctrl-class.md) objektu. [Cmfcbasetabctrl – třída](../../mfc/reference/cmfcbasetabctrl-class.md) se pak stane podřízené okno podokna s kartami.

Další informace o tom, jak vytvořit podokně s kartami, naleznete v tématu [CDockablePane – třída](../../mfc/reference/cdockablepane-class.md), [ctabbedpane – třída](../../mfc/reference/ctabbedpane-class.md), a [CMFCOutlookBar – třída](../../mfc/reference/cmfcoutlookbar-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

`CBaseTabbedPane`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxBaseTabbedPane.h

##  <a name="addtab"></a>  CBaseTabbedPane::AddTab

Přidá novou kartu do podokna s kartami.

```
virtual BOOL AddTab(
    CWnd* pNewBar,
    BOOL bVisible = TRUE,
    BOOL bSetActive = TRUE,
    BOOL bDetachable = TRUE);
```

### <a name="parameters"></a>Parametry

*pNewBar*<br/>
[out v] Ukazatel na panelu Přidat. Tento ukazatel může stát neplatnými po volání této metody. Další informace najdete v části poznámky.

*bVisible*<br/>
[in] Hodnota TRUE pro zviditelnění na kartě; v opačném případě hodnota FALSE.

*bSetActive*<br/>
[in] TRUE, pokud chcete provést na kartě na aktivní kartě; v opačném případě hodnota FALSE.

*bDetachable*<br/>
[in] TRUE, pokud chcete provést na kartě odpojitelných; v opačném případě hodnota FALSE.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud se podokno se úspěšně přidal jako kartu a nebyl zničeny v procesu. FALSE, pokud je podokno přidávaný objekt typu `CBaseTabbedPane`. Další informace najdete v části poznámky.

### <a name="remarks"></a>Poznámky

Volejte tuto metodu za účelem přidání podokna jako novou kartu na podokno s kartami. Pokud *pNewBar* odkazuje na objekt typu `CBaseTabbedPane`, všechny její karty se zkopírují do podokna s kartami a potom *pNewBar* zničen. Proto *pNewBar* změní neplatný ukazatel by se neměl používat.

##  <a name="allowdestroyemptytabbedpane"></a>  CBaseTabbedPane::AllowDestroyEmptyTabbedPane

Určuje, zda lze zničit prázdné podokno s kartami.

```
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud lze zničit prázdné podokno s kartami; v opačném případě hodnota FALSE. Výchozí implementace vždy vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Pokud zničení, není povolena prázdná podokna s kartami, skryje rozhraní podokno.

##  <a name="applyrestoredtabinfo"></a>  CBaseTabbedPane::ApplyRestoredTabInfo

Načte nastavení na kartě z registru a aplikuje je do podokna s kartami.

```
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```

### <a name="parameters"></a>Parametry

*bUseTabIndexes*<br/>
[in] Tento parametr se používá interně v rámci rozhraní.

### <a name="remarks"></a>Poznámky

Tato metoda je volána rozhraním, když se znovu načte dokovací informace o stavu z registru. Metoda získává informace o pořadí a názvy karet pro podokna s kartami.

##  <a name="canfloat"></a>  CBaseTabbedPane::CanFloat

Určuje, zda podokno s kartami můžete uvolnit.

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud se v podokně můžete uvolnit; v opačném případě hodnota FALSE.

##  <a name="cansetcaptiontexttotabname"></a>  CBaseTabbedPane::CanSetCaptionTextToTabName

Určuje, zda Titulek podokna s kartami by měl zobrazit stejný text jako na aktivní kartě.

```
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud text titulku podokna s kartami je nastavena na text na aktivní kartě; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Metoda se používá k určení, zda bude text zobrazen na titulek duplicity podokna s kartami popisek na aktivní kartě. Můžete povolit nebo zakázat tuto funkci voláním [CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname).

##  <a name="converttotabbeddocument"></a>  CBaseTabbedPane::ConvertToTabbedDocument

Převede jednu nebo více ukotvitelná podokna do dokumentů s kartami MDI.

```
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```

### <a name="parameters"></a>Parametry

*bActiveTabOnly*<br/>
[in] Při převodu podokna s kartami, zadejte hodnotu PRAVDA pro převod na aktivní kartě. Zadáním hodnoty FALSE převést všechny karty na panelu.

##  <a name="detachpane"></a>  CBaseTabbedPane::DetachPane

Odpojí podokno z podokna s kartami.

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[in] Ukazatel do podokna odpojit.

*bHide*<br/>
[in] Logický parametr, který určuje, zda rozhraní skryje panel po je odpojená.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud rozhraní framework úspěšně odpojí podokna. FALSE v případě *pBar* má hodnotu NULL nebo odkazuje na podokno, které se nenachází v podokně s kartami.

### <a name="remarks"></a>Poznámky

Rozhraní framework čísel s plovoucí čárkou v odpojeném podokně Pokud je to možné. Další informace najdete v tématu [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).

##  <a name="enablesetcaptiontexttotabname"></a>  CBaseTabbedPane::EnableSetCaptionTextToTabName

Povolí nebo zakáže možnost podokna s kartami pro synchronizaci text titulku se text popisku na aktivní kartě.

```
virtual void EnableSetCaptionTextToTabName(BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[in] TRUE, pokud chcete synchronizovat Titulek podokna s kartami s titulkem aktivní kartě; v opačném případě hodnota FALSE.

##  <a name="filldefaulttabsorderarray"></a>  CBaseTabbedPane::FillDefaultTabsOrderArray

Interní pořadí obnoví do výchozího stavu.

```
void FillDefaultTabsOrderArray();
```

### <a name="remarks"></a>Poznámky

Tato metoda je volána, když rozhraní obnoví panel aplikace Outlook k počáteční stav.

##  <a name="findpanebyid"></a>  CBaseTabbedPane::FindPaneByID

Vrátí podokno identifikují pomocí ID podokně.

```
virtual CWnd* FindPaneByID(UINT uBarID);
```

### <a name="parameters"></a>Parametry

*uBarID*<br/>
[in] Určuje ID v podokně, který se má najít.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na podokno, pokud byl nalezen; v opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

Tato metoda Porovná všechny karty v podokně a vrátí se zadané podle ID *uBarID* parametru.

##  <a name="findbarbytabnumber"></a>  CBaseTabbedPane::FindBarByTabNumber

Vrátí podokno, které se nachází na kartě.

```
virtual CWnd* FindBarByTabNumber(
    int nTabNum,
    BOOL bGetWrappedBar = FALSE);
```

### <a name="parameters"></a>Parametry

*nTabNum*<br/>
[in] Určuje index založený na nule kartě k načtení.

*bGetWrappedBar*<br/>
[in] TRUE, pokud chcete vrátit základní (zabalená) okno podokna místo v podokně sama o sobě; v opačném případě FALSE. To platí jenom pro odvozený z podokna [cdockablepaneadapter –](../../mfc/reference/cdockablepaneadapter-class.md).

### <a name="return-value"></a>Návratová hodnota

Pokud se najde v podokně, pak je vrácen platný ukazatel do podokna vyhledávaná; v opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

Volejte tuto metodu za účelem načtení podokně umístěných v kartě určené *nTabNum* parametru.

##  <a name="floattab"></a>  CBaseTabbedPane::FloatTab

Podokno, ale pouze čísel s plovoucí čárkou, pokud se v podokně se aktuálně nachází odpojitelných kartě.

```
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[out v] Ukazatel na podokně s plovoucí desetinnou čárkou.

*nTabID*<br/>
[in] Určuje index založený na nule na kartu pro plovoucí desetinnou čárkou.

*dockMethod*<br/>
[in] Určuje způsob, kterým uvolnit podokně. Další informace najdete v části poznámky.

*bHide*<br/>
[in] TRUE, pokud chcete skrýt podokno před plovoucí; v opačném případě hodnota FALSE.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud se v podokně obtékané; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Volejte tuto metodu za účelem plovoucí podokno, které se aktuálně nachází odpojitelných kartě.

Pokud chcete odpojit podokno prostřednictvím kódu programu, zadejte DM_SHOW pro *dockMethod* parametru. Pokud chcete uvolnit podokno na stejné pozici, kde obtékané dříve, zadejte DM_DBL_CLICK jako *dockMethod* parametru.

##  <a name="getdefaulttabsorder"></a>  CBaseTabbedPane::GetDefaultTabsOrder

Vrátí výchozí pořadí karet na panelu.

```
const CArray<int,int>& GetDefaultTabsOrder();
```

### <a name="return-value"></a>Návratová hodnota

A `CArray` objekt, který určuje výchozí pořadí karet na panelu.

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto metodu při panel aplikace Outlook je resetování na počáteční stav.

##  <a name="getfirstvisibletab"></a>  CBaseTabbedPane::GetFirstVisibleTab

Načte ukazatel na první kartě zobrazené.

```
virtual CWnd* GetFirstVisibleTab(int& iTabNum);
```

### <a name="parameters"></a>Parametry

*iTabNum*<br/>
[in] Odkaz na celé číslo. Tato metoda zápisy z nuly vycházející index první karta zobrazené pro tento parametr nebo -1, pokud ne, zobrazí se karta nachází.

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, ukazatel na první zobrazené karta; v opačném případě hodnota NULL.

##  <a name="getminsize"></a>  CBaseTabbedPane::GetMinSize

Získá minimální povolená velikost podokna.

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
[out] A `CSize` objekt, který je vyplněna minimální povolenou velikost.

### <a name="remarks"></a>Poznámky

Pokud je aktivní konzistentní zpracování podokna minimální velikostí ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)), *velikost* je vyplněna minimální povolená velikost na aktivní kartě. V opačném případě *velikost* je vyplněna návratová hodnota [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).

##  <a name="getpaneicon"></a>  CBaseTabbedPane::GetPaneIcon

Získá minimální povolená velikost podokna.

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
[out] A `CSize` objekt, který je vyplněna minimální povolenou velikost.

### <a name="remarks"></a>Poznámky

Pokud je aktivní konzistentní zpracování podokna minimální velikostí ( [CPane::m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)), *velikost* je vyplněna minimální povolená velikost na aktivní kartě. V opačném případě *velikost* je vyplněna návratová hodnota [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).

##  <a name="getpanelist"></a>  CBaseTabbedPane::GetPaneList

Vrátí seznam podoken, které jsou obsaženy v podokně s kartami.

```
virtual void GetPaneList(
    CObList& lst,
    CRuntimeClass* pRTCFilter = NULL);
```

### <a name="parameters"></a>Parametry

*obrázků*<br/>
[out] A `CObList` , který je vyplněna podoken, které jsou obsaženy v podokně s kartami.

*pRTCFilter*<br/>
[in] Pokud hodnota není NULL, vrácený seznam obsahuje pouze podoken, které jsou zadané runtime třídy.

##  <a name="gettabarea"></a>  CBaseTabbedPane::GetTabArea

Vrací ohraničující rámečky pro horní a dolní části karty.

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const = 0;
```

### <a name="parameters"></a>Parametry

*rectTabAreaTop*<br/>
[out] Přijímá souřadnice obrazovky oblasti karta nahoře.

*rectTabAreaBottom*<br/>
[out] Přijímá souřadnice obrazovky nižší oblasti karet.

### <a name="remarks"></a>Poznámky

Volejte tuto metodu za účelem určení ohraničovacího obdélníků v souřadnicovém systému obrazovky, pro oblasti horní a dolní karty.

##  <a name="gettabsnum"></a>  CBaseTabbedPane::GetTabsNum

Vrátí počet karty v okně kartu.

```
virtual int GetTabsNum() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet karet v podokně s kartami.

##  <a name="getunderlyingwindow"></a>  CBaseTabbedPane::GetUnderlyingWindow

Získá základní okna Karta (zabalená).

```
virtual CMFCBaseTabCtrl* GetUnderlyingWindow();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na podkladové okno s kartou.

##  <a name="getvisibletabsnum"></a>  CBaseTabbedPane::GetVisibleTabsNum

Vrátí počet viditelných karty.

```
virtual int GetVisibleTabsNum() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet viditelné karty, které budou mít větší než nebo rovna hodnotě nula.

### <a name="remarks"></a>Poznámky

Voláním této metody lze určit počet viditelných karet v podokně s kartami.

##  <a name="hasautohidemode"></a>  CBaseTabbedPane::HasAutoHideMode

Určuje, zda podokno s kartami můžete přepnout do režimu automaticky skrývat.

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud se v podokně můžete přepnout do režimu automatické skrývání; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Pokud je zakázané automatické skrývání režimu, se neobjeví tlačítko PIN kód se zobrazí na titulek podokna s kartami.

##  <a name="ishidesingletab"></a>  CBaseTabbedPane::IsHideSingleTab

Určuje, zda je skrytý podokna s kartami, pokud pouze jedna karta se zobrazí.

```
virtual BOOL IsHideSingleTab() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud okno s kartou není zobrazený v případě viditelná pouze jedna karta; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Pokud se v podokně nezobrazí, protože je otevřená pouze jedna karta, můžete volat tuto metodu za účelem určení, zda podokno s kartami pracuje správně.

##  <a name="removepane"></a>  CBaseTabbedPane::RemovePane

Podokno se odebere z podokna s kartami.

```
virtual BOOL RemovePane(CWnd* pBar);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[out v] Ukazatel do podokna odebrat z podokna s kartami.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud v podokně byla úspěšně odebrána z podokna s kartami a podokna s kartami jsou pořád platné. FALSE, pokud poslední podokno se odebral z podokna s kartami a podokna s kartami je zničení. Pokud vrácená hodnota je FALSE, nepoužívejte v podokně s kartami víc.

### <a name="remarks"></a>Poznámky

Volejte tuto metodu za účelem odebrání podokně určené *pBar* parametr z podokna s kartami.

##  <a name="setautodestroy"></a>  CBaseTabbedPane::SetAutoDestroy

Určuje, zda s kartami ovládací panel zničí automaticky.

```
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*bAutoDestroy*<br/>
[in] Hodnota TRUE, pokud se podokno s kartami vytvořil dynamicky a nejsou řízení životnosti; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Nastavit automatické zničení režim na hodnotu TRUE v případě, že vytvoříte podokna s kartami dynamicky a nejsou řízení svého životního cyklu. Pokud automatické zničení režimu je hodnota TRUE, v podokně s kartami zničí automaticky v rámci rozhraní.

##  <a name="showtab"></a>  CBaseTabbedPane::ShowTab

Zobrazí nebo skryje na kartě.

```
virtual BOOL ShowTab(
    CWnd* pBar,
    BOOL bShow,
    BOOL bDelay,
    BOOL bActivate);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[in] Ukazatel do podokna zobrazení nebo skrytí.

*bShow*<br/>
[in] TRUE, pokud chcete zobrazit podokno; FALSE, pokud chcete skrýt podokno.

*bDelay*<br/>
[in] Hodnota TRUE pro úpravy rozložení karet; zpoždění v opačném případě hodnota FALSE.

*bActivate*<br/>
[in] TRUE, pokud chcete provést na kartě na aktivní kartě; v opačném případě hodnota FALSE.

### <a name="return-value"></a>Návratová hodnota

Hodnota TRUE, pokud na kartě byla buď zobrazený nebo skrytý úspěšně; v opačném případě hodnota FALSE.

### <a name="remarks"></a>Poznámky

Při volání této metody na stavového řádku je buď zobrazený nebo skrytý, závisí na hodnotě *bShow* parametru. Je-li skrýt kartu a je poslední viditelné zarážky v okně základní kartu, je skrytý podokna s kartami. Pokud na kartě se zobrazí, pokud nebyly dříve žádné tabulátory viditelné, zobrazí se podokno s kartami.

##  <a name="recalclayout"></a>  CBaseTabbedPane::RecalcLayout

Přepočítá rozložení informace o podokně.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Poznámky

Pokud se v podokně je s plovoucí desetinnou čárkou, tato metoda upozorní rozhraní pro změnu velikosti panelu na aktuální velikost okna s minirámcem.

Pokud je ukotven v podokně, tato metoda nemá žádný účinek.

##  <a name="setautohidemode"></a>  CBaseTabbedPane::SetAutoHideMode

Nastaví režim automatického skrytí podokna s odnímatelnými v podokně s kartami.

```
virtual CMFCAutoHideToolBar* SetAutoHideMode(
    BOOL bMode,
    DWORD dwAlignment,
    CMFCAutoHideToolBar* pCurrAutoHideBar = NULL,
    BOOL bUseTimer = TRUE);
```

### <a name="parameters"></a>Parametry

*bMode*<br/>
[in] TRUE, pokud chcete povolit režim automatického skrytí; FALSE, pokud chcete zapnout pravidelné dokovací režim.

*dwAlignment*<br/>
[in] Určuje zarovnání automatického schovávání podokno, které se má vytvořit. Seznam možných hodnot najdete v tématu [CPane::MoveByAlignment](../../mfc/reference/cpane-class.md#movebyalignment).

*pCurrAutoHideBar*<br/>
[out v] Ukazatel na aktuální automatického schovávání panelu nástrojů. Může mít hodnotu NULL.

*bUseTimer*<br/>
[in] Určuje, zda automatického schovávání efekt použít, když uživatel přejde do režimu automatického skrytí podokna nebo skrytí podokna okamžitě.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na automatického schovávání panelu nástrojů, který je vytvořen při přepnutí do režimu automatického skrytí nebo hodnota NULL, pokud je vytvořen bez nástrojů.

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto metodu, když uživatel vybere tlačítko připnout do podokna s kartami přepnout do režimu automatického skrytí nebo do normálního režimu ukotvení.

Automaticky skrýt režim je nastaven pro každý odpojitelných podokno v podokně s kartami. Podoken, které jsou mimo odpojitelných jsou ignorovány. Další informace najdete v tématu [CMFCBaseTabCtrl::EnableTabDetach](../../mfc/reference/cmfcbasetabctrl-class.md#enabletabdetach).

Voláním této metody lze přepnout podokno s kartami na režim automatického schovávání prostřednictvím kódu programu. V podokně musí být ukotveno, do okna hlavního rámce ( [CDockablePane::GetDefaultPaneDivider](../../mfc/reference/cdockablepane-class.md#getdefaultpanedivider) musí vrátit platný ukazatel [cpanedivider –](../../mfc/reference/cpanedivider-class.md)).

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane – třída](../../mfc/reference/cdockablepane-class.md)
