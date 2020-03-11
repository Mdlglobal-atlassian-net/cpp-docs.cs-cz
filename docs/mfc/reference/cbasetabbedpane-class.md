---
title: CBaseTabbedPane – třída
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
ms.openlocfilehash: d7ffaa7274a8ed12944cdbc5dcbbdcb8fd3fd2b9
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78883647"
---
# <a name="cbasetabbedpane-class"></a>CBaseTabbedPane – třída

Rozšiřuje funkčnost [třídy CDockablePane](../../mfc/reference/cdockablepane-class.md) tak, aby podporovala vytváření oken s kartami.

## <a name="syntax"></a>Syntaxe

```
class CBaseTabbedPane : public CDockablePane
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|`CBaseTabbedPane::CBaseTabbedPane`|Výchozí konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CBaseTabbedPane::AddTab](#addtab)|Přidá novou kartu do podokna s kartami.|
|[CBaseTabbedPane::AllowDestroyEmptyTabbedPane](#allowdestroyemptytabbedpane)|Určuje, zda může být zničeno prázdné podokno s kartami.|
|[CBaseTabbedPane::ApplyRestoredTabInfo](#applyrestoredtabinfo)|Použije nastavení karty, které se načte z registru, do podokna s kartami.|
|[CBaseTabbedPane::CanFloat](#canfloat)|Určuje, zda může být podokno plovoucí. (Overrides [CBasePane:: CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).)|
|[CBaseTabbedPane::CanSetCaptionTextToTabName](#cansetcaptiontexttotabname)|Určuje, zda se má v záhlaví okna s kartami zobrazit stejný text jako aktivní karta.|
|[CBaseTabbedPane::ConvertToTabbedDocument](#converttotabbeddocument)|(Overrides [CDockablePane:: ConvertToTabbedDocument](../../mfc/reference/cdockablepane-class.md#converttotabbeddocument).)|
|[CBaseTabbedPane::D etachPane](#detachpane)|Převede jedno nebo více podoken ukotvit na dokumenty s kartami MDI.|
|[CBaseTabbedPane::EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname)|Povolí nebo zakáže schopnost podokna s kartami synchronizovat text titulku s textem popisku na aktivní kartě.|
|[CBaseTabbedPane::FillDefaultTabsOrderArray](#filldefaulttabsorderarray)|Obnoví interní pořadí karet do výchozího stavu.|
|[CBaseTabbedPane::FindBarByTabNumber](#findbarbytabnumber)|Vrátí podokno, které je umístěno na kartě, když je karta identifikována indexem karet založenými na nule.|
|||
|[CBaseTabbedPane::FindPaneByID](#findpanebyid)|Vrátí podokno identifikované ID podokna.|
|[CBaseTabbedPane::FloatTab](#floattab)|Oddělí podokno, ale pouze v případě, že se podokno aktuálně nachází na odpojené kartě.|
|[CBaseTabbedPane::GetDefaultTabsOrder](#getdefaulttabsorder)|Vrátí výchozí pořadí karet v podokně.|
|[CBaseTabbedPane::GetFirstVisibleTab](#getfirstvisibletab)|Načte ukazatel na první zobrazenou kartu.|
|[CBaseTabbedPane:: getminsize](#getminsize)|Načte minimální povolenou velikost podokna. (Overrides [CPane:: getminsize](../../mfc/reference/cpane-class.md#getminsize).)|
|[CBaseTabbedPane::GetPaneIcon](#getpaneicon)|Vrátí popisovač ikony podokna. (Overrides [CBasePane:: GetPaneIcon](../../mfc/reference/cbasepane-class.md#getpaneicon).)|
|[CBaseTabbedPane:: getPanel](#getpanelist)|Vrátí seznam podoken, která jsou obsažena v podokně s kartami.|
|[CBaseTabbedPane::GetTabArea](#gettabarea)|Vrátí ohraničující obdélníky pro oblasti horních a dolních karet.|
|[CBaseTabbedPane::GetTabsNum](#gettabsnum)|Vrátí počet karet v okně karet.|
|[CBaseTabbedPane::GetUnderlyingWindow](#getunderlyingwindow)|Získá základní (zabalenou) kartu okna.|
|[CBaseTabbedPane::GetVisibleTabsNum](#getvisibletabsnum)|Vrátí počet zobrazených karet.|
|[CBaseTabbedPane::HasAutoHideMode](#hasautohidemode)|Určuje, zda může být podokno s kartami přepnuto do režimu automatického skrývání.|
|[CBaseTabbedPane::IsHideSingleTab](#ishidesingletab)|Určuje, zda je podokno s kartami skryto, pokud je zobrazena pouze jedna karta.|
|`CBaseTabbedPane::LoadSiblingPaneIDs`|Používá se interně během serializace.|
|[CBaseTabbedPane::RecalcLayout](#recalclayout)|Přepočítá informace o rozložení podokna. (Overrides [CPane:: RecalcLayout](../../mfc/reference/cpane-class.md#recalclayout).)|
|[CBaseTabbedPane::RemovePane](#removepane)|Odebere podokno z podokna s kartami.|
|`CBaseTabbedPane::SaveSiblingBarIDs`|Používá se interně během serializace.|
|`CBaseTabbedPane::Serialize`|(Overrides [CDockablePane:: serializovat](cdockablepane-class.md).)|
|`CBaseTabbedPane::SerializeTabWindow`|Používá se interně během serializace.|
|[CBaseTabbedPane::SetAutoDestroy](#setautodestroy)|Určuje, zda bude automaticky zničen ovládací panel s kartami.|
|[CBaseTabbedPane::SetAutoHideMode](#setautohidemode)|Přepne ukotvené podokno mezi zobrazeným a automatickým skrytím režimu. (Overrides [CDockablePane:: SetAutoHideMode](../../mfc/reference/cdockablepane-class.md#setautohidemode).)|
|[CBaseTabbedPane:: ShowTab](#showtab)|Zobrazí nebo skryje kartu.|

## <a name="remarks"></a>Poznámky

Tato třída je abstraktní třídou a nelze na ni vytvořit instanci. Implementuje služby, které jsou společné pro všechny druhy podoken s kartami.

V současné době knihovna obsahuje dvě odvozené třídy podokna s kartami: třídy [CTabbedPane](../../mfc/reference/ctabbedpane-class.md) a [třídy CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md).

Objekt `CBaseTabbedPane` obtéká ukazatel na objekt [třídy CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md) . [Třída CMFCBaseTabCtrl](../../mfc/reference/cmfcbasetabctrl-class.md) se pak stala podřízeným oknem podokna s kartami.

Další informace o vytváření podoken s kartami naleznete v tématu [Třída CDockablePane](../../mfc/reference/cdockablepane-class.md), třída [CTabbedPane](../../mfc/reference/ctabbedpane-class.md)a [Třída CMFCOutlookBar](../../mfc/reference/cmfcoutlookbar-class.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

[CWnd](../../mfc/reference/cwnd-class.md)

[CBasePane](../../mfc/reference/cbasepane-class.md)

[CPane](../../mfc/reference/cpane-class.md)

[CDockablePane](../../mfc/reference/cdockablepane-class.md)

`CBaseTabbedPane`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxBaseTabbedPane. h

##  <a name="addtab"></a>CBaseTabbedPane::AddTab

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
[in, out] Ukazatel na podokno, které se má přidat Po volání této metody může být tento ukazatel neplatný. Další informace najdete v části poznámky.

*bVisible*<br/>
pro TRUE, pokud chcete, aby byla karta viditelná; v opačném případě FALSE.

*bSetActive*<br/>
pro TRUE pro nastavení karty jako aktivní; v opačném případě FALSE.

*bDetachable*<br/>
pro TRUE, pokud chcete, aby se karta odpojila; v opačném případě FALSE.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud se podokno úspěšně přidalo jako karta a v procesu se nezničilo. FALSE, pokud je přidávané podokno objekt typu `CBaseTabbedPane`. Další informace najdete v části poznámky.

### <a name="remarks"></a>Poznámky

Voláním této metody přidáte podokno jako novou kartu v podokně s kartami. Pokud *pNewBar* odkazuje na objekt typu `CBaseTabbedPane`, všechny jeho karty se zkopírují do podokna s kartami a pak se *pNewBar* zničí. Proto se *pNewBar* stal neplatným ukazatelem a neměl by se používat.

##  <a name="allowdestroyemptytabbedpane"></a>CBaseTabbedPane::AllowDestroyEmptyTabbedPane

Určuje, zda může být zničeno prázdné podokno s kartami.

```
virtual BOOL AllowDestroyEmptyTabbedPane() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud může být zničeno prázdné podokno s kartami; v opačném případě FALSE. Výchozí implementace vždy vrátí hodnotu TRUE.

### <a name="remarks"></a>Poznámky

Pokud není povoleno zničení prázdného podokna s kartami, rozhraní místo toho skryje podokno.

##  <a name="applyrestoredtabinfo"></a>CBaseTabbedPane::ApplyRestoredTabInfo

Načte nastavení karty z registru a použije je pro podokno s kartami.

```
virtual void ApplyRestoredTabInfo(BOOL bUseTabIndexes = FALSE);
```

### <a name="parameters"></a>Parametry

*bUseTabIndexes*<br/>
pro Tento parametr je používán interně rozhraním.

### <a name="remarks"></a>Poznámky

Tato metoda je volána rozhraním při opětovném načtení informací o stavu ukotvení z registru. Metoda získá informace o pořadí karet a názvech karet pro podokno s kartami.

##  <a name="canfloat"></a>CBaseTabbedPane::CanFloat

Určuje, zda může být podokno s kartami plovoucí.

```
virtual BOOL CanFloat() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud se může podokno uvolnit; v opačném případě FALSE.

##  <a name="cansetcaptiontexttotabname"></a>CBaseTabbedPane::CanSetCaptionTextToTabName

Určuje, zda se má v záhlaví okna s kartami zobrazit stejný text jako aktivní karta.

```
virtual BOOL CanSetCaptionTextToTabName() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je text titulku podokna s kartami nastavený na text aktivní karty; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Metoda se používá k určení, zda text zobrazený v záhlaví podokna s kartami duplikuje popisek aktivní karty. Tuto funkci můžete povolit nebo zakázat voláním [CBaseTabbedPane:: EnableSetCaptionTextToTabName](#enablesetcaptiontexttotabname).

##  <a name="converttotabbeddocument"></a>CBaseTabbedPane::ConvertToTabbedDocument

Převede jedno nebo více podoken ukotvit na dokumenty s kartami MDI.

```
virtual void ConvertToTabbedDocument(BOOL bActiveTabOnly = TRUE);
```

### <a name="parameters"></a>Parametry

*bActiveTabOnly*<br/>
pro Pokud převedete podokno s kartami, zadejte hodnotu TRUE pro převod pouze aktivní karty. Zadejte hodnotu FALSE pro převod všech karet v podokně.

##  <a name="detachpane"></a>CBaseTabbedPane::D etachPane

Odpojí podokno od podokna s kartami.

```
virtual BOOL DetachPane(
    CWnd* pBar,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
pro Ukazatel na podokno, které se má odpojit.

*bHide*<br/>
pro Parametr Boolean, který určuje, zda rozhraní skrývá podokno po jeho odpojení.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud rozhraní úspěšně odpojí podokno; FALSE, pokud má *pBar* hodnotu null nebo odkazuje na podokno, které není v podokně s kartami.

### <a name="remarks"></a>Poznámky

Pokud je to možné, rozhraní plovoucí odpojí. Další informace najdete v tématu [CBasePane:: CanFloat](../../mfc/reference/cbasepane-class.md#canfloat).

##  <a name="enablesetcaptiontexttotabname"></a>CBaseTabbedPane::EnableSetCaptionTextToTabName

Povolí nebo zakáže schopnost podokna s kartami synchronizovat text titulku s textem popisku na aktivní kartě.

```
virtual void EnableSetCaptionTextToTabName(BOOL bEnable);
```

### <a name="parameters"></a>Parametry

*bEnable*<br/>
pro TRUE pro synchronizaci titulků podokna s kartami s popiskem aktivní karty; v opačném případě FALSE.

##  <a name="filldefaulttabsorderarray"></a>CBaseTabbedPane::FillDefaultTabsOrderArray

Obnoví interní pořadí karet do výchozího stavu.

```
void FillDefaultTabsOrderArray();
```

### <a name="remarks"></a>Poznámky

Tato metoda je volána, když rozhraní obnoví panel aplikace Outlook do počátečního stavu.

##  <a name="findpanebyid"></a>CBaseTabbedPane::FindPaneByID

Vrátí podokno identifikované ID podokna.

```
virtual CWnd* FindPaneByID(UINT uBarID);
```

### <a name="parameters"></a>Parametry

*uBarID*<br/>
pro Určuje ID podokna, které se má najít.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na podokno, pokud byl nalezen; v opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

Tato metoda porovnává všechny karty v podokně a vrátí hodnotu s ID zadanou parametrem *uBarID* .

##  <a name="findbarbytabnumber"></a>CBaseTabbedPane::FindBarByTabNumber

Vrátí podokno, které se nachází na kartě.

```
virtual CWnd* FindBarByTabNumber(
    int nTabNum,
    BOOL bGetWrappedBar = FALSE);
```

### <a name="parameters"></a>Parametry

*nTabNum*<br/>
pro Určuje index založený na nule karty, který se má načíst.

*bGetWrappedBar*<br/>
pro TRUE pro návrat základního (zabaleného) okna podokna místo samotného podokna; v opačném případě FALSE. To platí pouze pro podokna odvozená z [CDockablePaneAdapter](../../mfc/reference/cdockablepaneadapter-class.md).

### <a name="return-value"></a>Návratová hodnota

Pokud je podokno nalezeno, je vrácen platný ukazatel na prohledávané podokno; v opačném případě hodnota NULL.

### <a name="remarks"></a>Poznámky

Voláním této metody načtete podokno, které je umístěno na kartě určené parametrem *nTabNum* .

##  <a name="floattab"></a>CBaseTabbedPane::FloatTab

Oddělí podokno, ale pouze v případě, že se podokno aktuálně nachází na odpojené kartě.

```
virtual BOOL FloatTab(
    CWnd* pBar,
    int nTabID,
    AFX_DOCK_METHOD dockMethod,
    BOOL bHide = FALSE);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[in, out] Ukazatel na plovoucí podokno.

*nTabID*<br/>
pro Určuje index založený na nule pro plovoucí kartu.

*dockMethod*<br/>
pro Určuje metodu, která se má použít k vytvoření plovoucího panelu. Další informace najdete v části poznámky.

*bHide*<br/>
pro TRUE pro skrytí podokna před plovoucí; v opačném případě FALSE.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud je podokno plovoucí; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Voláním této metody naplovákete podokno, které se aktuálně nachází na odpojené kartě.

Chcete-li odpojit podokno programově, zadejte DM_SHOW pro parametr *dockMethod* . Chcete-li uvolnit podokno na stejném místě, kde bylo dříve plovoucí, zadejte DM_DBL_CLICK jako parametr *dockMethod* .

##  <a name="getdefaulttabsorder"></a>CBaseTabbedPane::GetDefaultTabsOrder

Vrátí výchozí pořadí karet v podokně.

```
const CArray<int,int>& GetDefaultTabsOrder();
```

### <a name="return-value"></a>Návratová hodnota

Objekt `CArray`, který určuje výchozí pořadí karet v podokně.

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto metodu, když je panel aplikace Outlook obnoven do počátečního stavu.

##  <a name="getfirstvisibletab"></a>CBaseTabbedPane::GetFirstVisibleTab

Načte ukazatel na první zobrazenou kartu.

```
virtual CWnd* GetFirstVisibleTab(int& iTabNum);
```

### <a name="parameters"></a>Parametry

*iTabNum*<br/>
pro Odkaz na celé číslo. Tato metoda zapisuje index založený na nule první zobrazené karty na tento parametr, nebo-1, pokud nebyla nalezena žádná zobrazená karta.

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, ukazatel na první zobrazenou kartu; v opačném případě hodnota NULL.

##  <a name="getminsize"></a>CBaseTabbedPane:: getminsize

Načte minimální povolenou velikost podokna.

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>Parametry

*hodnota*<br/>
mimo Objekt `CSize`, který je vyplněn minimální povolenou velikostí.

### <a name="remarks"></a>Poznámky

Je-li konzistentní zpracování minimální velikosti podokna aktivní ( [CPane:: m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)), je *Velikost* vyplněna minimální povolenou velikostí pro aktivní kartu. v opačném případě je *Velikost* vyplněna návratovou hodnotou [CPane:: getminsize](../../mfc/reference/cpane-class.md#getminsize).

##  <a name="getpaneicon"></a>CBaseTabbedPane::GetPaneIcon

Načte minimální povolenou velikost podokna.

```
virtual void GetMinSize(CSize& size) const;
```

### <a name="parameters"></a>Parametry

*hodnota*<br/>
mimo Objekt `CSize`, který je vyplněn minimální povolenou velikostí.

### <a name="remarks"></a>Poznámky

Je-li konzistentní zpracování minimální velikosti podokna aktivní ( [CPane:: m_bHandleMinSize](../../mfc/reference/cpane-class.md#m_bhandleminsize)), je *Velikost* vyplněna minimální povolenou velikostí pro aktivní kartu. v opačném případě je *Velikost* vyplněna návratovou hodnotou [CPane:: getminsize](../../mfc/reference/cpane-class.md#getminsize).

##  <a name="getpanelist"></a>CBaseTabbedPane:: getPanel

Vrátí seznam podoken, která jsou obsažena v podokně s kartami.

```
virtual void GetPaneList(
    CObList& lst,
    CRuntimeClass* pRTCFilter = NULL);
```

### <a name="parameters"></a>Parametry

*lst*<br/>
mimo `CObList`, která je vyplněna podokny, která jsou obsažena v podokně s kartami.

*pRTCFilter*<br/>
pro Pokud hodnota není NULL, vrácený seznam obsahuje pouze podokna, která jsou zadaného běhové třídy.

##  <a name="gettabarea"></a>CBaseTabbedPane::GetTabArea

Vrátí ohraničující obdélníky pro oblasti horních a dolních karet.

```
virtual void GetTabArea(
    CRect& rectTabAreaTop,
    CRect& rectTabAreaBottom) const = 0;
```

### <a name="parameters"></a>Parametry

*rectTabAreaTop*<br/>
mimo Přijme souřadnice obrazovky horní oblasti karet.

*rectTabAreaBottom*<br/>
mimo Přijme souřadnice obrazovky spodní oblasti karty.

### <a name="remarks"></a>Poznámky

Voláním této metody určíte ohraničující obdélníky v souřadnicích obrazovky pro oblasti horních a dolních karet.

##  <a name="gettabsnum"></a>CBaseTabbedPane::GetTabsNum

Vrátí počet karet v okně karet.

```
virtual int GetTabsNum() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet karet v podokně s kartami

##  <a name="getunderlyingwindow"></a>CBaseTabbedPane::GetUnderlyingWindow

Získá základní (zabalenou) kartu okna.

```
virtual CMFCBaseTabCtrl* GetUnderlyingWindow();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na podkladové okno karty.

##  <a name="getvisibletabsnum"></a>CBaseTabbedPane::GetVisibleTabsNum

Vrátí počet viditelných karet.

```
virtual int GetVisibleTabsNum() const;
```

### <a name="return-value"></a>Návratová hodnota

Počet viditelných karet, které budou větší nebo rovny nule.

### <a name="remarks"></a>Poznámky

Voláním této metody určíte počet zobrazených karet v podokně s kartami.

##  <a name="hasautohidemode"></a>CBaseTabbedPane::HasAutoHideMode

Určuje, zda může být podokno s kartami přepnuto do režimu automatické skrývání.

```
virtual BOOL HasAutoHideMode() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud může být podokno přepnuto do režimu skrývání; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Pokud je režim automatické skrývání zakázaný, v nadpisu podokna s kartami se nezobrazí žádné tlačítko PIN.

##  <a name="ishidesingletab"></a>CBaseTabbedPane::IsHideSingleTab

Určuje, zda je podokno s kartami skryto, pokud je zobrazena pouze jedna karta.

```
virtual BOOL IsHideSingleTab() const;
```

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud se okno karty nezobrazuje, když je jenom jedna karta viditelná. v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Pokud se podokno nezobrazí, protože je otevřeno pouze jedna karta, můžete zavolat tuto metodu, abyste zjistili, zda podokno s kartami funguje správně.

##  <a name="removepane"></a>CBaseTabbedPane::RemovePane

Odebere podokno z podokna s kartami.

```
virtual BOOL RemovePane(CWnd* pBar);
```

### <a name="parameters"></a>Parametry

*pBar*<br/>
[in, out] Ukazatel na podokno, který se má odebrat z podokna s kartami

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud se podokno úspěšně odebralo z podokna s kartami a pokud je podokno s kartami stále platné. FALSE, pokud se poslední podokno odebralo z podokna s kartami a chystá se zničit podokno s kartami. Pokud je vrácená hodnota FALSE, nepoužívejte podokno s kartami.

### <a name="remarks"></a>Poznámky

Voláním této metody odeberete podokno určené parametrem *pBar* z podokna s kartami.

##  <a name="setautodestroy"></a>CBaseTabbedPane::SetAutoDestroy

Určuje, zda bude automaticky zničen ovládací panel s kartami.

```
void SetAutoDestroy(BOOL bAutoDestroy = TRUE);
```

### <a name="parameters"></a>Parametry

*bAutoDestroy*<br/>
pro TRUE, pokud bylo podokno s kartami vytvořeno dynamicky a neovládáte jeho životnost; v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Nastavte režim automatického zničení na hodnotu TRUE, pokud vytvoříte podokno s kartami dynamicky a Pokud neovládáte jeho životnost. Je-li režim automatického zničení nastaven na hodnotu TRUE, bude v rámci rozhraní automaticky zničeno podokno s kartami.

##  <a name="showtab"></a>CBaseTabbedPane:: ShowTab

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
pro Ukazatel na podokno, který se má zobrazit nebo skrýt.

*bShow*<br/>
pro TRUE pro zobrazení podokna; FALSE pro skrytí podokna.

*bDelay*<br/>
pro TRUE pro zpoždění úpravy rozložení karet; v opačném případě FALSE.

*bActivate*<br/>
pro TRUE pro nastavení karty jako aktivní; v opačném případě FALSE.

### <a name="return-value"></a>Návratová hodnota

TRUE, pokud se karta buď zobrazila, nebo byla skrytá. v opačném případě FALSE.

### <a name="remarks"></a>Poznámky

Při volání této metody je podokno buď zobrazeno, nebo skryto, v závislosti na hodnotě parametru *bShow* . Skryjete-li kartu a je to poslední zobrazená karta v podkladovém okně karet, podokno s kartami je skryto. Pokud se zobrazí karta, když se předtím nezobrazí žádné karty, zobrazí se podokno s kartami.

##  <a name="recalclayout"></a>CBaseTabbedPane::RecalcLayout

Přepočítá informace o rozložení podokna.

```
virtual void RecalcLayout();
```

### <a name="remarks"></a>Poznámky

Pokud je podokno plovoucí, tato metoda upozorní rozhraní, aby změnila velikost podokna na aktuální velikost zkráceného snímku.

Pokud je podokno ukotveno, tato metoda neprovede žádnou akci.

##  <a name="setautohidemode"></a>CBaseTabbedPane::SetAutoHideMode

Nastaví režim automatického skrývání pro odpojená podokna v podokně s kartami.

```
virtual CMFCAutoHideToolBar* SetAutoHideMode(
    BOOL bMode,
    DWORD dwAlignment,
    CMFCAutoHideToolBar* pCurrAutoHideBar = NULL,
    BOOL bUseTimer = TRUE);
```

### <a name="parameters"></a>Parametry

*bMode*<br/>
pro TRUE pro povolení režimu automatického skrývání; FALSE, pokud chcete povolit běžný režim uchycení.

*dwAlignment*<br/>
pro Určuje zarovnání podokna automatického skrývání, které má být vytvořeno. Seznam možných hodnot naleznete v tématu [CPane:: MoveByAlignment](../../mfc/reference/cpane-class.md#movebyalignment).

*pCurrAutoHideBar*<br/>
[in, out] Ukazatel na aktuální panel nástrojů pro automatické skrývání. Může mít hodnotu NULL.

*bUseTimer*<br/>
pro Určuje, zda se má použít efekt automatického skrývání, když uživatel přepne podokno do režimu automatického skrývání nebo skryje podokno hned.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na panel nástrojů pro automatické skrývání, který je vytvořen při přepnutí do režimu automatického skrývání, nebo hodnotu NULL, pokud není vytvořen žádný panel nástrojů.

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto metodu, když uživatel zvolí tlačítko pro zadání kódu PIN a přepne podokno s kartami na režim automatického skrývání nebo na normální režim uchycení.

Pro každé odpojitelné podokno v podokně s kartami je nastaven automatický režim skrývání. Podoken, která jsou neodpojená, se ignorují. Další informace najdete v tématu [CMFCBaseTabCtrl:: EnableTabDetach](../../mfc/reference/cmfcbasetabctrl-class.md#enabletabdetach).

Voláním této metody přepnete podokno s kartami na automatické skrývání režimu programově. Podokno musí být ukotveno v hlavním okně rámce ( [CDockablePane:: GetDefaultPaneDivider](../../mfc/reference/cdockablepane-class.md#getdefaultpanedivider) musí vrátit platný ukazatel na [CPaneDivider](../../mfc/reference/cpanedivider-class.md)).

## <a name="see-also"></a>Viz také

[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[Třídy](../../mfc/reference/mfc-classes.md)<br/>
[CDockablePane – třída](../../mfc/reference/cdockablepane-class.md)
