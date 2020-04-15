---
title: Třída CBaseTabbedPane
ms.date: 11/04/2016
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
ms.openlocfilehash: ce7c48263ed511545757c94d61552e6206e74a00
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81352859"
---
# <a name="cbasetabbedpane-class"></a>Třída CBaseTabbedPane

Rozšiřuje funkce [třídy CDockablePane tak,](../../mfc/reference/cdockablepane-class.md) aby podporovala vytváření oken s kartami.

## <a name="syntax"></a>Syntaxe

```
class CBaseTabbedPane : public CDockablePane
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|`CBaseTabbedPane::CBaseTabbedPane`|Výchozí konstruktor.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CBaseTabbedPane::AddTab](#addtab)|Přidá novou kartu do podokna s kartami.|
|[CBaseTabbedPane::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|Určuje, zda lze zničit prázdné podokno s kartami.|
|[CBaseTabbedPane::ApplyRestoredTabInfo](#applyrestoredtabinfo)|Použije nastavení karty, která jsou načtena z registru, na podokno s kartami.|
|[CBaseTabbedPane::CanFloat](#canfloat)|Určuje, zda může být podokno plovoucí. (Přepíše [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).)|
|[CBaseTabbedPane::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|Určuje, zda má titulek podokna s kartami zobrazovat stejný text jako aktivní karta.|
|[CBaseTabbedPane::ConvertToTabbedDocument](#converttotabbeddocument)|(Přepíše [CDockablePane::ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument).)|
|[CBaseTabbedPane::DetachPane](#detachpane)|Převede jedno nebo více ukotvených podoken na dokumenty s kartami MDI.|
|[CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)|Povolí nebo zakáže možnost podokna s kartami synchronizovat text titulků s textem popisku na aktivní kartě.|
|[CBaseTabbedPane::FillDefaultTabsOrderArray](#filldefaulttabsorderarray)|Obnoví výchozí stav vnitřního pořadí polí.|
|[CBaseTabbedPane::FindBarByTabNumber](#findbarbytabnumber)|Vrátí podokno, které je umístěno na kartě, když je karta označena indexem karty s nulou.|
|||
|[CBaseTabbedPane::FindPaneByID](#findpanebyid)|Vrátí podokno, které je identifikováno ID podokna.|
|[CBaseTabbedPane::FloatTab](#floattab)|Plovoucí podokno, ale pouze v případě, že podokno aktuálně umístěnna na odpojitelné kartu.|
|[CBaseTabbedPane::GetDefaultTabsOrder](#getdefaulttabsorder)|Vrátí výchozí pořadí karet v podokně.|
|[CBaseTabbedPane::GetFirstVisibleTab](#getfirstvisibletab)|Načte ukazatel na první zobrazenou kartu.|
|[CBaseTabbedPane::GetMinSize](#getminsize)|Načte minimální povolenou velikost podokna. (Přepíše [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).)|
|[CBaseTabbedPane::GetPaneIcon](#getpaneicon)|Vrátí popisovač na ikonu podokna. (Přepíše [CBasePane::GetPaneIcon](../../mfc/reference/cbasepane-class.md#getpaneicon).)|
|[CBaseTabbedPane::GetPaneList](#getpanelist)|Vrátí seznam podoken, které jsou obsaženy v podokně s kartami.|
|[CBaseTabbedPane::GetTabArea](#gettabarea)|Vrátí ohraničovací obdélníky pro horní a dolní oblast tabulátoru.|
|[CBaseTabbedPane::GetTabsNum](#gettabsnum)|Vrátí počet karet v okně karty.|
|[CBaseTabbedPane::GetUnderlyingWindow](#getunderlyingwindow)|Získá základní (zabalené) okno karty.|
|[CBaseTabbedPane::GetVisibleTabsNum](#getvisibletabsnum)|Vrátí počet zobrazených karet.|
|[CBaseTabbedPane::HasAutoHideMode](#hasautohidemode)|Určuje, zda lze podokno s kartami přepnout do režimu automatického skrytí.|
|[CBaseTabbedPane::IsHideSingleTab](#ishidesingletab)|Určuje, zda je podokno s kartami skryté, pokud se zobrazí pouze jedna karta.|
|`CBaseTabbedPane::LoadSiblingPaneIDs`|Používá se interně během serializace.|
|[CBaseTabbedPane::RecalcLayout](#recalclayout)|Přepočítá informace o rozložení podokna. (Přepíše [CPane::RecalcLayout](../../mfc/reference/cpane-class.md#recalclayout).)|
|[CBaseTabbedPane::RemovePane](#removepane)|Odebere podokno z podokna s kartami.|
|`CBaseTabbedPane::SaveSiblingBarIDs`|Používá se interně během serializace.|
|`CBaseTabbedPane::Serialize`|(Přepíše [CDockablePane::Serializovat](cdockablepane-class.md).)|
|`CBaseTabbedPane::SerializeTabWindow`|Používá se interně během serializace.|
|[CBaseTabbedPane::SetAutoDestroy](#setautodestroy)|Určuje, zda bude ovládací panel s kartami automaticky zničen.|
|[CBaseTabbedPane::SetAutoHideMode](#setautohidemode)|Přepíná dokovací podokno mezi zobrazeným a automaticky skrytým režimem. (Přepíše [CDockablePane::SetAutoHideMode](../../mfc/reference/cdockablepane-class.md#setautohidemode).)|
|[CBaseTabbedPane::Zobrazit záložku](#showtab)|Zobrazí nebo skryje kartu.|

## <a name="remarks"></a>Poznámky

Tato třída je abstraktní třídy a nelze vytvořit instanci. Implementuje služby, které jsou společné pro všechny druhy tabbed.

Knihovna v současné době obsahuje dvě odvozené třídy podokna s kartami: [CTabbedPane Class](../../mfc/reference/ctabbedpane-class.md) a [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md).

Objekt `CBaseTabbedPane` obtéká ukazatel na objekt [třídy CMFCBaseTabCtrl.](../../mfc/reference/cmfcbasetabctrl-class.md) [Třída CMFCBaseTabCtrl se](../../mfc/reference/cmfcbasetabctrl-class.md) pak stane podřízeným oknem podokna s kartami.

Další informace o vytváření podoken s kartami naleznete v tématech [CDockablePane Class](../../mfc/reference/cdockablepane-class.md), [CTabbedPane Class](../../mfc/reference/ctabbedpane-class.md)a [CMFCOutlookBar Class](../../mfc/reference/cmfcoutlookbar-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

[Cwnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

`CBaseTabbedPane`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxBaseTabbedPane.h

## <a name="cbasetabbedpaneaddtab"></a><a name="addtab"></a>CBaseTabbedPane::AddTab

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
[dovnitř, ven] Ukazatel na podokno, které chcete přidat. Tento ukazatel může být neplatný po volání této metody. Další informace naleznete v části Poznámky.

*b*<br/>
[v] TRUE, aby byla karta viditelná; jinak NEPRAVDA.

*bSetAktivní*<br/>
[v] TRUE, aby se karta aktivní kartu; jinak NEPRAVDA.

*bOdpojitelný*<br/>
[v] TRUE, aby byla karta odnímatelná; jinak NEPRAVDA.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud bylo podokno úspěšně přidáno jako karta a nebylo v procesu zničeno. FALSE, pokud je přidávaný `CBaseTabbedPane`panel objektem typu . Další informace naleznete v části Poznámky.

### <a name="remarks"></a>Poznámky

Voláním této metody přidáte podokno jako novou kartu v podokně s kartami. Pokud *pNewBar* odkazuje na `CBaseTabbedPane`objekt typu , všechny jeho karty jsou zkopírovány do podokna s kartami a *pak pNewBar* je zničen. Proto *pNewBar* se stane neplatný ukazatel a by neměl být používán.

## <a name="cbasetabbedpaneallowdestroyemptytabbedpane"></a><a name="allowdestroyemptytabbedpane"></a>CBaseTabbedPane::AllowDestroyEmptyTabbedPane

Určuje, zda lze zničit prázdné podokno s kartami.

```
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud lze zničit prázdné podokno s kartami; jinak NEPRAVDA. Výchozí implementace vždy vrátí hodnotu PRAVDA.

### <a name="remarks"></a>Poznámky

Pokud prázdné podokno s kartami není povoleno zničit, rozhraní framework místo toho skryje podokno.

## <a name="cbasetabbedpaneapplyrestoredtabinfo"></a><a name="applyrestoredtabinfo"></a>CBaseTabbedPane::ApplyRestoredTabInfo

Načte nastavení karty z registru a použije je na podokno s kartami.

```
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```

### <a name="parameters"></a>Parametry

*bUseTabIndexes*<br/>
[v] Tento parametr se používá interně rámci.

### <a name="remarks"></a>Poznámky

Tato metoda je volána rámci při opětovném načtení informací o stavu ukotvení z registru. Metoda získá informace o pořadí polí a názvy tabulátorů pro podokno s kartami.

## <a name="cbasetabbedpanecanfloat"></a><a name="canfloat"></a>CBaseTabbedPane::CanFloat

Určuje, zda se podokno s kartami může uvolnit.

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud se podokno může vznášet; jinak NEPRAVDA.

## <a name="cbasetabbedpanecansetcaptiontexttotabname"></a><a name="cansetcaptiontexttotabname"></a>CBaseTabbedPane::CanSetCaptionTextToTabName

Určuje, zda má titulek podokna s kartami zobrazovat stejný text jako aktivní karta.

```
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je text titulku podokna s kartami nastaven na text aktivní karty; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Metoda se používá k určení, zda text zobrazený na titulku podokna karet duplikuje popisek aktivní karty. Tuto funkci můžete povolit nebo zakázat voláním [CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname).

## <a name="cbasetabbedpaneconverttotabbeddocument"></a><a name="converttotabbeddocument"></a>CBaseTabbedPane::ConvertToTabbedDocument

Převede jedno nebo více ukotvených podoken na dokumenty s kartami MDI.

```
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```

### <a name="parameters"></a>Parametry

*bActiveTabOnly*<br/>
[v] Při převodu podokna s kartami zadejte hodnotu PRAVDA, chcete-li převést pouze aktivní kartu.

## <a name="cbasetabbedpanedetachpane"></a><a name="detachpane"></a>CBaseTabbedPane::DetachPane

Odpojí podokno od podokna s kartami.

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[v] Ukazatel na podokno odpojit.

*bSkrýt*<br/>
[v] Logický parametr, který určuje, zda rozhraní skryje podokno po odpojení.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud rozhraní úspěšně odpojí podokno; FALSE, pokud *pBar* je NULL nebo odkazuje na podokno, které není v podokně s kartami.

### <a name="remarks"></a>Poznámky

Rámec plovoucí odpojené podokno, pokud je to možné. Další informace naleznete v tématu [CBasePane::CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).

## <a name="cbasetabbedpaneenablesetcaptiontexttotabname"></a><a name="enablesetcaptiontexttotabname"></a>CBaseTabbedPane::EnableSetCaptionTextToTabName

Povolí nebo zakáže možnost podokna s kartami synchronizovat text titulků s textem popisku na aktivní kartě.

```
virtual void EnableSetCaptionTextToTabName(BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
[v] TRUE pro synchronizaci titulku podokna s kartami s aktivním titulkem karty; jinak NEPRAVDA.

## <a name="cbasetabbedpanefilldefaulttabsorderarray"></a><a name="filldefaulttabsorderarray"></a>CBaseTabbedPane::FillDefaultTabsOrderArray

Obnoví výchozí stav vnitřního pořadí polí.

```
void FillDefaultTabsOrderArray();
```

### <a name="remarks"></a>Poznámky

Tato metoda se nazývá, když rozhraní framework obnoví panel aplikace Outlook do počátečního stavu.

## <a name="cbasetabbedpanefindpanebyid"></a><a name="findpanebyid"></a>CBaseTabbedPane::FindPaneByID

Vrátí podokno identifikované ID podokna.

```
virtual CWnd* FindPaneByID(UINT uBarID);
```

### <a name="parameters"></a>Parametry

*uBarID*<br/>
[v] Určuje ID podokna, které má být vyhledání.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na podokno, pokud byl nalezen; jinak NULL.

### <a name="remarks"></a>Poznámky

Tato metoda porovná všechny karty v podokně a vrátí jeden s ID určené parametrem *uBarID.*

## <a name="cbasetabbedpanefindbarbytabnumber"></a><a name="findbarbytabnumber"></a>CBaseTabbedPane::FindBarByTabNumber

Vrátí podokno, které je umístěno na kartě.

```
virtual CWnd* FindBarByTabNumber(
    int nTabNum,
    BOOL bGetWrappedBar = FALSE);
```

### <a name="parameters"></a>Parametry

*nTabNum*<br/>
[v] Určuje nulový index karty, který má být načten.

*bGetWrappedBar*<br/>
[v] TRUE vrátíte podkladové (zabalené) okno podokna namísto samotného podokna; jinak FALSE. To platí pouze pro podokna odvozená z [CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md).

### <a name="return-value"></a>Návratová hodnota

Pokud je podokno nalezeno, je vrácen platný ukazatel na hledané podokno. jinak NULL.

### <a name="remarks"></a>Poznámky

Volání této metody načíst podokno s bydlištěm na kartě určené *parametrem nTabNum.*

## <a name="cbasetabbedpanefloattab"></a><a name="floattab"></a>CBaseTabbedPane::FloatTab

Plovoucí podokno, ale pouze v případě, že podokno aktuálně umístěnna na odpojitelné kartu.

```
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[dovnitř, ven] Ukazatel na podokno float.

*nTabID*<br/>
[v] Určuje nulový index karty, která má být plovoucí.

*dockMethod*<br/>
[v] Určuje metodu, která má být používána k nastavení plovoucího panelu. Další informace naleznete v části Poznámky.

*bSkrýt*<br/>
[v] TRUE skrýt podokno před plovoucí; jinak NEPRAVDA.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud se podokno vznášelo; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Volání této metody float podokno, které je aktuálně umístěnna oddělitelné kartu.

Pokud chcete odpojit podokno programově, zadejte DM_SHOW *parametrdockMethod.* Pokud chcete plovoucí podokno ve stejné poloze, kde se dříve plovoucí, zadejte DM_DBL_CLICK jako *dockMethod* parametr.

## <a name="cbasetabbedpanegetdefaulttabsorder"></a><a name="getdefaulttabsorder"></a>CBaseTabbedPane::GetDefaultTabsOrder

Vrátí výchozí pořadí karet v podokně.

```
const CArray<int,int>& GetDefaultTabsOrder();
```

### <a name="return-value"></a>Návratová hodnota

Objekt, `CArray` který určuje výchozí pořadí karet v podokně.

### <a name="remarks"></a>Poznámky

Rozhraní Framework volá tuto metodu při obnovení panelu aplikace Outlook do počátečního stavu.

## <a name="cbasetabbedpanegetfirstvisibletab"></a><a name="getfirstvisibletab"></a>CBaseTabbedPane::GetFirstVisibleTab

Načte ukazatel na první zobrazenou kartu.

```
virtual CWnd* GetFirstVisibleTab(int& iTabNum);
```

### <a name="parameters"></a>Parametry

*iTabNum*<br/>
[v] Odkaz na celé číslo. Tato metoda zapíše index na základě nuly první zobrazené karty na tento parametr nebo -1, pokud není nalezena žádná zobrazená karta.

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu ukazatel na první zobrazenou kartu; jinak NULL.

## <a name="cbasetabbedpanegetminsize"></a><a name="getminsize"></a>CBaseTabbedPane::GetMinSize

Načte minimální povolenou velikost podokna.

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
[out] Objekt, `CSize` který je vyplněn minimální povolenou velikostí.

### <a name="remarks"></a>Poznámky

Pokud je aktivní konzistentní zpracování minimálních velikostí podokna [(CPane::m_bHandleMinSize),](../../mfc/reference/cpane-class.md#m_bhandleminsize) *je velikost* vyplněna minimální povolenou velikostí pro aktivní kartu. V opačném případě je *velikost* vyplněna vrácenou hodnotou [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).

## <a name="cbasetabbedpanegetpaneicon"></a><a name="getpaneicon"></a>CBaseTabbedPane::GetPaneIcon

Načte minimální povolenou velikost podokna.

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>Parametry

*Velikost*<br/>
[out] Objekt, `CSize` který je vyplněn minimální povolenou velikostí.

### <a name="remarks"></a>Poznámky

Pokud je aktivní konzistentní zpracování minimálních velikostí podokna [(CPane::m_bHandleMinSize),](../../mfc/reference/cpane-class.md#m_bhandleminsize) *je velikost* vyplněna minimální povolenou velikostí pro aktivní kartu. V opačném případě je *velikost* vyplněna vrácenou hodnotou [CPane::GetMinSize](../../mfc/reference/cpane-class.md#getminsize).

## <a name="cbasetabbedpanegetpanelist"></a><a name="getpanelist"></a>CBaseTabbedPane::GetPaneList

Vrátí seznam podoken, které jsou obsaženy v podokně s kartami.

```
virtual void GetPaneList(
    CObList& lst,
    CRuntimeClass* pRTCFilter = NULL);
```

### <a name="parameters"></a>Parametry

*Lst*<br/>
[out] A, `CObList` která je vyplněna podokny, které jsou obsaženy v podokně s kartami.

*pRTCFiltr*<br/>
[v] Pokud není null, vrácený seznam obsahuje pouze podokna, které jsou zadané runtime třídy.

## <a name="cbasetabbedpanegettabarea"></a><a name="gettabarea"></a>CBaseTabbedPane::GetTabArea

Vrátí ohraničovací obdélníky pro horní a dolní oblast tabulátoru.

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const = 0;
```

### <a name="parameters"></a>Parametry

*rectTabAreaTop*<br/>
[out] Přijme souřadnice obrazovky v oblasti horní karty.

*rectTabAreaBottom*<br/>
[out] Přijme souřadnice obrazovky v oblasti dolní tabulátoru.

### <a name="remarks"></a>Poznámky

Volání této metody k určení ohraničující obdélníky, v souřadnicích obrazovky, pro horní a dolní tabulátor oblasti.

## <a name="cbasetabbedpanegettabsnum"></a><a name="gettabsnum"></a>CBaseTabbedPane::GetTabsNum

Vrátí počet karet v okně karty.

```
virtual int GetTabsNum() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet karet v podokně s kartami.

## <a name="cbasetabbedpanegetunderlyingwindow"></a><a name="getunderlyingwindow"></a>CBaseTabbedPane::GetUnderlyingWindow

Získá základní (zabalené) okno karty.

```
virtual CMFCBaseTabCtrl* GetUnderlyingWindow();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na základní okno karty.

## <a name="cbasetabbedpanegetvisibletabsnum"></a><a name="getvisibletabsnum"></a>CBaseTabbedPane::GetVisibleTabsNum

Vrátí počet viditelných karet.

```
virtual int GetVisibleTabsNum() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet viditelných karet, které budou větší nebo rovny nule.

### <a name="remarks"></a>Poznámky

Volánítéto metody k určení počtu viditelných karet v podokně s kartami.

## <a name="cbasetabbedpanehasautohidemode"></a><a name="hasautohidemode"></a>CBaseTabbedPane::HasAutoHideMode

Určuje, zda lze podokno s kartami přepnout do režimu automatického skrytí.

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud lze podokno přepnout do režimu automatického skrytí; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Pokud je režim automatického skrytí zakázán, na titulku podokna s kartami se nezobrazí žádné tlačítko pin.

## <a name="cbasetabbedpaneishidesingletab"></a><a name="ishidesingletab"></a>CBaseTabbedPane::IsHideSingleTab

Určuje, zda je podokno s kartami skryté, pokud se zobrazí pouze jedna karta.

```
virtual BOOL IsHideSingleTab() const;
```

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud se okno karty nezobrazuje, pokud je k dispozici pouze jedna viditelná karta; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Pokud se podokno nezobrazí, protože je otevřena pouze jedna karta, můžete tuto metodu volat a určit, zda podokno s kartami funguje správně.

## <a name="cbasetabbedpaneremovepane"></a><a name="removepane"></a>CBaseTabbedPane::RemovePane

Odebere podokno z podokna s kartami.

```
virtual BOOL RemovePane(CWnd* pBar);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[dovnitř, ven] Ukazatel na podokno odebrat z podokna s kartami.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud bylo podokno úspěšně odebráno z podokna s kartami a pokud je podokno s kartami stále platné. False, pokud bylo poslední podokno odebráno z podokna s kartami a podokno s kartami bude zničeno. Pokud je vrácená hodnota FALSE, nepoužívejte podokno s kartami.

### <a name="remarks"></a>Poznámky

Voláním této metody odeberte podokno určené parametrem *pBar* z podokna s kartami.

## <a name="cbasetabbedpanesetautodestroy"></a><a name="setautodestroy"></a>CBaseTabbedPane::SetAutoDestroy

Určuje, zda bude ovládací panel s kartami automaticky zničen.

```
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*bAutoDestroy*<br/>
[v] PRAVDA, pokud bylo podokno s kartami vytvořeno dynamicky a neřídíte jeho životnost; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Pokud podokno s kartami vytváříte dynamicky a neřídíte jeho životnost, nastavte režim automatického zničení na hodnotu TRUE. Pokud je režim automatického zničení true, podokno s kartami bude automaticky zničeno rámcem.

## <a name="cbasetabbedpaneshowtab"></a><a name="showtab"></a>CBaseTabbedPane::Zobrazit záložku

Zobrazí nebo skryje kartu.

```
virtual BOOL ShowTab(
    CWnd* pBar,
    BOOL bShow,
    BOOL bDelay,
    BOOL bActivate);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[v] Ukazatel na podokno, který chcete zobrazit nebo skrýt.

*bZobrazit*<br/>
[v] TRUE pro zobrazení podokna; Nepravda, chcete-li podokno skrýt.

*bZpoždění*<br/>
[v] TRUE zpoždění úpravy rozložení karty; jinak NEPRAVDA.

*bAktivovat*<br/>
[v] TRUE, aby se karta aktivní kartu; jinak NEPRAVDA.

### <a name="return-value"></a>Návratová hodnota

PRAVDA, pokud byla karta zobrazena nebo úspěšně skryta; jinak NEPRAVDA.

### <a name="remarks"></a>Poznámky

Při volání této metody je podokno zobrazeno nebo skryto v závislosti na hodnotě parametru *bShow.* Pokud kartu skryjete a je to poslední viditelná karta v základním okně karty, podokno s kartami je skryté. Pokud kartu zobrazíte, když dříve nebyly zobrazeny žádné karty, zobrazí se podokno s kartami.

## <a name="cbasetabbedpanerecalclayout"></a><a name="recalclayout"></a>CBaseTabbedPane::RecalcLayout

Přepočítá informace o rozložení podokna.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Poznámky

Pokud je podokno plovoucí, tato metoda upozorní rozhraní pro změny velikosti podokna na aktuální velikost minirámce.

Pokud je podokno ukotveno, tato metoda neprovede žádnou akci.

## <a name="cbasetabbedpanesetautohidemode"></a><a name="setautohidemode"></a>CBaseTabbedPane::SetAutoHideMode

Nastaví režim automatického skrytí pro odnímatelná podokna v podokně s kartami.

```
virtual CMFCAutoHideToolBar* SetAutoHideMode(
    BOOL bMode,
    DWORD dwAlignment,
    CMFCAutoHideToolBar* pCurrAutoHideBar = NULL,
    BOOL bUseTimer = TRUE);
```

### <a name="parameters"></a>Parametry

*bRežim*<br/>
[v] TRUE pro povolení režimu automatického skrytí; NEPRAVDA pro povolení pravidelného dokovacího režimu.

*dwAlignment*<br/>
[v] Určuje zarovnání podokna automatického skrytí, které má být vytvořeno. Seznam možných hodnot naleznete v [tématu CPane::MoveByAlignment](../../mfc/reference/cpane-class.md#movebyalignment).

*pCurrAutoHideBar*<br/>
[dovnitř, ven] Ukazatel na aktuální panel nástrojů automatického skrytí. Může být NULL.

*bPoužitíČasovač*<br/>
[v] Určuje, zda se má použít efekt automatického skrytí, když uživatel přepne podokno do režimu automatického skrytí, nebo zda má být podokno okamžitě skryto.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na automaticky skrýt panel nástrojů, který je vytvořen při přepnutí do režimu automatického skrytí nebo null, pokud není vytvořen žádný panel nástrojů.

### <a name="remarks"></a>Poznámky

Rozhraní Framework volá tuto metodu, když uživatel zvolí tlačítko pin přepnout podokno s kartami do režimu automatického skrytí nebo do normálního dokovacího režimu.

Režim automatického skrytí je nastaven pro každé oddělitelné podokno v podokně s kartami. Podokna, která nelze oddělit, jsou ignorována. Další informace naleznete v tématu [CMFCBaseTabCtrl::EnableTabDetach](../../mfc/reference/cmfcbasetabctrl-class.md#enabletabdetach).

Volání této metody přepnout podokno s kartami do režimu automatického skrytí programově. Podokno musí být ukotveno do okna hlavního rámce ( [CDockablePane::GetDefaultPaneDivider](../../mfc/reference/cdockablepane-class.md#getdefaultpanedivider) musí vrátit platný ukazatel [cPanedivider).](../../mfc/reference/cpanedivider-class.md)

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[Třída CDockablePane](../../mfc/reference/cdockablepane-class.md)
