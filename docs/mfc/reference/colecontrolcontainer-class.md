---
title: COleControlContainer – třída
ms.date: 11/04/2016
f1_keywords:
- COleControlContainer
- AFXOCC/COleControlContainer
- AFXOCC/COleControlContainer::COleControlContainer
- AFXOCC/COleControlContainer::AttachControlSite
- AFXOCC/COleControlContainer::BroadcastAmbientPropertyChange
- AFXOCC/COleControlContainer::CheckDlgButton
- AFXOCC/COleControlContainer::CheckRadioButton
- AFXOCC/COleControlContainer::CreateControl
- AFXOCC/COleControlContainer::CreateOleFont
- AFXOCC/COleControlContainer::FindItem
- AFXOCC/COleControlContainer::FreezeAllEvents
- AFXOCC/COleControlContainer::GetAmbientProp
- AFXOCC/COleControlContainer::GetDlgItem
- AFXOCC/COleControlContainer::GetDlgItemInt
- AFXOCC/COleControlContainer::GetDlgItemText
- AFXOCC/COleControlContainer::HandleSetFocus
- AFXOCC/COleControlContainer::HandleWindowlessMessage
- AFXOCC/COleControlContainer::IsDlgButtonChecked
- AFXOCC/COleControlContainer::OnPaint
- AFXOCC/COleControlContainer::OnUIActivate
- AFXOCC/COleControlContainer::OnUIDeactivate
- AFXOCC/COleControlContainer::ScrollChildren
- AFXOCC/COleControlContainer::SendDlgItemMessage
- AFXOCC/COleControlContainer::SetDlgItemInt
- AFXOCC/COleControlContainer::SetDlgItemText
- AFXOCC/COleControlContainer::m_crBack
- AFXOCC/COleControlContainer::m_crFore
- AFXOCC/COleControlContainer::m_listSitesOrWnds
- AFXOCC/COleControlContainer::m_nWindowlessControls
- AFXOCC/COleControlContainer::m_pOleFont
- AFXOCC/COleControlContainer::m_pSiteCapture
- AFXOCC/COleControlContainer::m_pSiteFocus
- AFXOCC/COleControlContainer::m_pSiteUIActive
- AFXOCC/COleControlContainer::m_pWnd
- AFXOCC/COleControlContainer::m_siteMap
helpviewer_keywords:
- COleControlContainer [MFC], COleControlContainer
- COleControlContainer [MFC], AttachControlSite
- COleControlContainer [MFC], BroadcastAmbientPropertyChange
- COleControlContainer [MFC], CheckDlgButton
- COleControlContainer [MFC], CheckRadioButton
- COleControlContainer [MFC], CreateControl
- COleControlContainer [MFC], CreateOleFont
- COleControlContainer [MFC], FindItem
- COleControlContainer [MFC], FreezeAllEvents
- COleControlContainer [MFC], GetAmbientProp
- COleControlContainer [MFC], GetDlgItem
- COleControlContainer [MFC], GetDlgItemInt
- COleControlContainer [MFC], GetDlgItemText
- COleControlContainer [MFC], HandleSetFocus
- COleControlContainer [MFC], HandleWindowlessMessage
- COleControlContainer [MFC], IsDlgButtonChecked
- COleControlContainer [MFC], OnPaint
- COleControlContainer [MFC], OnUIActivate
- COleControlContainer [MFC], OnUIDeactivate
- COleControlContainer [MFC], ScrollChildren
- COleControlContainer [MFC], SendDlgItemMessage
- COleControlContainer [MFC], SetDlgItemInt
- COleControlContainer [MFC], SetDlgItemText
- COleControlContainer [MFC], m_crBack
- COleControlContainer [MFC], m_crFore
- COleControlContainer [MFC], m_listSitesOrWnds
- COleControlContainer [MFC], m_nWindowlessControls
- COleControlContainer [MFC], m_pOleFont
- COleControlContainer [MFC], m_pSiteCapture
- COleControlContainer [MFC], m_pSiteFocus
- COleControlContainer [MFC], m_pSiteUIActive
- COleControlContainer [MFC], m_pWnd
- COleControlContainer [MFC], m_siteMap
ms.assetid: f7ce9246-0fb7-4f07-a83a-6c2390d0fdf8
ms.openlocfilehash: 3aa2515b1731eafcb5e3bcfa22a56ebbc1cdfdfb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69504327"
---
# <a name="colecontrolcontainer-class"></a>COleControlContainer – třída

Slouží jako kontejner ovládacího prvku pro ovládací prvky ActiveX.

## <a name="syntax"></a>Syntaxe

```
class COleControlContainer : public CCmdTarget
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[COleControlContainer::COleControlContainer](#colecontrolcontainer)|`COleControlContainer` Vytvoří objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[COleControlContainer::AttachControlSite](#attachcontrolsite)|Vytvoří lokalitu ovládacího prvku, která je hostována kontejnerem.|
|[COleControlContainer::BroadcastAmbientPropertyChange](#broadcastambientpropertychange)|Informuje všechny hostované ovládací prvky, že se změnila vlastnost Ambient.|
|[COleControlContainer::CheckDlgButton](#checkdlgbutton)|Upraví určený ovládací prvek tlačítko.|
|[COleControlContainer::CheckRadioButton](#checkradiobutton)|Vybere zadaný přepínač pro skupinu.|
|[COleControlContainer::CreateControl](#createcontrol)|Vytvoří hostovaný ovládací prvek ActiveX.|
|[COleControlContainer::CreateOleFont](#createolefont)|Vytvoří písmo OLE.|
|[COleControlContainer::FindItem](#finditem)|Vrátí vlastní web určeného ovládacího prvku.|
|[COleControlContainer::FreezeAllEvents](#freezeallevents)|Určuje, zda server ovládacího prvku přijímá události.|
|[COleControlContainer::GetAmbientProp](#getambientprop)|Načte zadanou vlastnost Ambient.|
|[COleControlContainer::GetDlgItem](#getdlgitem)|Načte určený ovládací prvek dialogu.|
|[COleControlContainer::GetDlgItemInt](#getdlgitemint)|Načte hodnotu zadaného ovládacího prvku dialogu.|
|[COleControlContainer::GetDlgItemText](#getdlgitemtext)|Načte titulek zadaného ovládacího prvku dialogu.|
|[COleControlContainer::HandleSetFocus](#handlesetfocus)|Určuje, zda kontejner zpracovává zprávy WM_SETFOCUS.|
|[COleControlContainer::HandleWindowlessMessage](#handlewindowlessmessage)|Zpracovává zprávy odesílané ovládacímu prvku bez oken.|
|[COleControlContainer::IsDlgButtonChecked](#isdlgbuttonchecked)|Určuje stav zadaného tlačítka.|
|[COleControlContainer::OnPaint](#onpaint)|Volá se, aby se mohla překreslit část kontejneru.|
|[COleControlContainer::OnUIActivate](#onuiactivate)|Volá se v případě, že se bude aktivovat místní čas ovládacího prvku.|
|[COleControlContainer::OnUIDeactivate](#onuideactivate)|Volá se, když se chystá deaktivovat ovládací prvek.|
|[COleControlContainer::ScrollChildren](#scrollchildren)|Volá se rozhraním, když se z podřízeného okna přijímají zprávy Scroll.|
|[COleControlContainer::SendDlgItemMessage](#senddlgitemmessage)|Odešle zprávu na určený ovládací prvek.|
|[COleControlContainer::SetDlgItemInt](#setdlgitemint)|Nastaví hodnotu zadaného ovládacího prvku.|
|[COleControlContainer::SetDlgItemText](#setdlgitemtext)|Nastaví text zadaného ovládacího prvku.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[COleControlContainer::m_crBack](#m_crback)|Barva pozadí kontejneru.|
|[COleControlContainer::m_crFore](#m_crfore)|Barva popředí kontejneru.|
|[COleControlContainer::m_listSitesOrWnds](#m_listsitesorwnds)|Seznam podporovaných lokalit ovládacích prvků.|
|[COleControlContainer::m_nWindowlessControls](#m_nwindowlesscontrols)|Počet hostovaných ovládacích prvků bez oken.|
|[COleControlContainer::m_pOleFont](#m_polefont)|Ukazatel na písmo OLE na webu vlastního ovládacího prvku.|
|[COleControlContainer::m_pSiteCapture](#m_psitecapture)|Ukazatel na web ovládacího prvku Capture.|
|[COleControlContainer::m_pSiteFocus](#m_psitefocus)|Ukazatel na ovládací prvek, který aktuálně má fokus vstupu.|
|[COleControlContainer::m_pSiteUIActive](#m_psiteuiactive)|Ukazatel na ovládací prvek, který je aktuálně aktivovaný na místě.|
|[COleControlContainer::m_pWnd](#m_pwnd)|Ukazatel na okno implementující kontejner ovládacího prvku.|
|[COleControlContainer::m_siteMap](#m_sitemap)|Mapa webu.|

## <a name="remarks"></a>Poznámky

K tomu je potřeba poskytnout podporu pro jeden nebo víc webů ovládacího prvku ActiveX (implementující v `COleControlSite`). `COleControlContainer`plně implementuje rozhraní [IOleInPlaceFrame](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceframe) a [IOleContainer](/windows/win32/api/oleidl/nn-oleidl-iolecontainer) , aby obsahovaly ovládací prvky ActiveX, aby splnily svou kvalifikaci jako místní položky.

Tato třída se běžně používá ve spojení s `COccManager` a `COleControlSite` k implementaci vlastního kontejneru ovládacího prvku ActiveX s vlastními weby pro jeden nebo více ovládacích prvků ActiveX.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleControlContainer`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxocc. h

##  <a name="attachcontrolsite"></a>COleControlContainer::AttachControlSite

Volá se rozhraním, aby se vytvořila a připojila lokalita ovládacího prvku.

```
virtual void AttachControlSite(
    CWnd* pWnd,
    UINT nIDC = 0);

void AttachControlSite(
    CWnd* pWnd,
    UINT nIDC = 0);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazatel na `CWnd` objekt.

*nIDC*<br/>
ID ovládacího prvku, který se má připojit

### <a name="remarks"></a>Poznámky

Tuto funkci přepište, pokud chcete tento proces upravit.

> [!NOTE]
>  První forma této funkce použijte, pokud staticky propojujete knihovnu MFC. Pokud dynamicky propojujete knihovnu MFC, použijte druhý formulář.

##  <a name="broadcastambientpropertychange"></a>COleControlContainer::BroadcastAmbientPropertyChange

Informuje všechny hostované ovládací prvky, že se změnila vlastnost Ambient.

```
virtual void BroadcastAmbientPropertyChange(DISPID dispid);
```

### <a name="parameters"></a>Parametry

*dispid*<br/>
ID odeslání u změněné vlastnosti okolního prostředí.

### <a name="remarks"></a>Poznámky

Tato funkce je volána rozhraním, když má vlastnost Ambient Value změněné. Tuto funkci můžete přizpůsobit tak, aby se toto chování potlačilo.

##  <a name="checkdlgbutton"></a>COleControlContainer::CheckDlgButton

Upraví aktuální stav tlačítka.

```
virtual void CheckDlgButton(
    int nIDButton,
    UINT nCheck);
```

### <a name="parameters"></a>Parametry

*nIDButton*<br/>
ID tlačítka, které má být upraveno

*Npokuste*<br/>
Určuje stav tlačítka. Může být jedna z následujících akcí:

- BST_CHECKED nastaví stav tlačítka na zaškrtnuto.

- BST_INDETERMINATE nastaví stav tlačítka na šedivý, což značí neurčitý stav. Tuto hodnotu použijte pouze v případě, že tlačítko má styl BS_3STATE nebo BS_AUTO3STATE.

- BST_UNCHECKED nastaví stav tlačítka na nezaškrtnuto.

##  <a name="checkradiobutton"></a>COleControlContainer::CheckRadioButton

Vybere vybraný přepínač ve skupině a vymaže zbývající tlačítka ve skupině.

```
virtual void CheckRadioButton(
    int nIDFirstButton,
    int nIDLastButton,
    int nIDCheckButton);
```

### <a name="parameters"></a>Parametry

*nIDFirstButton*<br/>
Určuje identifikátor prvního přepínacího tlačítka ve skupině.

*nIDLastButton*<br/>
Určuje identifikátor posledního přepínacího tlačítka ve skupině.

*nIDCheckButton*<br/>
Určuje identifikátor přepínače, který se má zkontrolovat.

##  <a name="colecontrolcontainer"></a>COleControlContainer::COleControlContainer

`COleControlContainer` Vytvoří objekt.

```
explicit COleControlContainer(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazatel na nadřazené okno kontejneru ovládacího prvku.

### <a name="remarks"></a>Poznámky

Po úspěšném vytvoření objektu přidejte vlastní web ovládacího prvku s voláním `AttachControlSite`.

##  <a name="createcontrol"></a>COleControlContainer::CreateControl

Vytvoří ovládací prvek ActiveX, který je hostovaný zadaným `COleControlSite` objektem.

```
BOOL CreateControl(
    CWnd* pWndCtrl,
    REFCLSID clsid,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const RECT& rect,
    UINT nID,
    CFile* pPersist =NULL,
    BOOL bStorage =FALSE,
    BSTR bstrLicKey =NULL,
    COleControlSite** ppNewSite =NULL);

BOOL CreateControl(
    CWnd* pWndCtrl,
    REFCLSID clsid,
    LPCTSTR lpszWindowName,
    DWORD dwStyle,
    const POINT* ppt,
    const SIZE* psize,
    UINT nID,
    CFile* pPersist =NULL,
    BOOL bStorage =FALSE,
    BSTR bstrLicKey =NULL,
    COleControlSite** ppNewSite =NULL);
```

### <a name="parameters"></a>Parametry

*pWndCtrl*<br/>
Ukazatel na objekt okna reprezentující ovládací prvek.

*CLSID*<br/>
Jedinečné ID třídy ovládacího prvku

*lpszWindowName*<br/>
Ukazatel na text, který má být zobrazen v ovládacím prvku. Nastaví hodnotu vlastnosti Caption nebo text ovládacího prvku (pokud existuje). Pokud má hodnotu NULL, vlastnost Caption nebo text ovládacího prvku se nezmění.

*dwStyle*<br/>
Styly Windows. Dostupné styly jsou uvedeny v části **poznámky** .

*OBD*<br/>
Určuje velikost a polohu ovládacího prvku. Může to být buď `CRect` objekt, `RECT` nebo struktura.

*nID*<br/>
Určuje ID podřízeného okna ovládacího prvku.

*pPersist*<br/>
Ukazatel na `CFile` obsahující trvalý stav ovládacího prvku. Výchozí hodnota je NULL, což značí, že se ovládací prvek inicializuje sám bez obnovení jeho stavu z jakéhokoli trvalého úložiště. Pokud hodnota není null, mělo by se jednat o ukazatel `CFile`na objekt odvozený od ovládacího prvku, který obsahuje trvalá data ovládacího prvku, a to ve formě datového proudu nebo úložiště. Tato data mohla být uložena v předchozí aktivaci klienta. Může obsahovat další data, ale musí mít ukazatel pro čtení i zápis nastavený na první bajt trvalých dat v době `CreateControl`volání. `CFile`

*bStorage*<br/>
Určuje, zda mají být data v *pPersist* interpretována `IStorage` jako `IStream` data. Pokud jsou data v *pPersist* úložiště, *bStorage* by měla být true. Pokud jsou data v *pPersist* datový proud, *bStorage* by měl mít hodnotu false. Výchozí hodnota je FALSE (NEPRAVDA).

*bstrLicKey*<br/>
Volitelná data licenčního klíče. Tato data jsou potřebná jenom pro vytváření ovládacích prvků, které vyžadují licenční klíč za běhu. Pokud ovládací prvek podporuje licencování, je nutné zadat licenční klíč pro vytvoření ovládacího prvku, který má být úspěšný. Výchozí hodnota je NULL.

*ppNewSite*<br/>
Ukazatel na existující web ovládacího prvku, který bude hostitelem vytvářeného ovládacího prvku. Výchozí hodnota je NULL, což znamená, že se automaticky vytvoří nový řídicí web a připojí se k novému ovládacímu prvku.

*ppt*<br/>
Ukazatel na `POINT` strukturu, která obsahuje levý horní roh ovládacího prvku. Velikost ovládacího prvku je určena hodnotou *psize*. Hodnoty *PPT* a *psize* jsou volitelnou metodou určení velikosti a umístění ovládacího prvku.

*psize*<br/>
Ukazatel na `SIZE` strukturu, která obsahuje velikost ovládacího prvku. Levý horní roh je určen hodnotou *PPT*. Hodnoty *PPT* a *psize* jsou volitelnou metodou určení velikosti a umístění ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

### <a name="remarks"></a>Poznámky

V`CreateControl`systému je podporována pouze podmnožina příznaků Windows *dwStyle* :

- WS_VISIBLE vytvoří okno, které je zpočátku viditelné. Vyžaduje se, pokud chcete, aby byl ovládací prvek viditelný hned, například v běžných oknech.

- WS_DISABLED vytvoří okno, které je zpočátku zakázané. Zakázané okno nemůže přijmout vstup od uživatele. Lze nastavit, pokud má ovládací prvek vlastnost Enabled.

- WS_BORDER vytvoří okno s ohraničením tenké čáry. Lze nastavit, pokud má ovládací prvek vlastnost BorderStyle.

- WS_GROUP Určuje první ovládací prvek skupiny ovládacích prvků. Uživatel může změnit fokus klávesnice z jednoho ovládacího prvku ve skupině na další pomocí směrových kláves. Všechny ovládací prvky definované pomocí stylu WS_GROUP po prvním ovládacím prvku patří do stejné skupiny. Další ovládací prvek se stylem WS_GROUP ukončí skupinu a spustí další skupinu.

- WS_TABSTOP určuje ovládací prvek, který může obdržet fokus klávesnice, když uživatel stiskne klávesu TAB. Stisknutí klávesy TAB změní fokus klávesnice na další ovládací prvek WS_TABSTOP stylu.

Pomocí druhého přetížení vytvořte ovládací prvky výchozí velikosti.

##  <a name="createolefont"></a>COleControlContainer::CreateOleFont

Vytvoří písmo OLE.

```
void CreateOleFont(CFont* pFont);
```

### <a name="parameters"></a>Parametry

*pFont*<br/>
Ukazatel na písmo, které má být použito kontejnerem ovládacího prvku.

##  <a name="finditem"></a>COleControlContainer::FindItem

Vyhledá vlastní web, který je hostitelem zadané položky.

```
virtual COleControlSite* FindItem(UINT nID) const;
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Identifikátor položky, která se má najít

### <a name="return-value"></a>Návratová hodnota

Ukazatel na vlastní web zadané položky.

##  <a name="freezeallevents"></a>COleControlContainer::FreezeAllEvents

Určuje, zda bude kontejner ignorovat události z připojených lokalit ovládacího prvku, nebo je přijmout.

```
void FreezeAllEvents(BOOL bFreeze);
```

### <a name="parameters"></a>Parametry

*bFreeze*<br/>
Nenulové, pokud budou zpracovány události; v opačném případě 0.

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Ovládací prvek není požadován k zastavení vypálení událostí, pokud je požadován kontejnerem ovládacího prvku. Může pokračovat v napálení, ale všechny následné události budou ignorovány kontejnerem ovládacího prvku.

##  <a name="getambientprop"></a>COleControlContainer::GetAmbientProp

Načte hodnotu zadané ambientní vlastnosti.

```
virtual BOOL GetAmbientProp(
    COleControlSite* pSite,
    DISPID dispid,
    VARIANT* pvarResult);
```

### <a name="parameters"></a>Parametry

*pSite*<br/>
Ukazatel na lokalitu ovládacího prvku, ze které se bude načítat vlastnost okolí.

*dispid*<br/>
ID odeslání požadované vnější vlastnosti.

*pVarResult*<br/>
Ukazatel na hodnotu vlastnosti Ambient.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; v opačném případě 0.

##  <a name="getdlgitem"></a>COleControlContainer::GetDlgItem

Načte ukazatel na určený ovládací prvek nebo podřízené okno v dialogovém okně nebo v jiném okně.

```
virtual CWnd* GetDlgItem(int nID) const;

virtual void GetDlgItem(
    int nID,
    HWND* phWnd) const;
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Identifikátor položky dialogového okna, která se má načíst

*phWnd*<br/>
Ukazatel na popisovač objektu okna dané položky dialogového okna.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na okno položky dialogového okna.

##  <a name="getdlgitemint"></a>  COleControlContainer::GetDlgItemInt

Načte hodnotu přeloženého textu daného ovládacího prvku.

```
virtual UINT GetDlgItemInt(
    int nID,
    BOOL* lpTrans,
    BOOL bSigned) const;
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Identifikátor ovládacího prvku

*lpTrans*<br/>
Ukazatel na logickou proměnnou, která přijímá hodnotu úspěch/selhání funkce (hodnota TRUE označuje úspěch, FALSE označuje selhání).

*bSigned*<br/>
Určuje, zda má funkce kontrolovat text pro symbol mínus na začátku a vracet celočíselnou hodnotu se znaménkem, pokud nalezne jednu. Pokud má parametr *bSigned* hodnotu true, určuje, že hodnota, která má být načtena, je celočíselná hodnota se znaménkem, přetypování návratové hodnoty na typ **int** . Chcete-li získat rozšířené informace o chybě, volejte příkaz [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu je proměnná, na kterou odkazuje *lpTrans* , nastavena na hodnotu true a návratová hodnota je přeložená hodnota řídicího textu.

Pokud se funkce nezdařila, proměnná, na kterou odkazuje *lpTrans* , je nastavena na hodnotu false a vrácená hodnota je nula. Všimněte si, že vzhledem k tomu, že nula je možná přeložená hodnota, návratová hodnota nula neznamená samo o sobě indikaci selhání.

Pokud má *lpTrans* hodnotu null, vrátí funkce žádné informace o úspěchu nebo neúspěchu.

### <a name="remarks"></a>Poznámky

Funkce převede načtený text tak, že na začátku textu vypustí všechny nadbytečné mezery a pak Převede desítkové číslice. Funkce zastaví překládání, když dosáhne konce textu nebo narazí na nečíselný znak.

Tato funkce vrátí nulu, pokud je přeložená hodnota větší než INT_MAX (pro čísla se znaménkem) nebo UINT_MAX (pro čísla bez znaménka).

##  <a name="getdlgitemtext"></a>  COleControlContainer::GetDlgItemText

Načte text daného ovládacího prvku.

```
virtual int GetDlgItemText(
    int nID,
    LPTSTR lpStr,
    int nMaxCount) const;
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Identifikátor ovládacího prvku

*lpStr*<br/>
Ukazatel na text ovládacího prvku.

*nMaxCount*<br/>
Určuje maximální délku řetězce, který má být zkopírován do vyrovnávací paměti, na kterou odkazuje *typem LPStr*. Pokud délka řetězce překračuje limit, řetězec se zkrátí.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, vrácená hodnota určuje počet znaků zkopírovaných do vyrovnávací paměti, včetně ukončujícího znaku null.

Pokud dojde k chybě funkce, vrácená hodnota je nula. Chcete-li získat rozšířené informace o chybě, volejte příkaz [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

##  <a name="handlesetfocus"></a>COleControlContainer::HandleSetFocus

Určuje, zda kontejner zpracovává zprávy WM_SETFOCUS.

```
virtual BOOL HandleSetFocus();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud kontejner zpracovává zprávy WM_SETFOCUS; jinak nula.

##  <a name="handlewindowlessmessage"></a>COleControlContainer::HandleWindowlessMessage

Zpracuje zprávy okna pro ovládací prvky bez oken.

```
virtual BOOL HandleWindowlessMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* plResult);
```

### <a name="parameters"></a>Parametry

*message*<br/>
Identifikátor zprávy okna, který je součástí systému Windows.

*wParam*<br/>
Parametr zprávy; poskytované systémem Windows. Určuje další informace specifické pro zprávu. Obsah tohoto parametru závisí na hodnotě parametru *zprávy* .

*lParam*<br/>
Parametr zprávy; poskytované systémem Windows. Určuje další informace specifické pro zprávu. Obsah tohoto parametru závisí na hodnotě parametru *zprávy* .

*plResult*<br/>
Kód výsledku Windows Určuje výsledek zpracování zprávy a závisí na odeslané zprávě.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud bylo úspěšné; jinak nula.

### <a name="remarks"></a>Poznámky

Přepište tuto funkci, chcete-li přizpůsobit zpracování řídicích zpráv bez oken.

##  <a name="isdlgbuttonchecked"></a>  COleControlContainer::IsDlgButtonChecked

Určuje stav zadaného tlačítka.

```
virtual UINT IsDlgButtonChecked(int nIDButton) const;
```

### <a name="parameters"></a>Parametry

*nIDButton*<br/>
Identifikátor ovládacího prvku tlačítko

### <a name="return-value"></a>Návratová hodnota

Návratová hodnota z tlačítka vytvořeného pomocí stylu BS_AUTOCHECKBOX, BS_AUTORADIOBUTTON, BS_AUTO3STATE, BS_CHECKBOX, BS_RADIOBUTTON nebo BS_3STATE. Může být jedna z následujících akcí:

- Je zaškrtnuto tlačítko BST_CHECKED.

- Tlačítko BST_INDETERMINATE je šedé, což značí neurčitý stav (platí pouze v případě, že tlačítko má styl BS_3STATE nebo BS_AUTO3STATE).

- Tlačítko BST_UNCHECKED je vymazáno.

### <a name="remarks"></a>Poznámky

Pokud je tlačítko ovládacím prvkem se třemi stavy, členská funkce určí, zda je ztlumená, zaškrtnutá nebo žádná.

##  <a name="m_crback"></a>COleControlContainer::m_crBack

Barva pozadí kontejneru.

```
COLORREF m_crBack;
```

##  <a name="m_crfore"></a>COleControlContainer::m_crFore

Barva popředí kontejneru.

```
COLORREF m_crFore;
```

##  <a name="m_listsitesorwnds"></a>COleControlContainer::m_listSitesOrWnds

Seznam lokalit ovládacích prvků hostovaných kontejnerem.

```
CTypedPtrList<CPtrList, COleControlSiteOrWnd*> m_listSitesOrWnds;
```

##  <a name="m_nwindowlesscontrols"></a>COleControlContainer::m_nWindowlessControls

Počet ovládacích prvků bez oken hostovaných kontejnerem ovládacích prvků.

```
int m_nWindowlessControls;
```

##  <a name="m_polefont"></a>COleControlContainer::m_pOleFont

Ukazatel na písmo OLE na webu vlastního ovládacího prvku.

```
LPFONTDISP m_pOleFont;
```

##  <a name="m_psitecapture"></a>  COleControlContainer::m_pSiteCapture

Ukazatel na web ovládacího prvku Capture.

```
COleControlSite* m_pSiteCapture;
```

##  <a name="m_psitefocus"></a>  COleControlContainer::m_pSiteFocus

Ukazatel na web ovládacího prvku, který aktuálně má fokus vstupu.

```
COleControlSite* m_pSiteFocus;
```

##  <a name="m_psiteuiactive"></a>  COleControlContainer::m_pSiteUIActive

Ukazatel na místně aktivovaný web ovládacího prvku.

```
COleControlSite* m_pSiteUIActive;
```

##  <a name="m_pwnd"></a>COleControlContainer::m_pWnd

Ukazatel na objekt okna přidružený ke kontejneru.

```
CWnd* m_pWnd;
```

##  <a name="m_sitemap"></a>  COleControlContainer::m_siteMap

Mapa webu.

```
CMapPtrToPtr m_siteMap;
```

##  <a name="onpaint"></a>COleControlContainer:: propaintt

Volá se rozhraním, aby se zpracovaly požadavky WM_PAINT.

```
virtual BOOL OnPaint(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Ukazatel na kontext zařízení používaný kontejnerem.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byla zpráva zpracována; jinak nula.

### <a name="remarks"></a>Poznámky

Přepište tuto funkci pro přizpůsobení procesu malování.

##  <a name="onuiactivate"></a>COleControlContainer::OnUIActivate

Volá se rozhraním, když se má na místě aktivovat řídicí lokalita, na kterou odkazuje *pSite*.

```
virtual void OnUIActivate(COleControlSite* pSite);
```

### <a name="parameters"></a>Parametry

*pSite*<br/>
Ukazatel na lokalitu ovládacího prvku, který má být na místě aktivované.

### <a name="remarks"></a>Poznámky

Místní aktivace znamená, že je hlavní nabídka kontejneru nahrazena místní nabídkou.

##  <a name="onuideactivate"></a>COleControlContainer::OnUIDeactivate

Volá se rozhraním, když se chystá deaktivovat lokalita ovládacího prvku, na kterou odkazuje *pSite*.

```
virtual void OnUIDeactivate(COleControlSite* pSite);
```

### <a name="parameters"></a>Parametry

*pSite*<br/>
Je třeba deaktivovat ukazatel na lokalitu ovládacího prvku.

### <a name="remarks"></a>Poznámky

Po přijetí tohoto oznámení by měl kontejner znovu nainstalovat své uživatelské rozhraní a provést fokus.

##  <a name="scrollchildren"></a>COleControlContainer::ScrollChildren

Volá se rozhraním, když se z podřízeného okna přijímají zprávy Scroll.

```
virtual void ScrollChildren(
    int dx,
    int dy);
```

### <a name="parameters"></a>Parametry

*dx*<br/>
Množství posouvání podél osy x v pixelech

*dy*<br/>
Množství posouvání podél osy y v pixelech

##  <a name="senddlgitemmessage"></a>COleControlContainer::SendDlgItemMessage

Odešle zprávu na určený ovládací prvek.

```
virtual LRESULT SendDlgItemMessage(
    int nID,
    UINT message,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Určuje identifikátor ovládacího prvku, který přijímá zprávu.

*message*<br/>
Určuje zprávu, která se má odeslat.

*wParam*<br/>
Určuje další informace specifické pro zprávu.

*lParam*<br/>
Určuje další informace specifické pro zprávu.

##  <a name="setdlgitemint"></a>COleControlContainer::SetDlgItemInt

Nastaví text ovládacího prvku v dialogovém okně na řetězcové vyjádření zadané celočíselné hodnoty.

```
virtual void SetDlgItemInt(
    int nID,
    UINT nValue,
    BOOL bSigned);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Identifikátor ovládacího prvku

*nHodnota*<br/>
Celočíselná hodnota, která se má zobrazit

*bSigned*<br/>
Určuje, zda je parametr *nHodnota* podepsán nebo není podepsaný. Pokud má tento parametr hodnotu TRUE, *nHodnota* je podepsán. Pokud má tento parametr hodnotu TRUE a *nHodnota* je menší než nula, symbol mínus se umístí před první číslici v řetězci. Pokud má tento parametr hodnotu FALSE, *nHodnota* je bez znaménka.

##  <a name="setdlgitemtext"></a>  COleControlContainer::SetDlgItemText

Nastaví text zadaného ovládacího prvku pomocí textu obsaženého v *lpszString*.

```
virtual void SetDlgItemText(
    int nID,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Identifikátor ovládacího prvku

*lpszString*<br/>
Ukazatel na text ovládacího prvku.

## <a name="see-also"></a>Viz také:

[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleControlSite – třída](../../mfc/reference/colecontrolsite-class.md)<br/>
[COccManager – třída](../../mfc/reference/coccmanager-class.md)
