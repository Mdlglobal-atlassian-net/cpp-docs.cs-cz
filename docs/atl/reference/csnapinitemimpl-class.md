---
title: "Třída CSnapInItemImpl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl::CSnapInItemImpl
- ATLSNAP/ATL::CSnapInItemImpl::AddMenuItems
- ATLSNAP/ATL::CSnapInItemImpl::Command
- ATLSNAP/ATL::CSnapInItemImpl::CreatePropertyPages
- ATLSNAP/ATL::CSnapInItemImpl::FillData
- ATLSNAP/ATL::CSnapInItemImpl::GetResultPaneInfo
- ATLSNAP/ATL::CSnapInItemImpl::GetResultViewType
- ATLSNAP/ATL::CSnapInItemImpl::GetScopePaneInfo
- ATLSNAP/ATL::CSnapInItemImpl::Notify
- ATLSNAP/ATL::CSnapInItemImpl::QueryPagesFor
- ATLSNAP/ATL::CSnapInItemImpl::SetMenuInsertionFlags
- ATLSNAP/ATL::CSnapInItemImpl::SetToolbarButtonInfo
- ATLSNAP/ATL::CSnapInItemImpl::UpdateMenuState
- ATLSNAP/ATL::CSnapInItemImpl::UpdateToolbarButton
- ATLSNAP/ATL::CSnapInItemImpl::m_bstrDisplayName
- ATLSNAP/ATL::CSnapInItemImpl::m_resultDataItem
- ATLSNAP/ATL::CSnapInItemImpl::m_scopeDataItem
dev_langs: C++
helpviewer_keywords:
- snap-ins, data items
- snap-ins, ATL support for
- CSnapInItemImpl class
- snap-ins
ms.assetid: 52caefbd-9eae-49b0-add2-d55524271aa7
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 1758a3d3bec03015abf35626adec69e1db9a7fdb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="csnapinitemimpl-class"></a>CSnapInItemImpl – třída
Tato třída poskytuje metody pro implementaci objekt modul snap-in uzlu.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T, BOOL bIsExtension = FALSE>  
class ATL_NO_VTABLE CSnapInItemImpl : public CSnapInItem
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `CSnapInItemImpl`.  
  
 *bIsExtension*  
 **Hodnota TRUE,** Pokud objekt je modul snap-in rozšíření; jinak **FALSE**.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CSnapInItemImpl::CSnapInItemImpl](#csnapinitemimpl)|Konstruktor|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CSnapInItemImpl::AddMenuItems](#addmenuitems)|Položky nabídky se přidá do kontextové nabídky.|  
|[CSnapInItemImpl::Command](#command)|Voláno rozhraním konzole při výběru položky nabídky vlastní.|  
|[CSnapInItemImpl::CreatePropertyPages](#createpropertypages)|Přidá do seznamu vlastností modulu snap-in stránky.|  
|[CSnapInItemImpl::FillData](#filldata)|Kopie informací o objektu modulu snap-in do zadaného datového proudu.|  
|[CSnapInItemImpl::GetResultPaneInfo](#getresultpaneinfo)|Načte **RESULTDATAITEM** struktura modulu snap-in.|  
|[CSnapInItemImpl::GetResultViewType](#getresultviewtype)|Určuje typ zobrazení používané v podokně výsledků.|  
|[CSnapInItemImpl::GetScopePaneInfo](#getscopepaneinfo)|Načte **SCOPEDATAITEM** struktura modulu snap-in.|  
|[CSnapInItemImpl::Notify](#notify)|Voláno rozhraním konzole upozornit modul snap-in akcí, které má uživatel.|  
|[CSnapInItemImpl::QueryPagesFor](#querypagesfor)|Volá se, pokud uzel modul snap-in podporuje stránky vlastností.|  
|[CSnapInItemImpl::SetMenuInsertionFlags](#setmenuinsertionflags)|Upravuje příznaky vložení nabídky pro objekt, který modul snap-in.|  
|[CSnapInItemImpl::SetToolbarButtonInfo](#settoolbarbuttoninfo)|Nastaví informace o zadané panelu nástrojů zobrazí tlačítko.|  
|[CSnapInItemImpl::UpdateMenuState](#updatemenustate)|Aktualizuje stav položky kontextové nabídky.|  
|[CSnapInItemImpl::UpdateToolbarButton](#updatetoolbarbutton)|Aktualizuje stav tlačítka zadaný panelu nástrojů.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CSnapInItemImpl::m_bstrDisplayName](#m_bstrdisplayname)|Název objektu modulu snap-in.|  
|[CSnapInItemImpl::m_resultDataItem](#m_resultdataitem)|Windows **RESULTDATAITEM** struktura používané `CSnapInItemImpl` objektu.|  
|[CSnapInItemImpl::m_scopeDataItem](#m_scopedataitem)|Windows **SCOPEDATAITEM** struktura používané `CSnapInItemImpl` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `CSnapInItemImpl`poskytuje základní implementaci pro objekt uzlu modul snap-in, například přidávání položek nabídek a panelů nástrojů a předávání příkazy pro uzel modul snap-in k funkci příslušnou obslužnou rutinu. Tyto funkce jsou implementovány pomocí několika různých rozhraní a mapování typů. Výchozí implementace zpracovává oznámení odesílaná určíte správné instanci odvozené třídy a pak předávání zpráv na správnou instanci objektu uzlu.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CSnapInItem`  
  
 `CSnapInItemImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsnap.h  
  
##  <a name="addmenuitems"></a>CSnapInItemImpl::AddMenuItems  
 Tato metoda implementuje funkce Win32 [IExtendContextMenu::AddMenuItems](http://msdn.microsoft.com/library/aa814841).  
  
```
AddMenuItems(  
    LPCONTEXTMENUCALLBACK piCallback,
    long* pInsertionAllowed,
    DATA_OBJECT_TYPES type);
```  
  
### <a name="parameters"></a>Parametry  
 *piCallback*  
 [v] Ukazatel **IContextMenuCallback** položky, můžete přidat do kontextové nabídky.  
  
 `pInsertionAllowed`  
 [ve out] Identifikuje Microsoft Management Console MMC definována, položky nabídky vložení body, které lze použít. To může být kombinací následující příznaky:  
  
- **CCM_INSERTIONALLOWED_TOP** položky lze vložit v horní části z kontextové nabídky.  
  
- **CCM_INSERTIONALLOWED_NEW** lze vytvořit nový dílčí vkládat položky.  
  
- **CCM_INSERTIONALLOWED_TASK** položky lze vkládat dílčí úlohy.  
  
- **CCM_INSERTIONALLOWED_VIEW** možné vložit položky v nabídce zobrazení panelu nástrojů nebo v podnabídce zobrazení v místní nabídce podokně výsledků.  
  
 `type`  
 [v] Určuje typ objektu. Může mít jednu z následujících hodnot:  
  
- **CCT_SCOPE** datový objekt pro kontext podokně oboru.  
  
- **CCT_RESULT** datový objekt pro kontext podokně výsledků.  
  
- **CCT_SNAPIN_MANAGER** datového objektu pro modul snap-in Správce kontext.  
  
- **CCT_UNINITIALIZED** má neplatný typ datového objektu.  
  
##  <a name="command"></a>CSnapInItemImpl::Command  
 Tato metoda implementuje funkce Win32 [IExtendContextMenu::Command](http://msdn.microsoft.com/library/aa814842).  
  
```
Command(long lCommandID, DATA_OBJECT_TYPES type);
```  
  
### <a name="parameters"></a>Parametry  
 *lCommandID*  
 [v] Určuje identifikátor příkazu položky nabídky.  
  
 `type`  
 [v] Určuje typ objektu. Může mít jednu z následujících hodnot:  
  
- **CCT_SCOPE** datový objekt pro kontext podokně oboru.  
  
- **CCT_RESULT** datový objekt pro kontext podokně výsledků.  
  
- **CCT_SNAPIN_MANAGER** datového objektu pro modul snap-in Správce kontext.  
  
- **CCT_UNINITIALIZED** má neplatný typ datového objektu.  
  
##  <a name="createpropertypages"></a>CSnapInItemImpl::CreatePropertyPages  
 Tato metoda implementuje funkce Win32 [IExtendPropertySheet::CreatePropertyPages](http://msdn.microsoft.com/library/aa814846).  
  
```
CreatePropertyPages(  
    LPPROPERTYSHEETCALLBACK lpProvider,
    long handle,
    IUnknown* pUnk,
    DATA_OBJECT_TYPES type);
```  
  
### <a name="parameters"></a>Parametry  
 *lpProvider*  
 [v] Ukazatel **IPropertySheetCallback** rozhraní.  
  
 *Popisovač*  
 [v] Určuje popisovač použít trasu **MMCN_PROPERTY_CHANGE** oznámení k třídě příslušná data.  
  
 *pUnk*  
 [v] Ukazatel **IExtendPropertySheet** rozhraní na objekt, který obsahuje kontextové informace o uzlu.  
  
 `type`  
 [v] Určuje typ objektu. Může mít jednu z následujících hodnot:  
  
- **CCT_SCOPE** datový objekt pro kontext podokně oboru.  
  
- **CCT_RESULT** datový objekt pro kontext podokně výsledků.  
  
- **CCT_SNAPIN_MANAGER** datového objektu pro modul snap-in Správce kontext.  
  
- **CCT_UNINITIALIZED** má neplatný typ datového objektu.  
  
##  <a name="csnapinitemimpl"></a>CSnapInItemImpl::CSnapInItemImpl  
 Vytvoří `CSnapInItemImpl` objektu.  
  
```
CSnapInItemImpl();
```  
  
##  <a name="filldata"></a>CSnapInItemImpl::FillData  
 Tato funkce je volána k načtení informací o položce.  
  
```
FillData(CLIPFORMAT cf, LPSTREAM pStream);
```  
  
### <a name="parameters"></a>Parametry  
 `cf`  
 [v] Formát (text, formátovaným textem nebo RTF s OLE – položky) do schránky.  
  
 `pStream`  
 [v] Ukazatel na datový proud obsahující data objektu.  
  
### <a name="remarks"></a>Poznámky  
 Chcete-li správně implementovat tuto funkci, zkopírujte správné informace do datového proudu ( `pStream`), v závislosti na formát schránky indikován `cf`.  
  
##  <a name="getresultviewtype"></a>CSnapInItemImpl::GetResultViewType  
 Volání této funkce se načíst typ zobrazení podokně s výsledky modulu snap-in objektu.  
  
```
GetResultViewType(
    LPOLESTR* ppViewType,
    long* pViewOptions);
```  
  
### <a name="parameters"></a>Parametry  
 *ppViewType*  
 [out] Ukazatel na adresu typ vrácený zobrazení.  
  
 *pViewOptions*  
 [out] Ukazatel **MMC_VIEW_OPTIONS** výčtu, který poskytuje možnosti určeného vlastnícím modul snap-in konzole. Tato hodnota může být jeden z následujících akcí:  
  
- **MMC_VIEW_OPTIONS_NOLISTVIEWS** = 0x00000001 informuje nepoužívejte prezentací standardní seznam možností zobrazení v konzole **zobrazení** nabídky. Umožňuje modulu snap-in-li zobrazit svou vlastní vlastní zobrazení pouze v podokně výsledků. Toto je pouze možnost příznak definované v tuto chvíli.  
  
- **MMC_VIEW_OPTIONS_NONE** = 0 umožňuje výchozí možnosti zobrazení.  
  
##  <a name="getscopepaneinfo"></a>CSnapInItemImpl::GetScopePaneInfo  
 Volání této funkce můžete získat **SCOPEDATAITEM** struktura modulu snap-in.  
  
```
GetScopePaneInfo (SCOPEDATAITEM* pScopeDataItem);
```  
  
### <a name="parameters"></a>Parametry  
 *pScopeDataItem*  
 [out] Ukazatel **SCOPEDATAITEM** struktura `CSnapInItemImpl` objektu.  
  
##  <a name="getresultpaneinfo"></a>CSnapInItemImpl::GetResultPaneInfo  
 Volání této funkce můžete získat **RESULTDATAITEM** struktura modulu snap-in.  
  
```
GetResultPaneInfo (RESULTDATAITEM* pResultDataItem);
```  
  
### <a name="parameters"></a>Parametry  
 *pResultDataItem*  
 [out] Ukazatel **RESULTDATAITEM** struktura `CSnapInItemImpl` objektu.  
  
##  <a name="m_bstrdisplayname"></a>CSnapInItemImpl::m_bstrDisplayName  
 Obsahuje řetězec zobrazí pro položku uzlu.  
  
```
CComBSTR m_bstrDisplayName;
```  
  
##  <a name="m_scopedataitem"></a>CSnapInItemImpl::m_scopeDataItem  
 `SCOPEDATAITEM` Struktura modul snap-in datového objektu.  
  
```
SCOPEDATAITEM m_scopeDataItem;
```  
  
##  <a name="m_resultdataitem"></a>CSnapInItemImpl::m_resultDataItem  
 [RESULTDATAITEM](http://msdn.microsoft.com/library/aa815165) struktura modul snap-in datového objektu.  
  
```
RESULTDATAITEM m_resultDataItem;
```  
  
##  <a name="notify"></a>CSnapInItemImpl::Notify  
 Voláno, když je objekt modul snap-in reagovali na ni uživatelem.  
  
```
STDMETHOD(Notify)(
    MMC_NOTIFY_TYPE event,
    long arg,
    long param,
    IComponentData* pComponentData,
    IComponent* pComponent,
    DATA_OBJECT_TYPES type) = 0;
```  
  
### <a name="parameters"></a>Parametry  
 `event`  
 [v] Určuje akci provedenou uživatele. Následující oznámení jsou možné:  
  
- **MMCN_ACTIVATE** odeslána, když okno je aktivovat a deaktivovat.  
  
- **MMCN_ADD_IMAGES** posílá přidat Image do podokna výsledků.  
  
- **MMCN_BTN_CLICK** odeslána po kliknutí na jednu z tlačítka panelu nástrojů.  
  
- **MMCN_CLICK** odeslána, když uživatel klikne na tlačítko myši na položku zobrazení seznamu.  
  
- **MMCN_DBLCLICK** odeslána po dvojité kliknutí tlačítkem myši na položku zobrazení seznamu.  
  
- **MMCN_DELETE** o modulu snap-in, která má být objekt odeslána odstranit.  
  
- **MMCN_EXPAND** odeslat v případě, že složka je nutné rozšířit nebo uzavřeny.  
  
- **MMCN_MINIMIZED** odeslána, když okno je se rychle minimalizovat nebo v maximalizovaném okně.  
  
- **MMCN_PROPERTY_CHANGE** odesílá informuje objekt modul snap-in, který zobrazení objektu modulu snap-in se má změnit.  
  
- **MMCN_REMOVE_CHILDREN** odeslat v případě, že modul snap-in, musíte odstranit celý podstrom byl přidán pod určeného uzlu.  
  
- **MMCN_RENAME** odeslat dotaz pro přejmenovat při prvním a druhém uděláte přejmenování.  
  
- **MMCN_SELECT** odeslané vybranou položku v podokně zobrazení obor nebo výsledek.  
  
- **MMCN_SHOW** odeslat v případě, že je výběru nebo zrušení výběru první položku oboru.  
  
- **MMCN_VIEW_CHANGE** odeslat v případě, že modul snap-in můžete aktualizovat všechna zobrazení Pokud dojde ke změně.  
  
 `arg`  
 [v] Závisí na typu oznámení.  
  
 `param`  
 [v] Závisí na typu oznámení.  
  
 *pComponentData*  
 [out] Ukazatel na implementaci objekt **IComponentData**. Tento parametr je **NULL** Pokud oznámení není předávaná ze **IComponentData::Notify**.  
  
 *pComponent*  
 [out] Ukazatel na objektu, který implementuje **IComponent**. Tento parametr je **NULL** Pokud oznámení není předávaná ze **IComponent::Notify**.  
  
 `type`  
 [v] Určuje typ objektu. Může mít jednu z následujících hodnot:  
  
- **CCT_SCOPE** datový objekt pro kontext podokně oboru.  
  
- **CCT_RESULT** datový objekt pro kontext podokně výsledků.  
  
- **CCT_SNAPIN_MANAGER** datového objektu pro modul snap-in Správce kontext.  
  
- **CCT_UNINITIALIZED** má neplatný typ datového objektu.  
  
##  <a name="querypagesfor"></a>CSnapInItemImpl::QueryPagesFor  
 Volá se, pokud uzel modul snap-in podporuje stránky vlastností.  
  
```
QueryPagesFor(DATA_OBJECT_TYPES type);
```  
  
##  <a name="setmenuinsertionflags"></a>CSnapInItemImpl::SetMenuInsertionFlags  
 Volání této funkce můžete upravit v nabídce příznacích vložení určeného `pInsertionAllowed`, modul snap-in objektu.  
  
```
void SetMenuInsertionFlags(  
    bool bBeforeInsertion,
    long* pInsertionAllowed);
```  
  
### <a name="parameters"></a>Parametry  
 *bBeforeInsertion*  
 [v] Nenulové hodnoty, pokud funkce by měla být volána před položky budou přidány do kontextové nabídky; jinak 0.  
  
 `pInsertionAllowed`  
 [ve out] Identifikuje Microsoft Management Console MMC definována, položky nabídky vložení body, které lze použít. To může být kombinací následující příznaky:  
  
- **CCM_INSERTIONALLOWED_TOP** položky lze vložit v horní části z kontextové nabídky.  
  
- **CCM_INSERTIONALLOWED_NEW** lze vytvořit nový dílčí vkládat položky.  
  
- **CCM_INSERTIONALLOWED_TASK** položky lze vkládat dílčí úlohy.  
  
- **CCM_INSERTIONALLOWED_VIEW** možné vložit položky v nabídce zobrazení panelu nástrojů nebo v podnabídce zobrazení v místní nabídce podokně výsledků.  
  
### <a name="remarks"></a>Poznámky  
 Pokud vyvíjíte primární modul snap-in, můžete obnovit žádné příznaky vložení jako způsob omezení druh položky nabídky, které můžete přidat rozšíření třetích stran. Například primární modul snap-in můžete zrušit **CCM_INSERTIONALLOWED_NEW** příznak, abyste zabránili přidávání vlastních vytvořit nové položky nabídky rozšíření.  
  
 Byste neměli nastavení bits v `pInsertionAllowed` které byly původně vymazán. Další verze konzoly MMC může pomocí služby bits není aktuálně definován, takže byste neměli měnit bitů, které nejsou aktuálně definován.  
  
##  <a name="settoolbarbuttoninfo"></a>CSnapInItemImpl::SetToolbarButtonInfo  
 Volání této funkce k úpravě jakékoli styly tlačítek panelu nástrojů objektu modulu snap-in, před vytvořením panelu nástrojů.  
  
```
void SetToolbarButtonInfo(  
    UINT id,
    BYTE* fsState,
    BYTE* fsType);
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 [v] ID na panelu nástrojů tlačítko nastavit.  
  
 `fsState`  
 [v] Příznaky stavu tlačítka. Může být jeden nebo více následujících akcí:  
  
- `TBSTATE_CHECKED`Tlačítko má **TBSTYLE_CHECKED** styl a je stisknutí tlačítka.  
  
- `TBSTATE_ENABLED`Tlačítko přijme vstup uživatele. Tlačítko, které nemá tento stav nepřijímá vstup uživatele a neaktivní.  
  
- `TBSTATE_HIDDEN`Tlačítko není viditelná a nemůže přijímat vstup uživatele.  
  
- `TBSTATE_INDETERMINATE`Tlačítko neaktivní.  
  
- `TBSTATE_PRESSED`Stisknutí tlačítka.  
  
- `TBSTATE_WRAP`Konec řádku následuje tlačítko. Tlačítko musí mít také `TBSTATE_ENABLED`.  
  
 *fsType*  
 [v] Příznaky stavu tlačítka. Může být jeden nebo více následujících akcí:  
  
- `TBSTYLE_BUTTON`Vytvoří standardní tlačítka.  
  
- `TBSTYLE_CHECK`Vytvoří tlačítko, která přepíná mezi stavy při stisknutí tlačítka myši a stisknutí není pokaždé, když uživatel klikne. Tlačítko má jinou barvu pozadí, když je ve stavu při stisknutí tlačítka.  
  
- `TBSTYLE_CHECKGROUP`Vytvoří tlačítko kontroly, které zůstává při stisknutí tlačítka, dokud není stisknuta jiné tlačítko ve skupině.  
  
- `TBSTYLE_GROUP`Vytvoří tlačítko, které zůstává při stisknutí tlačítka, dokud není stisknuta jiné tlačítko ve skupině.  
  
- `TBSTYLE_SEP`Vytvoří oddělovač poskytování malá mezera mezi skupinami tlačítko. Tlačítko, které má tento styl nepřijímá vstup uživatele.  
  
##  <a name="updatemenustate"></a>CSnapInItemImpl::UpdateMenuState  
 Volání této funkce můžete upravit položku nabídky, než je vložen do místní nabídky objektu modulu snap-in.  
  
```
void UpdateMenuState(  
    UINT id,
    LPTSTR pBuf,
    UINT* flags);
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 [v] ID položku nabídky nastavení.  
  
 `pBuf`  
 [v] Ukazatel na řetězec pro položku nabídky aktualizovat.  
  
 `flags`  
 [v] Určuje nové příznaky stavu. To může být kombinací následující příznaky:  
  
- **MF_POPUP** Určuje, že se jedná o podnabídky v místní nabídce. Položky nabídky, body vložení a další dílčích mohou být přidány do této konfigurace pomocí podnabídky jeho **lCommandID** jako jejich **IInsertionPointID**.  
  
- **MF_BITMAP** a `MF_OWNERDRAW` nejsou povolené tyto příznaky a bude mít za následek návratová hodnota `E_INVALIDARG`.  
  
- **MF_SEPARATOR** nevykresluje na vodorovném řádku rozdíl. Pouze **IContextMenuProvider** je povolen pro přidání položek nabídky se **MF_SEPARATOR** nastavit.  
  
- **MF_CHECKED** zaškrtne políčko vedle položky nabídky.  
  
- **MF_DISABLED** zakáže položky nabídky, takže ji nelze vybrat, ale příznak není šedé ho.  
  
- `MF_ENABLED`Umožňuje položky nabídky, lze ji použít, obnovení z šedým stavu.  
  
- **MF_GRAYED** zakáže položky nabídky, graying ji proto není k dispozici.  
  
- **MF_MENUBARBREAK** funguje stejně jako **MF_MENUBREAK** příznak pro řádku nabídek. Pro rozevírací nabídky, podnabídky nebo místní nabídky nový sloupec je oddělená od původního sloupce svislá čára.  
  
- **MF_MENUBREAK** umístí položku na nový řádek (pro řádku nabídek) nebo v novém sloupci (pro rozevírací nabídky, podnabídky nebo místní nabídky) bez dělicí sloupce.  
  
- **MF_UNCHECKED** není, zaškrtněte políčko vedle položky (výchozí).  
  
 Následující skupiny příznaky nelze použít společně:  
  
- **MF_DISABLED**, `MF_ENABLED`, a **MF_GRAYED**.  
  
- **MF_MENUBARBREAK** a **MF_MENUBREAK**.  
  
- **MF_CHECKED** a **MF_UNCHECKED**.  
  
##  <a name="updatetoolbarbutton"></a>CSnapInItemImpl::UpdateToolbarButton  
 Volání této funkce můžete upravit tlačítka panelu nástrojů, objektu modulu snap-in, než se zobrazí.  
  
```
BOOL UpdateToolbarButton(UINT id, BYTE fsState);
```  
  
### <a name="parameters"></a>Parametry  
 `id`  
 Určuje ID tlačítka panelu nástrojů zobrazí tlačítko Aktualizovat.  
  
 `fsState`  
 Určuje stav tlačítka panelu nástrojů. Pokud tento stav je možné nastavit, vrátí **TRUE**. To může být kombinací následující příznaky:  
  
- **Povolit** tlačítko zadávaná uživateli. Tlačítko, které nemá tento stav nepřijímá vstup uživatele a neaktivní.  
  
- **ZAŠKRTNUTÍ** tlačítko má **zaškrtnutí** styl a je stisknutí tlačítka.  
  
- **SKRYTÝ** tlačítko není viditelná a nemůže přijímat vstup uživatele.  
  
- **NEURČITÉM** neaktivní tlačítko.  
  
- **BUTTONPRESSED** stisknutí tlačítka.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)
