---
title: "Třída COlePropertyPage | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COlePropertyPage
- AFXCTL/COlePropertyPage
- AFXCTL/COlePropertyPage::COlePropertyPage
- AFXCTL/COlePropertyPage::GetControlStatus
- AFXCTL/COlePropertyPage::GetObjectArray
- AFXCTL/COlePropertyPage::GetPageSite
- AFXCTL/COlePropertyPage::OVERWRITEApply
- AFXCTL/COlePropertyPage::IsModified
- AFXCTL/COlePropertyPage::OnEditProperty
- AFXCTL/COlePropertyPage::OnHelp
- AFXCTL/COlePropertyPage::OnInitDialog
- AFXCTL/COlePropertyPage::OnObjectsChanged
- AFXCTL/COlePropertyPage::OnSetPageSite
- AFXCTL/COlePropertyPage::SetControlStatus
- AFXCTL/COlePropertyPage::SetDialogResource
- AFXCTL/COlePropertyPage::SetHelpInfo
- AFXCTL/COlePropertyPage::SetModifiedFlag
- AFXCTL/COlePropertyPage::SetPageName
dev_langs: C++
helpviewer_keywords:
- COlePropertyPage [MFC], COlePropertyPage
- COlePropertyPage [MFC], GetControlStatus
- COlePropertyPage [MFC], GetObjectArray
- COlePropertyPage [MFC], GetPageSite
- COlePropertyPage [MFC], IgnoreApply
- COlePropertyPage [MFC], IsModified
- COlePropertyPage [MFC], OnEditProperty
- COlePropertyPage [MFC], OnHelp
- COlePropertyPage [MFC], OnInitDialog
- COlePropertyPage [MFC], OnObjectsChanged
- COlePropertyPage [MFC], OnSetPageSite
- COlePropertyPage [MFC], SetControlStatus
- COlePropertyPage [MFC], SetDialogResource
- COlePropertyPage [MFC], SetHelpInfo
- COlePropertyPage [MFC], SetModifiedFlag
- COlePropertyPage [MFC], SetPageName
ms.assetid: e9972872-8e6b-4550-905e-d36a274d64dc
caps.latest.revision: "23"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 19ed15a5245712933ec43daabc5444160e5eeb95
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="colepropertypage-class"></a>COlePropertyPage – třída
Slouží k zobrazení vlastností vlastního ovládacího prvku v grafickém rozhraní, podobně jako dialogové okno.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class AFX_NOVTABLE COlePropertyPage : public CDialog  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[COlePropertyPage::COlePropertyPage](#colepropertypage)|Vytvoří `COlePropertyPage` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COlePropertyPage::GetControlStatus](#getcontrolstatus)|Určuje, zda má uživatel změnil hodnotu v ovládacím prvku.|  
|[COlePropertyPage::GetObjectArray](#getobjectarray)|Vrátí pole objektů upravován stránku vlastností.|  
|[COlePropertyPage::GetPageSite](#getpagesite)|Vrací ukazatel na stránce vlastností `IPropertyPageSite` rozhraní.|  
|[COlePropertyPage::IgnoreApply](#ignoreapply)|Určuje, jaké ovládací prvky nepovolujte na tlačítko použít.|  
|[COlePropertyPage::IsModified](#ismodified)|Určuje, zda má uživatel změnil její stránku vlastností.|  
|[COlePropertyPage::OnEditProperty](#oneditproperty)|Voláno rámcem, když uživatel upravuje vlastnost.|  
|[COlePropertyPage::OnHelp](#onhelp)|Voláno rámcem, pokud uživatel vyvolá nápovědy.|  
|[COlePropertyPage::OnInitDialog](#oninitdialog)|Voláno rámcem při inicializaci stránku vlastností.|  
|[COlePropertyPage::OnObjectsChanged](#onobjectschanged)|Voláno rámcem při výběru jiného ovládacího prvku OLE, novými vlastnostmi.|  
|[COlePropertyPage::OnSetPageSite](#onsetpagesite)|Voláno rámcem, pokud vlastnost rámečku poskytuje stránky webu.|  
|[COlePropertyPage::SetControlStatus](#setcontrolstatus)|Nastaví příznak označující, zda má uživatel změnil hodnotu v ovládacím prvku.|  
|[COlePropertyPage::SetDialogResource](#setdialogresource)|Nastaví její stránku vlastností prostředku dialogového okna.|  
|[COlePropertyPage::SetHelpInfo](#sethelpinfo)|Nastaví její stránku vlastností stručný nápovědy text, název souboru jeho nápovědy a jeho kontextové nápovědy.|  
|[COlePropertyPage::SetModifiedFlag](#setmodifiedflag)|Nastaví příznak označující, zda má uživatel změnil její stránku vlastností.|  
|[COlePropertyPage::SetPageName](#setpagename)|Nastaví název stránky vlastností (záhlaví).|  
  
## <a name="remarks"></a>Poznámky  
 Stránky vlastností může zahrnovat textové pole, která umožňuje uživatelům zobrazit a upravit vlastnosti titulku ovládacího prvku.  
  
 Každou vlastnost vlastní nebo uložených řízení může mít ovládacího prvku dialogu, který umožňuje uživatelům ovládacího prvku zobrazení aktuální hodnota vlastnosti a v případě potřeby změňte tuto hodnotu.  
  
 Další informace o používání `COlePropertyPage`, najdete v článku [– ovládací prvky ActiveX: stránky vlastností](../../mfc/mfc-activex-controls-property-pages.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 [CWnd](../../mfc/reference/cwnd-class.md)  
  
 [CDialog](../../mfc/reference/cdialog-class.md)  
  
 `COlePropertyPage`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxctl.h  
  
##  <a name="colepropertypage"></a>COlePropertyPage::COlePropertyPage  
 Vytvoří `COlePropertyPage` objektu.  
  
```  
COlePropertyPage(
    UINT idDlg,  
    UINT idCaption);
```  
  
### <a name="parameters"></a>Parametry  
 *idDlg*  
 ID prostředku šablony dialogového okna.  
  
 *idCaption*  
 ID prostředku titulek její stránku vlastností.  
  
### <a name="remarks"></a>Poznámky  
 Při implementaci podtřídou třídy `COlePropertyPage`, měli používat vaše podtřída konstruktor `COlePropertyPage` konstruktor k identifikaci prostředku šablony dialogového okna na která je založena na stránku vlastností a prostředek řetězec obsahující titulek.  
  
##  <a name="getcontrolstatus"></a>COlePropertyPage::GetControlStatus  
 Určuje, zda má uživatel změnil hodnotu ovládací prvek stránku vlastností s číslem ID zadaný prostředek.  
  
```  
BOOL GetControlStatus(UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 ID prostředku ovládací prvek stránky vlastností.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud hodnota ovládacího prvku byl upravený; jinak hodnota **FALSE**.  
  
##  <a name="getobjectarray"></a>COlePropertyPage::GetObjectArray  
 Vrátí pole objektů upravován stránku vlastností.  
  
```  
LPDISPATCH* GetObjectArray(ULONG* pnObjects);
```  
  
### <a name="parameters"></a>Parametry  
 `pnObjects`  
 Ukazatel na celé číslo bez znaménka dlouhý, která bude přijímat počet objektů upravovaný stránkou.  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatele na pole `IDispatch` ukazatele, které se používají pro přístup k vlastnostem každý ovládací prvek na stránce vlastností. Volající nesmí uvolnit tyto ukazatele rozhraní.  
  
### <a name="remarks"></a>Poznámky  
 Každou vlastnost objektu page udržuje ukazatele na pole `IDispatch` rozhraní objektů upravovaný stránkou. Tato funkce nastaví jeho `pnObjects` argument počet elementů v tomto poli a vrací ukazatel na první prvek pole.  
  
##  <a name="getpagesite"></a>COlePropertyPage::GetPageSite  
 Získá ukazatel na stránce vlastností `IPropertyPageSite` rozhraní.  
  
```  
LPPROPERTYPAGESITE GetPageSite();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Ukazatel na stránce vlastností `IPropertyPageSite` rozhraní.  
  
### <a name="remarks"></a>Poznámky  
 Ovládací prvky a kontejnery spolupracují, aby uživatelé mohli procházet a úpravy vlastností ovládacích prvků. Ovládací prvek poskytuje stránky vlastností, z nichž každý je OLE objekt, který umožňuje uživateli upravit související sadu vlastností. Kontejner obsahuje vlastnost rámce, který zobrazuje stránky vlastností. Pro každou stránku rámečku vlastnost poskytuje lokalitě stránky, která podporuje `IPropertyPageSite` rozhraní.  
  
##  <a name="ignoreapply"></a>COlePropertyPage::IgnoreApply  
 Určuje, jaké ovládací prvky nepovolujte na tlačítko použít.  
  
```  
void IgnoreApply(UINT nID);
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 ID ovládacího prvku, který se má ignorovat.  
  
### <a name="remarks"></a>Poznámky  
 Stránka vlastností použít tlačítko je povoleno pouze v případě, že došlo ke změně hodnoty vlastnosti ovládací prvky stránky. Pomocí této funkce můžete zadat ovládacích prvků, které nezpůsobí na tlačítko použít, chcete-li povolit, pokud jejich hodnoty změnit.  
  
##  <a name="ismodified"></a>COlePropertyPage::IsModified  
 Určuje, zda uživatel změnil žádné hodnoty na stránce vlastností.  
  
```  
BOOL IsModified();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,** Pokud byl upraven na stránku vlastností.  
  
##  <a name="oneditproperty"></a>COlePropertyPage::OnEditProperty  
 Rozhraní framework volá tuto funkci při specifická vlastnost je k provádění úprav.  
  
```  
virtual BOOL OnEditProperty(DISPID dispid);
```  
  
### <a name="parameters"></a>Parametry  
 `dispid`  
 Odesílání ID vlastnosti Upravovaný.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výchozí implementace vrací **FALSE**. Přepsání této funkce by měla vrátit **TRUE**.  
  
### <a name="remarks"></a>Poznámky  
 Je možné přepsat jeho nastavení fokusu vhodný ovládací prvek na stránce. Výchozí implementace neprovede žádnou akci a vrátí **FALSE**.  
  
##  <a name="onhelp"></a>COlePropertyPage::OnHelp  
 Rozhraní framework volá tuto funkci, když uživatel požádá online nápovědy.  
  
```  
virtual BOOL OnHelp(LPCTSTR lpszHelpDir);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszHelpDir*  
 Adresář, který obsahuje soubor nápovědy její stránku vlastností.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výchozí implementace vrací **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 Přepište Pokud stránky vlastností musí provést zvláštní akce, když uživatel získá přístup k nápovědě. Výchozí implementace neprovede žádnou akci a vrátí **FALSE**, které nařídí rozhraní framework volání WinHelp.  
  
##  <a name="oninitdialog"></a>COlePropertyPage::OnInitDialog  
 Při inicializaci dialogové okno Vlastnosti stránky volá rámec této funkce.  
  
```  
virtual BOOL OnInitDialog();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Výchozí implementace vrací **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 Přepište je-li zvláštní akce, vyžadováno při inicializaci dialogu. Výchozí implementace volá `CDialog::OnInitDialog` a vrátí **FALSE**.  
  
##  <a name="onobjectschanged"></a>COlePropertyPage::OnObjectsChanged  
 Voláno rámcem při výběru jiného ovládacího prvku OLE, novými vlastnostmi.  
  
```  
virtual void OnObjectsChanged();
```  
  
### <a name="remarks"></a>Poznámky  
 Při zobrazení vlastností ovládacího prvku OLE vývojářského prostředí, dialogové okno nemodální slouží k zobrazení jeho stránky vlastností. Pokud je vybraný další ovládací prvek, musí být zobrazena jinou sadu stránek vlastností pro novou sadu vlastností. Tato funkce upozornit na stránce vlastností změnu volá framework.  
  
 Funkci pro příjem oznámení této akce a provádět žádné zvláštní akce přepište.  
  
##  <a name="onsetpagesite"></a>COlePropertyPage::OnSetPageSite  
 Rozhraní framework volá tuto funkci, pokud vlastnost rámečku poskytuje stránka vlastností stránky webu.  
  
```  
virtual void OnSetPageSite();
```  
  
### <a name="remarks"></a>Poznámky  
 Výchozí implementace načte záhlaví stránky a se pokusí určit velikost stránky z prostředku dialogového okna. Potlačí tuto funkci v případě, že žádné další akce; vyžaduje stránky vlastností přepsání by měly volat základní třídy implementaci.  
  
##  <a name="setcontrolstatus"></a>COlePropertyPage::SetControlStatus  
 Změní stav ovládací prvek stránky vlastností.  
  
```  
BOOL SetControlStatus(
    UINT nID,  
    BOOL bDirty);
```  
  
### <a name="parameters"></a>Parametry  
 `nID`  
 Obsahuje ID ovládacího prvku stránky vlastností.  
  
 `bDirty`  
 Určuje, pokud byla změněna pole její stránku vlastností. Nastavte na **TRUE** Pokud pole byl upraven, **FALSE** Pokud byl změněn.  
  
### <a name="return-value"></a>Návratová hodnota  
 **Hodnota TRUE,**, pokud byl daný ovládací prvek, jinak hodnota **FALSE**.  
  
### <a name="remarks"></a>Poznámky  
 Pokud při zavření stránku vlastností nebo na tlačítko použít je zvolen je nevyřízený stav ovládací prvek stránky vlastností, aktualizují se ovládacího prvku na odpovídající hodnotu.  
  
##  <a name="setdialogresource"></a>COlePropertyPage::SetDialogResource  
 Nastaví její stránku vlastností prostředku dialogového okna.  
  
```  
void SetDialogResource(HGLOBAL hDialog);
```  
  
### <a name="parameters"></a>Parametry  
 *hDialog*  
 Zpracování na stránce vlastností prostředku dialogového okna.  
  
##  <a name="sethelpinfo"></a>COlePropertyPage::SetHelpInfo  
 Určuje popisek informace, název souboru nápovědy a kontext nápovědy pro stránky vlastností.  
  
```  
void SetHelpInfo(
    LPCTSTR lpszDocString,  
    LPCTSTR lpszHelpFile = NULL,  
    DWORD dwHelpContext = 0);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszDocString*  
 Řetězec obsahující stručné informace o zobrazení ve stavovém řádku nebo jiné umístění.  
  
 `lpszHelpFile`  
 Název souboru nápovědy její stránku vlastností.  
  
 *dwHelpContext*  
 Kontext nápovědy pro stránku vlastností.  
  
##  <a name="setmodifiedflag"></a>COlePropertyPage::SetModifiedFlag  
 Určuje, zda má uživatel změnil její stránku vlastností.  
  
```  
void SetModifiedFlag(BOOL bModified = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 `bModified`  
 Určuje novou hodnotu upravené příznak její stránku vlastností.  
  
##  <a name="setpagename"></a>COlePropertyPage::SetPageName  
 Nastaví název její stránku vlastností, které rámečku vlastnost se obvykle zobrazí na kartě stránky.  
  
```  
void SetPageName(LPCTSTR lpszPageName);
```  
  
### <a name="parameters"></a>Parametry  
 *lpszPageName*  
 Ukazatel na řetězec obsahující název stránky vlastností.  
  
## <a name="see-also"></a>Viz také  
 [Circ3 – ukázka MFC](../../visual-cpp-samples.md)   
 [Ukázka MFC TESTHELP](../../visual-cpp-samples.md)   
 [CDialog – třída](../../mfc/reference/cdialog-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CDialog – třída](../../mfc/reference/cdialog-class.md)
