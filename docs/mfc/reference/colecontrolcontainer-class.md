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
ms.openlocfilehash: b1737b2ac114181a4245fff027b756ca30b64129
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366183"
---
# <a name="colecontrolcontainer-class"></a>COleControlContainer – třída

Funguje jako řídicí kontejner pro ovládací prvky ActiveX.

## <a name="syntax"></a>Syntaxe

```
class COleControlContainer : public CCmdTarget
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[COleControlContainer::COleControlContainer](#colecontrolcontainer)|Vytvoří `COleControlContainer` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[COleControlContainer::AttachControlSite](#attachcontrolsite)|Vytvoří řídicí web hostovaný kontejnerem.|
|[COleControlContainer::BroadcastAmbientPropertyChange](#broadcastambientpropertychange)|Informuje všechny hostované ovládací prvky, že došlo ke změně vlastnosti okolí.|
|[COleControlContainer::CheckDlgButton](#checkdlgbutton)|Upraví zadaný ovládací prvek tlačítka.|
|[COleControlContainer::CheckRadioButton](#checkradiobutton)|Vybere zadané přepínací tlačítko skupiny.|
|[COleControlContainer::CreateControl](#createcontrol)|Vytvoří hostovaný ovládací prvek ActiveX.|
|[COleControlContainer::CreateOleFont](#createolefont)|Vytvoří písmo OLE.|
|[COleControlContainer::FindItem](#finditem)|Vrátí vlastní web zadaného ovládacího prvku.|
|[COleControlContainer::FreezeAllEvents](#freezeallevents)|Určuje, zda řídicí web přijímá události.|
|[COleControlContainer::GetAmbientProp](#getambientprop)|Načte zadanou vlastnost ambient.|
|[COleControlContainer::GetDlgItem](#getdlgitem)|Načte zadaný ovládací prvek dialogového okna.|
|[COleControlContainer::GetDlgItemInt](#getdlgitemint)|Načte hodnotu zadaného ovládacího prvku dialogového okna.|
|[COleControlContainer::GetDlgItemText](#getdlgitemtext)|Načte titulek zadaného ovládacího prvku dialogového okna.|
|[COleControlContainer::HandleSetFocus](#handlesetfocus)|Určuje, zda kontejner zpracovává WM_SETFOCUS zprávy.|
|[COleControlContainer::HandleWindowlessMessage](#handlewindowlessmessage)|Zpracovává zprávy odeslané ovládacímu prvku bez oken.|
|[COleControlContainer::IsDlgButtonKontrolováno](#isdlgbuttonchecked)|Určuje stav zadaného tlačítka.|
|[COleControlContainer::OnPaint](#onpaint)|Volána k překreslení části kontejneru.|
|[COleControlContainer::OnuiActivate](#onuiactivate)|Nazývá se, když se má aktivovat ovládací prvek na místě.|
|[COleControlContainer::OnUIDeactivate](#onuideactivate)|Nazývá se, když má být ovládací prvek deaktivován.|
|[COleControlContainer::ScrollChildren](#scrollchildren)|Volat rámci při posouvání zprávy jsou přijímány z podřízeného okna.|
|[COleControlContainer::SendDlgItemMessage](#senddlgitemmessage)|Odešle zprávu zadanému ovládacímu prvku.|
|[COleControlContainer::SetDlgItemInt](#setdlgitemint)|Nastaví hodnotu zadaného ovládacího prvku.|
|[COleControlContainer::SetDlgItemText](#setdlgitemtext)|Nastaví text zadaného ovládacího prvku.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name (Název)|Popis|
|----------|-----------------|
|[COleControlContainer::m_crBack](#m_crback)|Barva pozadí kontejneru.|
|[COleControlContainer::m_crFore](#m_crfore)|Barva popředí kontejneru.|
|[COleControlContainer::m_listSitesOrWnds](#m_listsitesorwnds)|Seznam podporovaných řídicích webů.|
|[COleControlContainer::m_nWindowlessControls](#m_nwindowlesscontrols)|Počet hostovaných ovládacích prvků bez oken.|
|[COleControlContainer::m_pOleFont](#m_polefont)|Ukazatel na písmo OLE vlastního webu ovládacího prvku.|
|[COleControlContainer::m_pSiteCapture](#m_psitecapture)|Ukazatel na lokalitu ovládacího prvku sběru.|
|[COleControlContainer::m_pSiteFocus](#m_psitefocus)|Ukazatel na ovládací prvek, který má aktuálně vstupní fokus.|
|[COleControlContainer::m_pSiteUIActive](#m_psiteuiactive)|Ukazatel na ovládací prvek, který je aktuálně aktivován na místě.|
|[COleControlContainer::m_pWnd](#m_pwnd)|Ukazatel na okno implementace kontejneru ovládacího prvku.|
|[COleControlContainer::m_siteMap](#m_sitemap)|Mapa webu.|

## <a name="remarks"></a>Poznámky

To se provádí poskytováním podpory pro jeden nebo `COleControlSite`více lokalit ovládacích prvku ActiveX (implementovaných ). `COleControlContainer`plně implementuje [rozhraní IOleInPlaceFrame](/windows/win32/api/oleidl/nn-oleidl-ioleinplaceframe) a [IOleContainer,](/windows/win32/api/oleidl/nn-oleidl-iolecontainer) což umožňuje obsaženým ovládacím prvkům ActiveX plnit jejich kvalifikace jako položky na místě.

Tato třída se běžně používá `COccManager` ve `COleControlSite` spojení s a implementovat vlastní kontejner ovládacího prvku ActiveX s vlastními weby pro jeden nebo více ovládacích prvků ActiveX.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

`COleControlContainer`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxocc.h

## <a name="colecontrolcontainerattachcontrolsite"></a><a name="attachcontrolsite"></a>COleControlContainer::AttachControlSite

Volat rámci vytvořit a připojit řídicí lokality.

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
ID ovládacího prvku, který má být připojen.

### <a name="remarks"></a>Poznámky

Přepsat tuto funkci, pokud chcete přizpůsobit tento proces.

> [!NOTE]
> První formulář této funkce použijte, pokud staticky propojujete knihovnu knihovny MFC. Druhý formulář použijte, pokud dynamicky propojujete knihovnu knihovny MFC.

## <a name="colecontrolcontainerbroadcastambientpropertychange"></a><a name="broadcastambientpropertychange"></a>COleControlContainer::BroadcastAmbientPropertyChange

Informuje všechny hostované ovládací prvky, že došlo ke změně vlastnosti okolí.

```
virtual void BroadcastAmbientPropertyChange(DISPID dispid);
```

### <a name="parameters"></a>Parametry

*Dispid*<br/>
ID odeslání okolní vlastnosti, která byla změněna.

### <a name="remarks"></a>Poznámky

Tato funkce je volána rámci při okolní vlastnost změnila hodnotu. Přepište tuto funkci přizpůsobit toto chování.

## <a name="colecontrolcontainercheckdlgbutton"></a><a name="checkdlgbutton"></a>COleControlContainer::CheckDlgButton

Upraví aktuální stav tlačítka.

```
virtual void CheckDlgButton(
    int nIDButton,
    UINT nCheck);
```

### <a name="parameters"></a>Parametry

*nIDButton*<br/>
ID tlačítka, které má být změněno.

*nKontrola*<br/>
Určuje stav tlačítka. Může to být jedna z následujících možností:

- BST_CHECKED Nastaví zaškrtnutí stavu tlačítka.

- BST_INDETERMINATE Nastaví stav tlačítka na šedě, což označuje neurčitý stav. Tuto hodnotu použijte pouze v případě, že tlačítko má styl BS_3STATE nebo BS_AUTO3STATE.

- BST_UNCHECKED Nastaví, aby se stav tlačítka vymaže.

## <a name="colecontrolcontainercheckradiobutton"></a><a name="checkradiobutton"></a>COleControlContainer::CheckRadioButton

Vybere zadané přepínací tlačítko ve skupině a vymaže zbývající tlačítka ve skupině.

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
Určuje identifikátor přepínacího tlačítka, které má být zkontrolováno.

## <a name="colecontrolcontainercolecontrolcontainer"></a><a name="colecontrolcontainer"></a>COleControlContainer::COleControlContainer

Vytvoří `COleControlContainer` objekt.

```
explicit COleControlContainer(CWnd* pWnd);
```

### <a name="parameters"></a>Parametry

*pWnd*<br/>
Ukazatel na nadřazené okno kontejneru ovládacího prvku.

### <a name="remarks"></a>Poznámky

Po úspěšném vytvoření objektu přidejte vlastní řídicí web `AttachControlSite`s voláním aplikace .

## <a name="colecontrolcontainercreatecontrol"></a><a name="createcontrol"></a>COleControlContainer::CreateControl

Vytvoří ovládací prvek ActiveX, který `COleControlSite` je hostován zadaným objektem.

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
Ukazatel na objekt okna představující ovládací prvek.

*Identifikátor clsid*<br/>
Jedinečné ID třídy ovládacího prvku.

*lpszNázev_okna*<br/>
Ukazatel na text, který má být zobrazen v ovládacím prvku. Nastaví hodnotu vlastnosti Titulek nebo Text ovládacího prvku (pokud existuje). Pokud null, ovládací prvek Caption nebo Text vlastnost se nezmění.

*dwStyl*<br/>
Styly systému Windows. Dostupné styly jsou uvedeny v části **Poznámky.**

*Rect*<br/>
Určuje velikost a umístění ovládacího prvku. Může to být `CRect` objekt `RECT` nebo struktura.

*Nid*<br/>
Určuje ID podřízeného okna ovládacího prvku.

*pPřetrvávají*<br/>
Ukazatel na `CFile` obsahující trvalý stav ovládacího prvku. Výchozí hodnota je NULL, označující, že ovládací prvek inicializuje sám bez obnovení jeho stavu z jakékoli trvalé úložiště. Pokud není NULL, by měl `CFile`být ukazatel na -odvozený objekt, který obsahuje trvalé data ovládacího prvku, ve formě datového proudu nebo úložiště. Tato data mohla být uložena při předchozí aktivaci klienta. Může `CFile` obsahovat jiná data, ale musí mít ukazatel pro čtení a zápis nastavený na `CreateControl`první bajt trvalých dat v době volání aplikace .

*bÚložiště*<br/>
Označuje, zda data v *pPersist* `IStorage` by `IStream` měla být interpretována jako nebo data. Pokud data v *pPersist* je úložiště, *bStorage* by měla být TRUE. Pokud data v *pPersist* je datový proud, *bStorage* by měl být FALSE. Výchozí hodnota je FALSE.

*bstrLicKey*<br/>
Volitelná data licenčního klíče. Tato data jsou potřebná pouze pro vytváření ovládacích prvků, které vyžadují licenční klíč za běhu. Pokud ovládací prvek podporuje licencování, je nutné zadat licenční klíč pro vytvoření ovládacího prvku úspěšné. Výchozí hodnota je NULL.

*ppNewSite*<br/>
Ukazatel na existující lokalitu ovládacího prvku, který bude hostitelem vytvářený ovládací prvek. Výchozí hodnota je NULL, což znamená, že nový server ovládacího prvku bude automaticky vytvořen a připojen k novému ovládacímu prvku.

*Ppt*<br/>
Ukazatel na `POINT` strukturu, která obsahuje levý horní roh ovládacího prvku. Velikost ovládacího prvku je určena hodnotou *psize*. Hodnoty *ppt* a *psize* jsou volitelnou metodou určení velikosti a umístění ovládacího prvku.

*pvelikost*<br/>
Ukazatel na `SIZE` strukturu, která obsahuje velikost ovládacího prvku. Levý horní roh je určen hodnotou *ppt*. Hodnoty *ppt* a *psize* jsou volitelnou metodou určení velikosti a umístění ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

### <a name="remarks"></a>Poznámky

Pouze podmnožinu příznaků *Windows dwStyle* jsou podporovány `CreateControl`:

- WS_VISIBLE Vytvoří okno, které je zpočátku viditelné. Povinné, pokud chcete, aby byl ovládací prvek viditelný okamžitě, jako běžná okna.

- WS_DISABLED Vytvoří okno, které je zpočátku zakázáno. Zakázané okno nemůže přijímat vstup od uživatele. Lze nastavit, pokud má ovládací prvek vlastnost Enabled.

- WS_BORDER Vytvoří okno s tenkým ohraničením. Lze nastavit, pokud má ovládací prvek vlastnost BorderStyle.

- WS_GROUP Určuje první ovládací prvek skupiny ovládacích prvků. Uživatel může pomocí směrových kláves změnit fokus klávesnice z jednoho ovládacího prvku ve skupině na další. Všechny ovládací prvky definované WS_GROUP stylu po prvním ovládacím prvku patří do stejné skupiny. Další ovládací prvek se stylem WS_GROUP ukončí skupinu a spustí další skupinu.

- WS_TABSTOP Určuje ovládací prvek, který může přijímat fokus klávesnice, když uživatel stiskne klávesu TAB. Stisknutím klávesy TAB se změní zaostření klávesnice na další ovládací prvek WS_TABSTOP stylu.

Druhé přetížení použijte k vytvoření ovládacích prvků výchozí velikosti.

## <a name="colecontrolcontainercreateolefont"></a><a name="createolefont"></a>COleControlContainer::CreateOleFont

Vytvoří písmo OLE.

```
void CreateOleFont(CFont* pFont);
```

### <a name="parameters"></a>Parametry

*písmo*<br/>
Ukazatel na písmo, které má být použito kontejnerem ovládacího prvku.

## <a name="colecontrolcontainerfinditem"></a><a name="finditem"></a>COleControlContainer::FindItem

Vyhledá vlastní web, který je hostitelem zadané položky.

```
virtual COleControlSite* FindItem(UINT nID) const;
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Identifikátor položky, která má být nalezena.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na vlastní web zadané položky.

## <a name="colecontrolcontainerfreezeallevents"></a><a name="freezeallevents"></a>COleControlContainer::FreezeAllEvents

Určuje, zda bude kontejner ignorovat události z připojených řídicích webů nebo je přijme.

```
void FreezeAllEvents(BOOL bFreeze);
```

### <a name="parameters"></a>Parametry

*bZmrazení*<br/>
Nenulová, pokud budou události zpracovány; jinak 0.

### <a name="remarks"></a>Poznámky

> [!NOTE]
> Ovládací prvek není nutné zastavit vypalování událostí, pokud je požadováno řídicí kontejner. Může pokračovat v spouštění, ale všechny následné události budou ignorovány kontejnerem ovládacího prvku.

## <a name="colecontrolcontainergetambientprop"></a><a name="getambientprop"></a>COleControlContainer::GetAmbientProp

Načte hodnotu zadané vlastnosti okolí.

```
virtual BOOL GetAmbientProp(
    COleControlSite* pSite,
    DISPID dispid,
    VARIANT* pvarResult);
```

### <a name="parameters"></a>Parametry

*p Site*<br/>
Ukazatel na lokalitu ovládacího prvku, ze kterého bude načtena vlastnost okolí.

*Dispid*<br/>
ID odeslání požadované vlastnosti okolí.

*výsledek varu*<br/>
Ukazatel na hodnotu vlastnosti ambient.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak 0.

## <a name="colecontrolcontainergetdlgitem"></a><a name="getdlgitem"></a>COleControlContainer::GetDlgItem

Načte ukazatel na zadaný ovládací prvek nebo podřízené okno v dialogovém okně nebo jiném okně.

```
virtual CWnd* GetDlgItem(int nID) const;

virtual void GetDlgItem(
    int nID,
    HWND* phWnd) const;
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Identifikátor položky dialogu, kterou chcete načíst.

*phWnd*<br/>
Ukazatel na úchyt objektu okna zadané položky dialogového okna.

### <a name="return-value"></a>Návratová hodnota

Ukazatel na okno položky dialogového okna.

## <a name="colecontrolcontainergetdlgitemint"></a><a name="getdlgitemint"></a>COleControlContainer::GetDlgItemInt

Načte hodnotu přeloženého textu daného ovládacího prvku.

```
virtual UINT GetDlgItemInt(
    int nID,
    BOOL* lpTrans,
    BOOL bSigned) const;
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Identifikátor ovládacího prvku.

*lpTrans*<br/>
Ukazatel na logickou proměnnou, která obdrží hodnotu úspěchu/neúspěchu funkce (PRAVDA označuje úspěch, FALSE označuje selhání).

*bPodepsáno*<br/>
Určuje, zda má funkce zkontrolovat text pro znaménko mínus na začátku a vrátit podepsanou čtyřčíselnou hodnotu, pokud ji najde. Pokud je parametr *bSigned* TRUE, zadání, že hodnota, která má být načtena, je podepsaná celá hodnota, přetypování vrácené hodnoty na typ **int.** Chcete-li získat rozšířené informace o chybě, volejte [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, proměnná odkazovaná *lpTrans* je nastavena na HODNOTU TRUE a vrácená hodnota je přeložená hodnota řídicího textu.

Pokud funkce selže, proměnná odkazovaná *lpTrans* je nastavena na HODNOTU FALSE a vrácená hodnota je nulová. Všimněte si, že vzhledem k tomu, že nula je možná přeložená hodnota, vrácená hodnota nula sama o sobě neznamená selhání.

Pokud *lpTrans* je NULL, funkce vrátí žádné informace o úspěchu nebo neúspěchu.

### <a name="remarks"></a>Poznámky

Funkce převede načtený text odstraněním všech mezer na začátku textu a převodem desetinných míst. Funkce zastaví překlad, když dosáhne konce textu nebo narazí na nečíselný znak.

Tato funkce vrátí nulu, pokud je přeložená hodnota větší než INT_MAX (pro podepsaná čísla) nebo UINT_MAX (pro nepodepsaná čísla).

## <a name="colecontrolcontainergetdlgitemtext"></a><a name="getdlgitemtext"></a>COleControlContainer::GetDlgItemText

Načte text daného ovládacího prvku.

```
virtual int GetDlgItemText(
    int nID,
    LPTSTR lpStr,
    int nMaxCount) const;
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Identifikátor ovládacího prvku.

*lpStr*<br/>
Ukazatel na text ovládacího prvku.

*nMaxCount*<br/>
Určuje maximální délku řetězce, na který má být zkopírován do vyrovnávací paměti, na kterou se vztahuje *lpStr*. Pokud délka řetězce překročí limit, řetězec je zkrácen.

### <a name="return-value"></a>Návratová hodnota

Pokud je funkce úspěšná, vrácená hodnota určuje počet znaků zkopírovaných do vyrovnávací paměti, bez ukončujícího znaku null.

Pokud funkce selže, vrácená hodnota je nula. Chcete-li získat rozšířené informace o chybě, volejte [GetLastError](/windows/win32/api/errhandlingapi/nf-errhandlingapi-getlasterror).

## <a name="colecontrolcontainerhandlesetfocus"></a><a name="handlesetfocus"></a>COleControlContainer::HandleSetFocus

Určuje, zda kontejner zpracovává WM_SETFOCUS zprávy.

```
virtual BOOL HandleSetFocus();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud kontejner zpracovává WM_SETFOCUS zprávy; jinak nula.

## <a name="colecontrolcontainerhandlewindowlessmessage"></a><a name="handlewindowlessmessage"></a>COleControlContainer::HandleWindowlessMessage

Zpracovává zprávy oken pro ovládací prvky bez oken.

```
virtual BOOL HandleWindowlessMessage(
    UINT message,
    WPARAM wParam,
    LPARAM lParam,
    LRESULT* plResult);
```

### <a name="parameters"></a>Parametry

*Zprávu*<br/>
Identifikátor zprávy okna poskytované systémem Windows.

*wParam*<br/>
Parametr zprávy; poskytované systémem Windows. Určuje další informace specifické pro zprávu. Obsah tohoto parametru závisí na hodnotě parametru *zprávy.*

*Lparam*<br/>
Parametr zprávy; poskytované systémem Windows. Určuje další informace specifické pro zprávu. Obsah tohoto parametru závisí na hodnotě parametru *zprávy.*

*plVýsledek*<br/>
Kód výsledků systému Windows. Určuje výsledek zpracování zprávy a závisí na odeslané zprávě.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je úspěšná; jinak nula.

### <a name="remarks"></a>Poznámky

Přepsat tuto funkci přizpůsobit zpracování zpráv ovládacího prvku bez oken.

## <a name="colecontrolcontainerisdlgbuttonchecked"></a><a name="isdlgbuttonchecked"></a>COleControlContainer::IsDlgButtonKontrolováno

Určuje stav zadaného tlačítka.

```
virtual UINT IsDlgButtonChecked(int nIDButton) const;
```

### <a name="parameters"></a>Parametry

*nIDButton*<br/>
Identifikátor ovládacího prvku tlačítka.

### <a name="return-value"></a>Návratová hodnota

Vrácená hodnota z tlačítka vytvořeného ve stylu BS_AUTOCHECKBOX, BS_AUTORADIOBUTTON, BS_AUTO3STATE, BS_CHECKBOX, BS_RADIOBUTTON nebo BS_3STATE. Může to být jedna z následujících možností:

- tlačítko BST_CHECKED je zaškrtnuto.

- tlačítko BST_INDETERMINATE je šedé, což označuje neurčitý stav (platí pouze v případě, že tlačítko má BS_3STATE nebo BS_AUTO3STATE styl).

- BST_UNCHECKED Button je vymazán.

### <a name="remarks"></a>Poznámky

Pokud je tlačítko třístavové ovládací prvek, členská funkce určuje, zda je šedě, zaškrtnuto nebo ani jedno.

## <a name="colecontrolcontainerm_crback"></a><a name="m_crback"></a>COleControlContainer::m_crBack

Barva pozadí kontejneru.

```
COLORREF m_crBack;
```

## <a name="colecontrolcontainerm_crfore"></a><a name="m_crfore"></a>COleControlContainer::m_crFore

Barva popředí kontejneru.

```
COLORREF m_crFore;
```

## <a name="colecontrolcontainerm_listsitesorwnds"></a><a name="m_listsitesorwnds"></a>COleControlContainer::m_listSitesOrWnds

Seznam řídicích webů hostovaných kontejnerem.

```
CTypedPtrList<CPtrList, COleControlSiteOrWnd*> m_listSitesOrWnds;
```

## <a name="colecontrolcontainerm_nwindowlesscontrols"></a><a name="m_nwindowlesscontrols"></a>COleControlContainer::m_nWindowlessControls

Počet ovládacích prvků bez oken hostovaných kontejneru ovládacího prvku.

```
int m_nWindowlessControls;
```

## <a name="colecontrolcontainerm_polefont"></a><a name="m_polefont"></a>COleControlContainer::m_pOleFont

Ukazatel na písmo OLE vlastního webu ovládacího prvku.

```
LPFONTDISP m_pOleFont;
```

## <a name="colecontrolcontainerm_psitecapture"></a><a name="m_psitecapture"></a>COleControlContainer::m_pSiteCapture

Ukazatel na lokalitu ovládacího prvku sběru.

```
COleControlSite* m_pSiteCapture;
```

## <a name="colecontrolcontainerm_psitefocus"></a><a name="m_psitefocus"></a>COleControlContainer::m_pSiteFocus

Ukazatel na lokalitu ovládacího prvku, která má aktuálně vstupní fokus.

```
COleControlSite* m_pSiteFocus;
```

## <a name="colecontrolcontainerm_psiteuiactive"></a><a name="m_psiteuiactive"></a>COleControlContainer::m_pSiteUIActive

Ukazatel na řídicí lokalitu, která je aktivována na místě.

```
COleControlSite* m_pSiteUIActive;
```

## <a name="colecontrolcontainerm_pwnd"></a><a name="m_pwnd"></a>COleControlContainer::m_pWnd

Ukazatel na objekt okna přidružený k kontejneru.

```
CWnd* m_pWnd;
```

## <a name="colecontrolcontainerm_sitemap"></a><a name="m_sitemap"></a>COleControlContainer::m_siteMap

Mapa webu.

```
CMapPtrToPtr m_siteMap;
```

## <a name="colecontrolcontaineronpaint"></a><a name="onpaint"></a>COleControlContainer::OnPaint

Volat rámci pro zpracování WM_PAINT požadavků.

```
virtual BOOL OnPaint(CDC* pDC);
```

### <a name="parameters"></a>Parametry

*Pdc*<br/>
Ukazatel na kontext zařízení používaný kontejnerem.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla zpráva zpracována; jinak nula.

### <a name="remarks"></a>Poznámky

Přepište tuto funkci a přizpůsobte proces malování.

## <a name="colecontrolcontaineronuiactivate"></a><a name="onuiactivate"></a>COleControlContainer::OnuiActivate

Volat rámci, když kontrolní lokality, na které se vztahuje *pSite*, se chystá být aktivován na místě.

```
virtual void OnUIActivate(COleControlSite* pSite);
```

### <a name="parameters"></a>Parametry

*p Site*<br/>
Ukazatel na řídicí web, který má být aktivován na místě.

### <a name="remarks"></a>Poznámky

Aktivace na místě znamená, že hlavní nabídka kontejneru je nahrazena složenou nabídkou na místě.

## <a name="colecontrolcontaineronuideactivate"></a><a name="onuideactivate"></a>COleControlContainer::OnUIDeactivate

Volat rámci při kontrolní lokality, na které se vztahuje *pSite*, se chystá deaktivovat.

```
virtual void OnUIDeactivate(COleControlSite* pSite);
```

### <a name="parameters"></a>Parametry

*p Site*<br/>
Ukazatel na řídicí web, který má být deaktivován.

### <a name="remarks"></a>Poznámky

Po přijetí tohoto oznámení by měl kontejner přeinstalovat své uživatelské rozhraní a zaměřit se.

## <a name="colecontrolcontainerscrollchildren"></a><a name="scrollchildren"></a>COleControlContainer::ScrollChildren

Volat rámci při posouvání zprávy jsou přijímány z podřízeného okna.

```
virtual void ScrollChildren(
    int dx,
    int dy);
```

### <a name="parameters"></a>Parametry

*Dx*<br/>
Množství posouvání podél osy x v obrazových bodech.

*dy*<br/>
Množství posouvání podél osy y v obrazových bodech.

## <a name="colecontrolcontainersenddlgitemmessage"></a><a name="senddlgitemmessage"></a>COleControlContainer::SendDlgItemMessage

Odešle zprávu zadanému ovládacímu prvku.

```
virtual LRESULT SendDlgItemMessage(
    int nID,
    UINT message,
    WPARAM wParam,
    LPARAM lParam);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Určuje identifikátor ovládacího prvku, který obdrží zprávu.

*Zprávu*<br/>
Určuje zprávu, která má být odeslána.

*wParam*<br/>
Určuje další informace specifické pro zprávu.

*Lparam*<br/>
Určuje další informace specifické pro zprávu.

## <a name="colecontrolcontainersetdlgitemint"></a><a name="setdlgitemint"></a>COleControlContainer::SetDlgItemInt

Nastaví text ovládacího prvku v dialogovém okně na řetězcovou reprezentaci zadané celé hodnoty.

```
virtual void SetDlgItemInt(
    int nID,
    UINT nValue,
    BOOL bSigned);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Identifikátor ovládacího prvku.

*nHodnota*<br/>
Celá hodnota, která má být zobrazena.

*bPodepsáno*<br/>
Určuje, zda je parametr *nValue* podepsán nebo nepodepsán. Pokud je tento parametr TRUE, *nValue* je podepsán. Pokud je tento parametr TRUE a *nValue* je menší než nula, je před první číslici řetězce umístěno znaménko mínus. Pokud je tento parametr FALSE, *nValue* je nepodepsaný.

## <a name="colecontrolcontainersetdlgitemtext"></a><a name="setdlgitemtext"></a>COleControlContainer::SetDlgItemText

Nastaví text zadaného ovládacího prvku pomocí textu obsaženého v *lpszString*.

```
virtual void SetDlgItemText(
    int nID,
    LPCTSTR lpszString);
```

### <a name="parameters"></a>Parametry

*Nid*<br/>
Identifikátor ovládacího prvku.

*lpszString*<br/>
Ukazatel na text ovládacího prvku.

## <a name="see-also"></a>Viz také

[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[COleControlSite – třída](../../mfc/reference/colecontrolsite-class.md)<br/>
[Třída COccManager](../../mfc/reference/coccmanager-class.md)
