---
title: "Třída COleControlContainer | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
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
dev_langs: C++
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
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c6d04faa904eba416b290515e5e6773ac6ef9837
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="colecontrolcontainer-class"></a>COleControlContainer – třída
Funguje jako kontejneru ovládacího prvku pro ovládací prvky ActiveX.  
  
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
|[COleControlContainer::AttachControlSite](#attachcontrolsite)|Vytvoří řízení lokality, hostitelem kontejneru.|  
|[COleControlContainer::BroadcastAmbientPropertyChange](#broadcastambientpropertychange)|Informuje o všechny hostované ovládacích prvků, které se změnila vedlejší vlastnost.|  
|[COleControlContainer::CheckDlgButton](#checkdlgbutton)|Upravuje zadané tlačítko – ovládací prvek.|  
|[COleControlContainer::CheckRadioButton](#checkradiobutton)|Vybere zadaný přepínač skupiny.|  
|[COleControlContainer::CreateControl](#createcontrol)|Vytvoří hostované ovládací prvek ActiveX.|  
|[COleControlContainer::CreateOleFont](#createolefont)|Vytvoří OLE písma.|  
|[COleControlContainer::FindItem](#finditem)|Vrátí vlastní stránka daný ovládací prvek.|  
|[COleControlContainer::FreezeAllEvents](#freezeallevents)|Určuje, pokud řízení lokality přijímá události.|  
|[COleControlContainer::GetAmbientProp](#getambientprop)|Načte zadaný vedlejší vlastnost.|  
|[COleControlContainer::GetDlgItem](#getdlgitem)|Načte zadaný dialogovém okně ovládacího prvku.|  
|[COleControlContainer::GetDlgItemInt](#getdlgitemint)|Načte hodnotu zadaného dialogovém okně ovládacího prvku.|  
|[COleControlContainer::GetDlgItemText](#getdlgitemtext)|Načte popisek ovládacího prvku zadaný dialogové okno.|  
|[COleControlContainer::HandleSetFocus](#handlesetfocus)|Určuje, pokud kontejner zpracovává `WM_SETFOCUS` zprávy.|  
|[COleControlContainer::HandleWindowlessMessage](#handlewindowlessmessage)|Zpracovává zprávy odeslané do ovládacího prvku bez oken.|  
|[COleControlContainer::IsDlgButtonChecked](#isdlgbuttonchecked)|Určuje stav dané tlačítko.|  
|[COleControlContainer::OnPaint](#onpaint)|Voláno k překreslit část kontejneru.|  
|[COleControlContainer::OnUIActivate](#onuiactivate)|Voláno, pokud je ovládací prvek bude aktivován na místě.|  
|[COleControlContainer::OnUIDeactivate](#onuideactivate)|Volá se při ovládacího prvku je deaktivovat.|  
|[COleControlContainer::ScrollChildren](#scrollchildren)|Voláno rámcem při přijímání zprávy scroll z podřízeného okna.|  
|[COleControlContainer::SendDlgItemMessage](#senddlgitemmessage)|Odešle zprávu do zadané ovládacího prvku.|  
|[COleControlContainer::SetDlgItemInt](#setdlgitemint)|Nastaví hodnotu zadaného prvku.|  
|[COleControlContainer::SetDlgItemText](#setdlgitemtext)|Nastaví text zadaný ovládacího prvku.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[COleControlContainer::m_crBack](#m_crback)|Barva pozadí kontejneru.|  
|[COleControlContainer::m_crFore](#m_crfore)|Barvu popředí kontejneru.|  
|[COleControlContainer::m_listSitesOrWnds](#m_listsitesorwnds)|Seznam podporovaných řízení lokality.|  
|[COleControlContainer::m_nWindowlessControls](#m_nwindowlesscontrols)|Počet prvků hostované bez oken.|  
|[COleControlContainer::m_pOleFont](#m_polefont)|Ukazatel na písmo OLE vlastního ovládacího prvku lokality.|  
|[COleControlContainer::m_pSiteCapture](#m_psitecapture)|Ukazatel na ovládací prvek webu zachycení.|  
|[COleControlContainer::m_pSiteFocus](#m_psitefocus)|Ukazatel na ovládací prvek, který má aktuálně vstupu fokus.|  
|[COleControlContainer::m_pSiteUIActive](#m_psiteuiactive)|Ukazatel na ovládací prvek, který je aktuálně aktivaci.|  
|[COleControlContainer::m_pWnd](#m_pwnd)|Ukazatel na okno implementace kontejneru ovládacího prvku.|  
|[COleControlContainer::m_siteMap](#m_sitemap)|Mapy webu.|  
  
## <a name="remarks"></a>Poznámky  
 To se provádí prostřednictvím podpory pro jednu nebo více lokalit ovládacího prvku ActiveX (implementované `COleControlSite`). `COleControlContainer`plně implementuje [IOleInPlaceFrame](http://msdn.microsoft.com/library/windows/desktop/ms692770) a [IOleContainer](http://msdn.microsoft.com/library/windows/desktop/ms690103) rozhraní, povolení obsažené ovládacích prvků ActiveX ke splnění jejich kvalifikaci jako položky na místě.  
  
 Běžně, tato třída se používá ve spojení s `COccManager` a `COleControlSite` implementovat vlastní kontejneru ovládacího prvku ActiveX, s vlastní weby pro jednu nebo více ovládacích prvků ActiveX.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleControlContainer`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxocc.h  
  
##  <a name="attachcontrolsite"></a>COleControlContainer::AttachControlSite  
 Voláno rámcem a vytvořte ovládacího prvku lokality.  
  
```  
virtual void AttachControlSite(
    CWnd* pWnd,  
    UINT nIDC = 0);

 
void AttachControlSite(
    CWnd* pWnd,  
    UINT nIDC = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Ukazatel na `CWnd` objektu.  
  
 `nIDC`  
 ID ovládacího prvku na připojit.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce přepsání, pokud chcete přizpůsobit tohoto procesu.  
  
> [!NOTE]
>  Pokud se staticky připojujete ke knihovně MFC, použijte první formulář této funkce. Vytváříte-li dynamicky propojení do knihovny MFC, použijte druhý formulář.  
  
##  <a name="broadcastambientpropertychange"></a>COleControlContainer::BroadcastAmbientPropertyChange  
 Informuje o všechny hostované ovládacích prvků, které se změnila vedlejší vlastnost.  
  
```  
virtual void BroadcastAmbientPropertyChange(DISPID dispid);
```  
  
### <a name="parameters"></a>Parametry  
 `dispid`  
 Odesílání ID vedlejší vlastnost mění.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce je volána rámcem při vedlejší vlastnost změnil hodnotu. Chcete-li přizpůsobit toto chování funkci přepište.  
  
##  <a name="checkdlgbutton"></a>COleControlContainer::CheckDlgButton  
 Upravuje aktuální stav tlačítko.  
  
```  
virtual void CheckDlgButton(
    int nIDButton,  
    UINT nCheck);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDButton`  
 ID na tlačítko Upravit.  
  
 `nCheck`  
 Určuje stav tlačítko. Může být jedna z následujících akcí:  
  
- **BST_CHECKED** nastaví stav tlačítka zaškrtnuté.  
  
- **BST_INDETERMINATE** nastaví stav tlačítka šedým, která určuje neurčitém stavu. Tuto hodnotu použijte pouze v případě na tlačítko **bs_3state –** nebo **bs_auto3state –** stylu.  
  
- **BST_UNCHECKED** nastaví stav tlačítka nezaškrtnuté.  
  
##  <a name="checkradiobutton"></a>COleControlContainer::CheckRadioButton  
 Vybere zadaný přepínače ve skupině a vymaže zbývající tlačítka ve skupině.  
  
```  
virtual void CheckRadioButton(
    int nIDFirstButton,  
    int nIDLastButton,  
    int nIDCheckButton);
```  
  
### <a name="parameters"></a>Parametry  
 `nIDFirstButton`  
 Určuje identifikátor první přepínače ve skupině.  
  
 `nIDLastButton`  
 Určuje identifikátor poslední přepínače ve skupině.  
  
 `nIDCheckButton`  
 Určuje identifikátor přepínač ke kontrole.  
  
##  <a name="colecontrolcontainer"></a>COleControlContainer::COleControlContainer  
 Vytvoří `COleControlContainer` objektu.  
  
```  
explicit COleControlContainer(CWnd* pWnd);
```  
  
### <a name="parameters"></a>Parametry  
 `pWnd`  
 Ukazatel do nadřazeného okna kontejneru ovládacího prvku.  
  
### <a name="remarks"></a>Poznámky  
 Po úspěšném vytvoření objektu přidání vlastního ovládacího prvku serveru pomocí volání `AttachControlSite`.  
  
##  <a name="createcontrol"></a>COleControlContainer::CreateControl  
 Vytvoří ovládacího prvku ActiveX hostované zadaný `COleControlSite` objektu.  
  
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
 `pWndCtrl`  
 Ukazatel na okno objekt reprezentující ovládacího prvku.  
  
 `clsid`  
 ID jedinečný třídy ovládacího prvku.  
  
 `lpszWindowName`  
 Ukazatel na text, který se zobrazí v ovládacím prvku. Nastaví hodnotu vlastnosti ovládacího prvku popisek nebo Text (pokud existuje). Pokud **NULL**, popisek nebo Text ovládacího prvku se nezmění.  
  
 `dwStyle`  
 Styly systému Windows. Styly k dispozici jsou uvedeny v seznamu **poznámky** části.  
  
 `rect`  
 Určuje velikost a umístění ovládacího prvku. Může být buď `CRect` objekt nebo `RECT` struktury.  
  
 `nID`  
 Určuje ID ovládacího prvku podřízené okno.  
  
 `pPersist`  
 Ukazatel na `CFile` obsahující trvalý stav pro ovládací prvek. Výchozí hodnota je **NULL**, která určuje, že ovládací prvek se inicializuje bez obnovení stavu z jakékoli trvalé úložiště. Není-li **NULL**, by mělo být ukazatel na `CFile`-odvozené objekt, který obsahuje trvalé data ovládacího prvku ve formě datového proudu nebo úložiště. Tato data by byla uložena v předchozí aktivace klienta. `CFile` Může obsahovat další data, ale musí mít jeho ukazatele pro čtení a zápis nastavit do prvního bajtu trvalé dat při volání `CreateControl`.  
  
 `bStorage`  
 Určuje, zda data v `pPersist` by měl být interpretován jako `IStorage` nebo `IStream` data. Pokud data v `pPersist` je úložiště, `bStorage` by měla být **TRUE**. Pokud data v `pPersist` je datový proud, `bStorage` by měla být **FALSE**. Výchozí hodnota je **FALSE**.  
  
 `bstrLicKey`  
 Volitelné licence klíčová data. Tato data je potřeba pouze při vytváření ovládacích prvků, které vyžadují spuštění licenční klíč. Pokud ovládací prvek podporuje licencování, je nutné zadat licenční klíč pro vytvoření ovládacího prvku proběhla úspěšně. Výchozí hodnota je **NULL**.  
  
 *ppNewSite*  
 Ukazatele na existující web ovládací prvek, který bude hostitelem ovládacího prvku vytváří. Výchozí hodnota je **NULL**, indikující, nové řízení lokality bude automaticky vytvořen a připojený k nové ovládací prvek.  
  
 `ppt`  
 Ukazatel **bodu** struktura, která obsahuje levém horním rohu ovládacího prvku. Velikost ovládacího prvku je dáno hodnotu *psize*. `ppt` a *psize* hodnoty jsou volitelné metodu zadávání velikost a umístění ovládacího prvku.  
  
 *psize*  
 Ukazatel **velikost** struktura, která obsahuje velikosti ovládacího prvku. Levém horním rohu je dáno hodnotu `ppt`. `ppt` a *psize* hodnoty jsou volitelné metodu zadávání velikost a umístění ovládacího prvku.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Pouze podmnožinu Windows `dwStyle` příznaky podporuje `CreateControl`:  
  
- **Ws_visible –** vytvoří okno, které je původně viditelná. Vyžaduje, pokud chcete ovládat viditelné okamžitě, stejně jako obyčejnou windows.  
  
- **Ws_disabled –** vytvoří okno, které je původně zakázána. Okno zakázané nemůže přijímat vstup od uživatele. Můžete nastavit, pokud má vlastnost povoleno ovládacího prvku.  
  
- `WS_BORDER`Vytvoří okno se dynamicky čáry ohraničení. Můžete nastavit, pokud má vlastnost styl okraje na ovládací prvek.  
  
- **Ws_group –** Určuje první prvek skupiny ovládacích prvků. Uživatel může změnit fokus klávesnice z jednoho ovládacího prvku ve skupině na další pomocí klíčů směr. Všechny ovládací prvky, které jsou definované pomocí **ws_group –** styl po první prvek patří do stejné skupiny. Na další ovládací prvek s **ws_group –** styl končí skupině a spustí na další skupinu.  
  
- **Ws_tabstop –** určuje ovládací prvek, který může získat fokus klávesnice, při stisknutí klávesy TAB. Stisknutím klávesy TAB změní fokus klávesnice na další ovládací prvek z **ws_tabstop –** stylu.  
  
 Chcete-li vytvořit výchozí velikosti ovládacích prvků, použijte druhý přetížení.  
  
##  <a name="createolefont"></a>COleControlContainer::CreateOleFont  
 Vytvoří OLE písma.  
  
```  
void CreateOleFont(CFont* pFont);
```  
  
### <a name="parameters"></a>Parametry  
 `pFont`  
 Ukazatel na písma, který má být používána kontejneru ovládacího prvku.  
  
##  <a name="finditem"></a>COleControlContainer::FindItem  
 Vyhledá vlastní web, který je hostitelem zadanou položku.  
  
```  
virtual COleControlSite* FindItem(UINT nID) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 Identifikátor položky, která se má najít.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na vlastní web zadané položky.  
  
##  <a name="freezeallevents"></a>COleControlContainer::FreezeAllEvents  
 Určuje, zda kontejner bude ignorovat události z připojených řízení webů, nebo přijměte je.  
  
```  
void FreezeAllEvents(BOOL bFreeze);
```  
  
### <a name="parameters"></a>Parametry  
 `bFreeze`  
 Nenulové hodnoty v případě, že události budou zpracovány; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Ovládací prvek není potřeba zastavit aktivaci událostí, pokud požadoval kontejneru ovládacího prvku. Pálení může pokračovat, ale všechny následné události budou ignorovány podle kontejneru ovládacího prvku.  
  
##  <a name="getambientprop"></a>COleControlContainer::GetAmbientProp  
 Načte hodnotu zadaného vedlejším vlastnosti.  
  
```  
virtual BOOL GetAmbientProp(
    COleControlSite* pSite,  
    DISPID dispid,  
    VARIANT* pvarResult);
```  
  
### <a name="parameters"></a>Parametry  
 `pSite`  
 Ukazatel na řízení lokality, ze kterého bude načten vedlejší vlastnost.  
  
 `dispid`  
 Odesílání ID požadované vedlejší vlastnost.  
  
 *pVarResult*  
 Ukazatel na hodnotu vedlejším vlastnosti.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
##  <a name="getdlgitem"></a>COleControlContainer::GetDlgItem  
 Načte ukazatel na vybrané okno nebo podřízený ovládací prvek v dialogovém okně nebo jiné okno.  
  
```  
virtual CWnd* GetDlgItem(int nID) const;  
  
virtual void GetDlgItem(
    int nID,  
    HWND* phWnd) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 Identifikátor položky dialogové okno načíst.  
  
 `phWnd`  
 Ukazatel na popisovač objektu okna dialogové okno zadané položky.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na položce dialogovém okně.  
  
##  <a name="getdlgitemint"></a>COleControlContainer::GetDlgItemInt  
 Načte hodnotu přeložený text daného ovládacího prvku.  
  
```  
virtual UINT GetDlgItemInt(
    int nID,  
    BOOL* lpTrans,  
    BOOL bSigned) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 Identifikátor ovládacího prvku.  
  
 `lpTrans`  
 Ukazatel na logická hodnota proměnné, která obdrží hodnotu úspěch nebo selhání funkce ( **TRUE** označuje úspěch, **FALSE** označuje selhání).  
  
 `bSigned`  
 Určuje, zda by měl funkce zkontrolujte text pro znaménkem minus na začátku a vrátit hodnotu číslo se znaménkem, pokud jej nalezne. Pokud `bSigned` parametr **TRUE**, návratovou hodnotu k určení, že je hodnota, která má být načtena hodnota číslo se znaménkem přetypovat `int` typu. Chcete-li získat rozšířené informace o chybě, volejte [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360).  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud úspěšné, proměnnou ukazující na `lpTrans` je nastaven na **TRUE**, a návratovou hodnotu je přeložená hodnota ovládací prvek text.  
  
 V případě selhání funkce proměnnou na kterou odkazuje `lpTrans` je nastaven na **FALSE**, a návratovou hodnotu 0. Všimněte si, že možná hodnota přeložený totiž nula návratovou hodnotu nula samostatně neindikuje selhání.  
  
 Pokud `lpTrans` je **NULL**, funkce vrátí hodnotu žádné informace o úspěchu nebo neúspěchu.  
  
### <a name="remarks"></a>Poznámky  
 Funkce překládá načtený text odstraňování žádné mezery na začátku textu a potom převést desetinných míst. Funkce zastaví překladu, pokud dosáhne konce text nebo zaznamená znak číselného typu.  
  
 Funkce vrátí hodnotu nula. Pokud je přeložená hodnota větší než **INT_MAX** (pro podepsané čísla) nebo **uint_max –** (pro bez znaménka čísla).  
  
##  <a name="getdlgitemtext"></a>COleControlContainer::GetDlgItemText  
 Načte text daného ovládacího prvku.  
  
```  
virtual int GetDlgItemText(
    int nID,  
    LPTSTR lpStr,  
    int nMaxCount) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 Identifikátor ovládacího prvku.  
  
 `lpStr`  
 Ukazatel na text ovládacího prvku.  
  
 `nMaxCount`  
 Určuje maximální délku znaků řetězce, který se má zkopírovat do vyrovnávací paměti, na kterou odkazuje `lpStr`. Pokud délka řetězce překračuje limit, se zkrátí řetězec.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud funkci úspěšné, návratová hodnota určuje počet znaků, které jsou zkopírovány do vyrovnávací paměti není včetně ukončující znak hodnoty null.  
  
 Pokud funkce selže, je vrácenou hodnotu nula. Chcete-li získat rozšířené informace o chybě, volejte [GetLastError](http://msdn.microsoft.com/library/windows/desktop/ms679360).  
  
##  <a name="handlesetfocus"></a>COleControlContainer::HandleSetFocus  
 Určuje, pokud kontejner zpracovává `WM_SETFOCUS` zprávy.  
  
```  
virtual BOOL HandleSetFocus();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud kontejner zpracovává `WM_SETFOCUS` zprávy; jinak hodnota nula.  
  
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
 `message`  
 Identifikátor pro zpráv oken, obsažené v systému Windows.  
  
 `wParam`  
 Parametr zprávy; obsažené v systému Windows. Určuje další informace specifické pro zprávy. Obsah tohoto parametru je závislý na hodnotě `message` parametr.  
  
 `lParam`  
 Parametr zprávy; obsažené v systému Windows. Určuje další informace specifické pro zprávy. Obsah tohoto parametru je závislý na hodnotě `message` parametr.  
  
 *plResult*  
 Kód výsledku systému Windows. Určuje výsledek zpracování zprávy a závisí na zprávy odeslané.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
 Přepsání této funkci můžete přizpůsobit zpracování zprávy bez oken ovládacího prvku.  
  
##  <a name="isdlgbuttonchecked"></a>COleControlContainer::IsDlgButtonChecked  
 Určuje stav dané tlačítko.  
  
```  
virtual UINT IsDlgButtonChecked(int nIDButton) const;  
```  
  
### <a name="parameters"></a>Parametry  
 `nIDButton`  
 Identifikátor ovládacího prvku tlačítko.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrácená hodnota z tlačítko vytvořené pomocí **bs_autocheckbox –**, **bs_autoradiobutton –**, **bs_auto3state –**, **bs_checkbox –**, **Bs_radiobutton –**, nebo **bs_3state –** stylu. Může být jedna z následujících akcí:  
  
- **BST_CHECKED** zaškrtnutí tlačítka.  
  
- **BST_INDETERMINATE** neaktivní tlačítko označující neurčitém stavu (platí jenom v případě, že má tlačítko **bs_3state –** nebo **bs_auto3state –** styl).  
  
- **BST_UNCHECKED** je tlačítko Vymazat.  
  
### <a name="remarks"></a>Poznámky  
 Pokud tlačítko ovládacího prvku tří stavů, – členská funkce určuje, zda jej není k dispozici, zaškrtnuto, nebo žádný z nich.  
  
##  <a name="m_crback"></a>COleControlContainer::m_crBack  
 Barva pozadí kontejneru.  
  
```  
COLORREF m_crBack;  
```  
  
##  <a name="m_crfore"></a>COleControlContainer::m_crFore  
 Barvu popředí kontejneru.  
  
```  
COLORREF m_crFore;  
```  
  
##  <a name="m_listsitesorwnds"></a>COleControlContainer::m_listSitesOrWnds  
 Seznam řízení hostovaném službou kontejneru.  
  
```  
CTypedPtrList<CPtrList, COleControlSiteOrWnd*> m_listSitesOrWnds;  
```  
  
##  <a name="m_nwindowlesscontrols"></a>COleControlContainer::m_nWindowlessControls  
 Počet prvků bez oken hostitelem kontejneru ovládacího prvku.  
  
```  
int m_nWindowlessControls;  
```  
  
##  <a name="m_polefont"></a>COleControlContainer::m_pOleFont  
 Ukazatel na písmo OLE vlastního ovládacího prvku lokality.  
  
```  
LPFONTDISP m_pOleFont;  
```  
  
##  <a name="m_psitecapture"></a>COleControlContainer::m_pSiteCapture  
 Ukazatel na ovládací prvek webu zachycení.  
  
```  
COleControlSite* m_pSiteCapture;  
```  
  
##  <a name="m_psitefocus"></a>COleControlContainer::m_pSiteFocus  
 Ukazatel na řízení lokality, která má aktuálně vstupu fokus.  
  
```  
COleControlSite* m_pSiteFocus;  
```  
  
##  <a name="m_psiteuiactive"></a>COleControlContainer::m_pSiteUIActive  
 Ukazatel na řízení lokality, která je aktivován na místě.  
  
```  
COleControlSite* m_pSiteUIActive;  
```  
  
##  <a name="m_pwnd"></a>COleControlContainer::m_pWnd  
 Ukazatel na objekt okna přidružené kontejneru.  
  
```  
CWnd* m_pWnd;  
```  
  
##  <a name="m_sitemap"></a>COleControlContainer::m_siteMap  
 Mapy webu.  
  
```  
CMapPtrToPtr m_siteMap;  
```  
  
##  <a name="onpaint"></a>COleControlContainer::OnPaint  
 Voláno rámcem pro zpracování `WM_PAINT` požadavky.  
  
```  
virtual BOOL OnPaint(CDC* pDC);
```  
  
### <a name="parameters"></a>Parametry  
 `pDC`  
 Ukazatel na kontext zařízení používá kontejneru.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty, pokud bylo zpracováno zprávy; jinak hodnota nula.  
  
### <a name="remarks"></a>Poznámky  
 Funkci k přizpůsobení procesu Malování přepište.  
  
##  <a name="onuiactivate"></a>COleControlContainer::OnUIActivate  
 Voláno rámcem při řízení lokality, na kterou odkazuje `pSite`, má být aktivována na místě.  
  
```  
virtual void OnUIActivate(COleControlSite* pSite);
```  
  
### <a name="parameters"></a>Parametry  
 `pSite`  
 Ukazatel na webu ovládací prvek bude aktivován na místě.  
  
### <a name="remarks"></a>Poznámky  
 Aktivace na místě, znamená to, přejděte z hlavní nabídky kontejneru se nahradí složené nabídky místní.  
  
##  <a name="onuideactivate"></a>COleControlContainer::OnUIDeactivate  
 Voláno rámcem při řízení lokality, na kterou odkazuje `pSite`, je deaktivovat.  
  
```  
virtual void OnUIDeactivate(COleControlSite* pSite);
```  
  
### <a name="parameters"></a>Parametry  
 `pSite`  
 Ukazatel na řízení lokality se deaktivovat.  
  
### <a name="remarks"></a>Poznámky  
 Po přijetí tohoto oznámení by měl kontejner přeinstalujte svoje uživatelské rozhraní a zaměřit.  
  
##  <a name="scrollchildren"></a>COleControlContainer::ScrollChildren  
 Voláno rámcem při přijímání zprávy scroll z podřízeného okna.  
  
```  
virtual void ScrollChildren(
    int dx,  
    int dy);
```  
  
### <a name="parameters"></a>Parametry  
 `dx`  
 Množství, v pixelech posouvání podél osy x.  
  
 *dy*  
 Množství, v pixelech posouvání podél osy y.  
  
##  <a name="senddlgitemmessage"></a>COleControlContainer::SendDlgItemMessage  
 Odešle zprávu do zadané ovládacího prvku.  
  
```  
virtual LRESULT SendDlgItemMessage(
    int nID,  
    UINT message,  
    WPARAM wParam,  
    LPARAM lParam);
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 Určuje identifikátor ovládací prvek, který obdrží zprávu.  
  
 `message`  
 Určuje zprávu, která k odeslání.  
  
 `wParam`  
 Určuje další informace specifické pro zprávy.  
  
 `lParam`  
 Určuje další informace specifické pro zprávy.  
  
##  <a name="setdlgitemint"></a>COleControlContainer::SetDlgItemInt  
 Nastaví text ovládacího prvku v dialogovém okně pro řetězcovou reprezentaci zadané celočíselné hodnoty.  
  
```  
virtual void SetDlgItemInt(
    int nID,  
    UINT nValue,  
    BOOL bSigned);
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 Identifikátor ovládacího prvku.  
  
 `nValue`  
 Celočíselná hodnota, který se má zobrazit.  
  
 `bSigned`  
 Určuje, zda `nValue` parametr je podepsaný nebo bez znaménka. Pokud tento parametr je **TRUE**, `nValue` je podepsaný. Pokud tento parametr je **TRUE** a `nValue` je menší než nula, minus přihlášení je umístěna před první číslice v řetězci. Pokud tento parametr je **FALSE**, `nValue` není podepsaný.  
  
##  <a name="setdlgitemtext"></a>COleControlContainer::SetDlgItemText  
 Nastaví text zadaný ovládací prvek text součástí s použitím `lpszString`.  
  
```  
virtual void SetDlgItemText(
    int nID,  
    LPCTSTR lpszString);
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 Identifikátor ovládacího prvku.  
  
 `lpszString`  
 Ukazatel na text ovládacího prvku.  
  
## <a name="see-also"></a>Viz také  
 [CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [COleControlSite – třída](../../mfc/reference/colecontrolsite-class.md)   
 [COccManager – třída](../../mfc/reference/coccmanager-class.md)
