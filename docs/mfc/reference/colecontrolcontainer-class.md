---
title: COleControlContainer Class
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
ms.openlocfilehash: 6e97f7ceafb92098d701cba64b4ec01d26d3991a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57274983"
---
# <a name="colecontrolcontainer-class"></a>COleControlContainer Class

Funguje jako kontejner ovládacího prvku pro ovládací prvky ActiveX.

## <a name="syntax"></a>Syntaxe

```
class COleControlContainer : public CCmdTarget
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[COleControlContainer::COleControlContainer](#colecontrolcontainer)|Vytvoří `COleControlContainer` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[COleControlContainer::AttachControlSite](#attachcontrolsite)|Vytvoří ovládací prvek webu, hostitelem kontejneru.|
|[COleControlContainer::BroadcastAmbientPropertyChange](#broadcastambientpropertychange)|Informuje o tom všechny hostované ovládací prvky, které změní vlastnost ambient změnila.|
|[COleControlContainer::CheckDlgButton](#checkdlgbutton)|Upraví ovládacího prvku určeného tlačítka.|
|[COleControlContainer::CheckRadioButton](#checkradiobutton)|Vybere zadaný přepínač skupiny.|
|[COleControlContainer::CreateControl](#createcontrol)|Vytvoří hostovaného ovládacího prvku ActiveX.|
|[COleControlContainer::CreateOleFont](#createolefont)|Vytvoří písmo OLE.|
|[COleControlContainer::FindItem](#finditem)|Vrátí vlastní web určený ovládací prvek.|
|[COleControlContainer::FreezeAllEvents](#freezeallevents)|Určuje, pokud ovládací prvek webu přijímá události.|
|[COleControlContainer::GetAmbientProp](#getambientprop)|Načte zadaný vedlejší vlastnost.|
|[COleControlContainer::GetDlgItem](#getdlgitem)|Načte zadaný dialogového okna ovládacího prvku.|
|[COleControlContainer::GetDlgItemInt](#getdlgitemint)|Načte hodnotu zadaného dialogového okna ovládacího prvku.|
|[COleControlContainer::GetDlgItemText](#getdlgitemtext)|Načte popisek ovládacího prvku zadané dialogového okna.|
|[COleControlContainer::HandleSetFocus](#handlesetfocus)|Určuje, pokud kontejner zpracovává WM_SETFOCUS zprávy.|
|[COleControlContainer::HandleWindowlessMessage](#handlewindowlessmessage)|Zpracovává zprávy odeslané na ovládací prvek bez oken.|
|[COleControlContainer::IsDlgButtonChecked](#isdlgbuttonchecked)|Určuje stav určeného tlačítka.|
|[COleControlContainer::OnPaint](#onpaint)|Volá se, aby repaint část kontejneru.|
|[COleControlContainer::OnUIActivate](#onuiactivate)|Volá se, když je ovládací prvek bude aktivovat na místě.|
|[COleControlContainer::OnUIDeactivate](#onuideactivate)|Volá se, když je ovládací prvek se deaktivuje.|
|[COleControlContainer::ScrollChildren](#scrollchildren)|Volá se rozhraním při posouvání zprávy byly přijaty z podřízeného okna.|
|[COleControlContainer::SendDlgItemMessage](#senddlgitemmessage)|Odešle zprávu pro zadaný ovládací prvek.|
|[COleControlContainer::SetDlgItemInt](#setdlgitemint)|Nastaví hodnotu zadaného prvku.|
|[COleControlContainer::SetDlgItemText](#setdlgitemtext)|Nastaví text zadaný ovládací prvek.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[COleControlContainer::m_crBack](#m_crback)|Barva pozadí kontejneru.|
|[COleControlContainer::m_crFore](#m_crfore)|Barva popředí kontejneru.|
|[COleControlContainer::m_listSitesOrWnds](#m_listsitesorwnds)|Seznam podporovaných ovládací prvky stránky.|
|[COleControlContainer::m_nWindowlessControls](#m_nwindowlesscontrols)|Počet hostované ovládací prvky bez oken.|
|[COleControlContainer::m_pOleFont](#m_polefont)|Ukazatel na písmo OLE vlastního ovládacího prvku lokality.|
|[COleControlContainer::m_pSiteCapture](#m_psitecapture)|Ukazatel na ovládací prvek webu zachycení.|
|[COleControlContainer::m_pSiteFocus](#m_psitefocus)|Ukazatel na ovládací prvek, který aktuálně má vstupní fokus.|
|[COleControlContainer::m_pSiteUIActive](#m_psiteuiactive)|Ukazatel na ovládací prvek, který je aktuálně aktivovaná v místě.|
|[COleControlContainer::m_pWnd](#m_pwnd)|Ukazatel na implementaci kontejnerem ovládacího prvku okna.|
|[COleControlContainer::m_siteMap](#m_sitemap)|Mapa webu.|

## <a name="remarks"></a>Poznámky

Je to tím, že poskytuje podporu pro jednu nebo více lokalit ovládacího prvku ActiveX (implementované `COleControlSite`). `COleControlContainer` plně implementuje [IOleInPlaceFrame](/windows/desktop/api/oleidl/nn-oleidl-ioleinplaceframe) a [IOleContainer](/windows/desktop/api/oleidl/nn-oleidl-iolecontainer) rozhraní, což obsažené ovládací prvky ActiveX ke splnění jejich kvalifikace jako místní položky.

Tato třída se často používá ve spojení s `COccManager` a `COleControlSite` implementovat vlastní kontejner ovládacího prvku ActiveX, s vlastní weby pro jednu nebo více ovládacích prvků ActiveX.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleControlContainer`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxocc.h

##  <a name="attachcontrolsite"></a>  COleControlContainer::AttachControlSite

Volá se rozhraním, které chcete vytvořit a připojit lokalitu ovládacího prvku.

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
Ukazatel `CWnd` objektu.

*nIDC*<br/>
ID ovládacího prvku na připojit.

### <a name="remarks"></a>Poznámky

Tato funkce přepište, pokud chcete tento proces přizpůsobit.

> [!NOTE]
>  První formulář této funkce použijte, pokud jsou staticky připojování ke knihovně MFC. Pokud jsou dynamického propojení ke knihovně MFC, použijte druhý formulář.

##  <a name="broadcastambientpropertychange"></a>  COleControlContainer::BroadcastAmbientPropertyChange

Informuje o tom všechny hostované ovládací prvky, které změní vlastnost ambient změnila.

```
virtual void BroadcastAmbientPropertyChange(DISPID dispid);
```

### <a name="parameters"></a>Parametry

*dispid*<br/>
ID odbavení vedlejší vlastnost mění.

### <a name="remarks"></a>Poznámky

Tato funkce je volána rozhraním, změní vlastnost ambient se při změně hodnoty. Tuto funkci k přizpůsobení toto chování přepište.

##  <a name="checkdlgbutton"></a>  COleControlContainer::CheckDlgButton

Změní aktuální stav tlačítka.

```
virtual void CheckDlgButton(
    int nIDButton,
    UINT nCheck);
```

### <a name="parameters"></a>Parametry

*nIDButton*<br/>
ID na tlačítko Upravit.

*nZkontrolujte*<br/>
Určuje stav tlačítka. Může být jedna z následujících akcí:

- Kontroluje stav tlačítka, který má BST_CHECKED sady.

- BST_INDETERMINATE sady šedý stav tlačítka, který má určující neurčitém stavu. Tuto hodnotu lze používejte pouze v případě, že tlačítko má BS_3STATE nebo BS_AUTO3STATE style.

- BST_UNCHECKED nastaví stav tlačítka, který se má vymazat.

##  <a name="checkradiobutton"></a>  COleControlContainer::CheckRadioButton

Vybere zadaný přepínač ve skupině a vymaže zbývající tlačítka ve skupině.

```
virtual void CheckRadioButton(
    int nIDFirstButton,
    int nIDLastButton,
    int nIDCheckButton);
```

### <a name="parameters"></a>Parametry

*nIDFirstButton*<br/>
Určuje identifikátor první přepínací tlačítko ve skupině.

*nIDLastButton*<br/>
Určuje identifikátor používaného poslední přepínač ve skupině.

*nIDCheckButton*<br/>
Určuje identifikátor přepínací tlačítko, která se má zkontrolovat.

##  <a name="colecontrolcontainer"></a>  COleControlContainer::COleControlContainer

Vytvoří `COleControlContainer` objektu.

```
explicit COleControlContainer(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazatel na nadřazené okno ovládacího prvku kontejneru.

### <a name="remarks"></a>Poznámky

Po úspěšném vytvoření objektu přidat vlastní ovládací prvek webu pomocí volání `AttachControlSite`.

##  <a name="createcontrol"></a>  COleControlContainer::CreateControl

Vytvoří ovládací prvek ActiveX hostitelem zadané `COleControlSite` objektu.

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
Ukazatel na objekt window představující ovládací prvek.

*clsid*<br/>
Třída jedinečné ID ovládacího prvku.

*lpszWindowName*<br/>
Ukazatel na text, který se zobrazí v ovládacím prvku. Nastaví hodnotu vlastnosti ovládacího prvku popisek nebo Text (pokud existuje). Pokud má hodnotu NULL, titulek a Text ovládacího prvku se nezmění.

*dwStyle*<br/>
Styly Windows. Dostupné styly jsou uvedeny v části **poznámky** oddílu.

*Rect*<br/>
Určuje velikost a umístění ovládacího prvku. Může se jednat buď `CRect` objektu nebo `RECT` struktury.

*nID*<br/>
Určuje ID ovládacího prvku podřízené okno.

*pPersist*<br/>
Ukazatel `CFile` obsahující trvalý stav ovládacího prvku. Výchozí hodnota je NULL označující, že ovládací prvek se inicializuje bez obnovení stavu z jakékoli trvalého úložiště. Pokud není NULL, mělo by být ukazatel `CFile`-odvozenému objektu, který obsahuje ovládací prvek trvalá data ve formě datového proudu nebo úložiště. Tato data by byla uložena do předchozí aktivace klienta. `CFile` Může obsahovat další data, ale musí být ukazatel jeho čtení a zápis nastavení do prvního bajtu trvalá data v okamžiku volání `CreateControl`.

*bStorage*<br/>
Určuje, zda data v *pPersist* by měl být interpretován jako `IStorage` nebo `IStream` data. Pokud data v *pPersist* je úložiště, *bStorage* by měla být nastavena na možnost PRAVDA. Pokud data v *pPersist* je datový proud, *bStorage* by měl mít hodnotu FALSE. Výchozí hodnota je FALSE.

*bstrLicKey*<br/>
Volitelné licenční klíče data. Tato data je potřeba jenom pro vytváření ovládacích prvků, které vyžadují za běhu licenční klíč. Pokud ovládací prvek podporuje licencování, je nutné zadat licenční klíč pro vytvoření ovládacího prvku na úspěšné. Výchozí hodnota je NULL.

*ppNewSite*<br/>
Ukazatel na existující web ovládací prvek, který bude hostitelem vytváří ovládacího prvku. Výchozí hodnota je NULL, která udává, že nový ovládací prvek webu budou automaticky vytvoří a připojí do nového ovládacího prvku.

*ppt*<br/>
Ukazatel `POINT` strukturu, která obsahuje levého horního rohu ovládacího prvku. Velikost ovládacího prvku, je určen hodnotou *psize*. *Ppt* a *psize* hodnoty jsou volitelné metodu pro určení velikosti a pozice ovládacího prvku.

*psize*<br/>
Ukazatel `SIZE` strukturu, která obsahuje velikost ovládacího prvku. Levém horním rohu je určen hodnotou *ppt*. *Ppt* a *psize* hodnoty jsou volitelné metodu pro určení velikosti a pozice ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

### <a name="remarks"></a>Poznámky

Pouze podmnožinu Windows *dwStyle* nepodporuje příznaky `CreateControl`:

- WS_VISIBLE vytvoří okno, které je zpočátku viditelné. Povinné, pokud chcete, aby ovládací prvek viditelný okamžitě, stejně jako běžná okna.

- WS_DISABLED vytvoří okno, které je zpočátku zakázáno. Zakázané okno nepřijímá vstup od uživatele. Můžete nastavit, pokud ovládací prvek má vlastnost Enabled.

- WS_BORDER vytvoří okno s dynamické čáry ohraničení. Můžete nastavit, pokud ovládací prvek má vlastnosti BorderStyle.

- WS_GROUP Určuje první prvek skupiny ovládacích prvků. Uživatel může změnit fokus klávesnice z jednoho ovládacího prvku ve skupině na další pomocí šipkových kláves. Všechny ovládací prvky definované ve stylu WS_GROUP po prvním ovládacím prvku, patří do stejné skupiny. Další ovládací prvek se stylem WS_GROUP končí skupině a začíná další skupinu.

- WS_TABSTOP určuje ovládací prvek, který může získat fokus klávesnice, když uživatel stiskne klávesu TAB. Na další ovládací prvek stylu WS_TABSTOP stisknutím klávesy TAB změní fokus klávesnice.

Druhé přetížení použijte k vytvoření výchozí velikosti ovládacích prvků.

##  <a name="createolefont"></a>  COleControlContainer::CreateOleFont

Vytvoří písmo OLE.

```
void CreateOleFont(CFont* pFont);
```

### <a name="parameters"></a>Parametry

*pFont*<br/>
Ukazatel na písma pro ovládací prvek kontejneru.

##  <a name="finditem"></a>  COleControlContainer::FindItem

Vyhledá vlastní web, který je hostitelem zadané položky.

```
virtual COleControlSite* FindItem(UINT nID) const;
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Identifikátor položky, která se má najít.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na vlastní web zadané položky.

##  <a name="freezeallevents"></a>  COleControlContainer::FreezeAllEvents

Určuje, zda kontejner bude ignorovat události z lokalit připojeného ovládacího prvku nebo je přijmout.

```
void FreezeAllEvents(BOOL bFreeze);
```

### <a name="parameters"></a>Parametry

*bFreeze*<br/>
Nenulové, pokud události budou zpracovány; jinak 0.

### <a name="remarks"></a>Poznámky

> [!NOTE]
>  Ovládací prvek není potřeba zastavit vyvolává události, pokud to vyžaduje kontejnerem ovládacího prvku. Může pokračovat v jeho spuštění, ale budou ignorovány všechny další události kontejnerem ovládacího prvku.

##  <a name="getambientprop"></a>  COleControlContainer::GetAmbientProp

Načte hodnotu zadané vlastnosti okolí.

```
virtual BOOL GetAmbientProp(
    COleControlSite* pSite,
    DISPID dispid,
    VARIANT* pvarResult);
```

### <a name="parameters"></a>Parametry

*pSite*<br/>
Ukazatel na ovládací prvek webu, ze kterého se budou načítat vedlejší vlastnost.

*dispid*<br/>
ID odbavení požadované vedlejší vlastnost.

*pVarResult*<br/>
Ukazatel na hodnotu vedlejší vlastnost.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak 0.

##  <a name="getdlgitem"></a>  COleControlContainer::GetDlgItem

Načte ukazatel na určené okno, nebo podřízený ovládací prvek v dialogovém okně nebo jiné okno.

```
virtual CWnd* GetDlgItem(int nID) const;

virtual void GetDlgItem(
    int nID,
    HWND* phWnd) const;
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Identifikátor položky dialogového okna pro načtení.

*phWnd*<br/>
Ukazatel na popisovač objektu window položku zadané dialogového okna.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na okno položky dialogového okna.

##  <a name="getdlgitemint"></a>  COleControlContainer::GetDlgItemInt

Načte hodnotu přeložený text zadaný ovládací prvek.

```
virtual UINT GetDlgItemInt(
    int nID,
    BOOL* lpTrans,
    BOOL bSigned) const;
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Identifikátor ovládacího prvku.

*lpTrans*<br/>
Ukazatel na logickou hodnotu, která přijímá hodnotu úspěch nebo selhání – funkce (hodnota TRUE označuje úspěch, hodnota FALSE označuje selhání).

*bSigned*<br/>
Určuje, zda by měla funkce prozkoumají text pro znaménko mínus na začátku a nenalezne-li vrátit hodnotu se znaménkem. Pokud *bSigned* parametr má hodnotu TRUE, určení, že je hodnota má být načtena hodnota celé číslo se znaménkem, přetypovávat návratovou hodnotu pro **int** typu. Chcete-li získat rozšířené informace o chybě, volejte [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360).

### <a name="return-value"></a>Návratová hodnota

Pokud úspěšné, proměnná ukazuje *lpTrans* nastavena na hodnotu TRUE, a návratová hodnota je hodnota přeložený text ovládacího prvku.

Pokud funkce selže, proměnná ukazuje *lpTrans* je nastavena na hodnotu FALSE, a vrácená hodnota je nula. Všimněte si, že nula je možné přeložené hodnoty, návratová hodnota nula samostatně neznamená selhání.

Pokud *lpTrans* má hodnotu NULL, funkce vrátí žádné informace o úspěchu nebo neúspěchu.

### <a name="remarks"></a>Poznámky

Funkce přeloží načtený text tak, že odstranění nadbytečné mezery na začátku text a pak převod desítkových číslic. Funkce zastaví překladu při dosažení konce text nebo zaznamená znaku číselného typu.

Tato funkce vrátí hodnotu 0, pokud přeloženou hodnota je větší než INT_MAX (pro čísla se znaménkem) nebo UINT_MAX (pro čísel bez znaménka).

##  <a name="getdlgitemtext"></a>  COleControlContainer::GetDlgItemText

Načte text zadaný ovládací prvek.

```
virtual int GetDlgItemText(
    int nID,
    LPTSTR lpStr,
    int nMaxCount) const;
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Identifikátor ovládacího prvku.

*lpStr*<br/>
Ukazatel na text ovládacího prvku.

*nMaxCount*<br/>
Určuje maximální délku znaků, řetězec, který má být zkopírován do vyrovnávací paměti, na které odkazuje *lpStr*. Pokud délka řetězce překračuje limit, řetězec je zkrácen.

### <a name="return-value"></a>Návratová hodnota

Pokud funkce uspěje, vrácená hodnota určuje počet znaků, které jsou zkopírovány do vyrovnávací paměti, bez ukončujícího znaku null.

Pokud funkce selže, vrácená hodnota je nula. Chcete-li získat rozšířené informace o chybě, volejte [GetLastError](https://msdn.microsoft.com/library/windows/desktop/ms679360).

##  <a name="handlesetfocus"></a>  COleControlContainer::HandleSetFocus

Určuje, pokud kontejner zpracovává WM_SETFOCUS zprávy.

```
virtual BOOL HandleSetFocus();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud kontejner zpracovává WM_SETFOCUS zprávy. jinak nula.

##  <a name="handlewindowlessmessage"></a>  COleControlContainer::HandleWindowlessMessage

Zpracovává zprávy okna pro ovládací prvky bez oken.

```
virtual BOOL HandleWindowlessMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* plResult);
```

### <a name="parameters"></a>Parametry

*message*<br/>
Identifikátor zprávy okna, poskytované Windows.

*wParam*<br/>
Parametr message; k dispozici ve Windows. Určuje další informace specifické pro zprávy. Obsah tohoto parametru závisí na hodnotě *zpráva* parametru.

*lParam*<br/>
Parametr message; k dispozici ve Windows. Určuje další informace specifické pro zprávy. Obsah tohoto parametru závisí na hodnotě *zpráva* parametru.

*plResult*<br/>
Kód výsledku Windows. Určuje výsledek zpracování zprávy a závisí na zprávy odeslané.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je úspěšná. jinak nula.

### <a name="remarks"></a>Poznámky

Přepsání této funkce můžete přizpůsobit zpracování zprávy pro ovládací prvek bez oken.

##  <a name="isdlgbuttonchecked"></a>  COleControlContainer::IsDlgButtonChecked

Určuje stav určeného tlačítka.

```
virtual UINT IsDlgButtonChecked(int nIDButton) const;
```

### <a name="parameters"></a>Parametry

*nIDButton*<br/>
Identifikátor ovládacího prvku tlačítko.

### <a name="return-value"></a>Návratová hodnota

Návratová hodnota z vytvořené pomocí BS_AUTOCHECKBOX, BS_AUTORADIOBUTTON, BS_AUTO3STATE, BS_CHECKBOX, BS_RADIOBUTTON nebo BS_3STATE styl tlačítka. Může být jedna z následujících akcí:

- Zaškrtnutí BST_CHECKED tlačítka.

- BST_INDETERMINATE tlačítko nejde aktivovat, určující neurčitém stavu (platí jenom v případě, že tlačítko má BS_3STATE nebo BS_AUTO3STATE style).

- Tlačítko BST_UNCHECKED je zrušeno.

### <a name="remarks"></a>Poznámky

Je-li na tlačítko se třemi stavy ovládacího prvku, členská funkce určuje, zda je zobrazené šedě, zaškrtnuto, nebo ani jedna.

##  <a name="m_crback"></a>  COleControlContainer::m_crBack

Barva pozadí kontejneru.

```
COLORREF m_crBack;
```

##  <a name="m_crfore"></a>  COleControlContainer::m_crFore

Barva popředí kontejneru.

```
COLORREF m_crFore;
```

##  <a name="m_listsitesorwnds"></a>  COleControlContainer::m_listSitesOrWnds

Seznam ovládací prvky stránky, který je hostitelem kontejneru.

```
CTypedPtrList<CPtrList, COleControlSiteOrWnd*> m_listSitesOrWnds;
```

##  <a name="m_nwindowlesscontrols"></a>  COleControlContainer::m_nWindowlessControls

Počet ovládací prvky bez oken hostitelem kontejneru ovládacího prvku.

```
int m_nWindowlessControls;
```

##  <a name="m_polefont"></a>  COleControlContainer::m_pOleFont

Ukazatel na písmo OLE vlastního ovládacího prvku lokality.

```
LPFONTDISP m_pOleFont;
```

##  <a name="m_psitecapture"></a>  COleControlContainer::m_pSiteCapture

Ukazatel na ovládací prvek webu zachycení.

```
COleControlSite* m_pSiteCapture;
```

##  <a name="m_psitefocus"></a>  COleControlContainer::m_pSiteFocus

Ukazatel na webu, které aktuálně pro ovládací prvek má vstupní fokus.

```
COleControlSite* m_pSiteFocus;
```

##  <a name="m_psiteuiactive"></a>  COleControlContainer::m_pSiteUIActive

Ukazatel na ovládací prvek webu, který se aktivuje v místě.

```
COleControlSite* m_pSiteUIActive;
```

##  <a name="m_pwnd"></a>  COleControlContainer::m_pWnd

Ukazatel na objekt okna spojenými s daným kontejnerem.

```
CWnd* m_pWnd;
```

##  <a name="m_sitemap"></a>  COleControlContainer::m_siteMap

Mapa webu.

```
CMapPtrToPtr m_siteMap;
```

##  <a name="onpaint"></a>  COleControlContainer::OnPaint

Volá se rozhraním pro zpracování požadavků WM_PAINT.

```
virtual BOOL OnPaint(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*pDC*<br/>
Ukazatel na kontext zařízení používá kontejneru.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud zpráva byla zpracována; jinak nula.

### <a name="remarks"></a>Poznámky

Přepsání této funkce můžete přizpůsobit proces vykreslování.

##  <a name="onuiactivate"></a>  COleControlContainer::OnUIActivate

Volá se rozhraním, když ovládací prvek webu, na které odkazuje *pSite*, bude zrovna místně aktivuje.

```
virtual void OnUIActivate(COleControlSite* pSite);
```

### <a name="parameters"></a>Parametry

*pSite*<br/>
Ukazatel na ovládací prvek webu bude aktivovat na místě.

### <a name="remarks"></a>Poznámky

Aktivace na místě znamená, že hlavní nabídky kontejneru je nahrazena složená nabídka na místě.

##  <a name="onuideactivate"></a>  COleControlContainer::OnUIDeactivate

Volá se rozhraním, když ovládací prvek webu, na které odkazuje *pSite*, se deaktivuje.

```
virtual void OnUIDeactivate(COleControlSite* pSite);
```

### <a name="parameters"></a>Parametry

*pSite*<br/>
Ukazatel na ovládací prvek webu se deaktivuje.

### <a name="remarks"></a>Poznámky

Po přijetí tohoto oznámení by měl kontejneru přeinstalujte uživatelského rozhraní a být aktivován.

##  <a name="scrollchildren"></a>  COleControlContainer::ScrollChildren

Volá se rozhraním při posouvání zprávy byly přijaty z podřízeného okna.

```
virtual void ScrollChildren(
    int dx,
    int dy);
```

### <a name="parameters"></a>Parametry

*dx*<br/>
Velikost, v pixelech, posouvání podél osy x.

*dy*<br/>
Velikost, v pixelech, posouvání podél osy y.

##  <a name="senddlgitemmessage"></a>  COleControlContainer::SendDlgItemMessage

Odešle zprávu pro zadaný ovládací prvek.

```
virtual LRESULT SendDlgItemMessage(
    int nID,
    UINT message,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Určuje identifikátor ovládacího prvku, který obdrží zprávu.

*message*<br/>
Určuje zprávu, která má být odeslána.

*wParam*<br/>
Určuje další informace specifické pro zprávy.

*lParam*<br/>
Určuje další informace specifické pro zprávy.

##  <a name="setdlgitemint"></a>  COleControlContainer::SetDlgItemInt

Nastaví text ovládacího prvku v dialogovém okně na řetězcovou reprezentaci zadaného celočíselné hodnoty.

```
virtual void SetDlgItemInt(
    int nID,
    UINT nValue,
    BOOL bSigned);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Identifikátor ovládacího prvku.

*nValue*<br/>
Celočíselná hodnota, který se má zobrazit.

*bSigned*<br/>
Určuje, zda *nHodnota* parametr je podepsaný nebo nepodepsaný řetězec. Pokud tento parametr má hodnotu TRUE, *nHodnota* je podepsán. Pokud tento parametr má hodnotu TRUE a *nHodnota* je menší než nula, minus přihlášení je umístěn před první číslice v řetězci. Pokud tento parametr má hodnotu FALSE, *nHodnota* je bez znaménka.

##  <a name="setdlgitemtext"></a>  COleControlContainer::SetDlgItemText

Nastaví text zadaný ovládací prvek pomocí textu součástí *lpszString*.

```
virtual void SetDlgItemText(
    int nID,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>Parametry

*nID*<br/>
Identifikátor ovládacího prvku.

*lpszString*<br/>
Ukazatel na text ovládacího prvku.

## <a name="see-also"></a>Viz také:

[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleControlSite – třída](../../mfc/reference/colecontrolsite-class.md)<br/>
[COccManager – třída](../../mfc/reference/coccmanager-class.md)
