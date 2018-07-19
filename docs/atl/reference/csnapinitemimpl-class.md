---
title: Csnapinitemimpl – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
dev_langs:
- C++
helpviewer_keywords:
- snap-ins, data items
- snap-ins, ATL support for
- CSnapInItemImpl class
- snap-ins
ms.assetid: 52caefbd-9eae-49b0-add2-d55524271aa7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 77f92e2a0a5ea65fce361c19ae52745932f58deb
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37884926"
---
# <a name="csnapinitemimpl-class"></a>Csnapinitemimpl – třída
Tato třída poskytuje metody pro implementaci modulu snap-in uzel objektu.  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T, BOOL bIsExtension = FALSE>  
class ATL_NO_VTABLE CSnapInItemImpl : public CSnapInItem
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Vaše třída odvozena od `CSnapInItemImpl`.  
  
 *bIsExtension*  
 Hodnota TRUE, pokud objekt je rozšíření modulu snap-in; v opačném případě FALSE.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[CSnapInItemImpl::CSnapInItemImpl](#csnapinitemimpl)|Konstruktor|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CSnapInItemImpl::AddMenuItems](#addmenuitems)|Přidá položky nabídky do kontextové nabídky.|  
|[CSnapInItemImpl::Command](#command)|Při výběru položky nabídky vlastní volány konzole.|  
|[CSnapInItemImpl::CreatePropertyPages](#createpropertypages)|Přidá do seznamu vlastností v modulu snap-in stránky.|  
|[CSnapInItemImpl::FillData](#filldata)|Zkopíruje informace o objektu modulu snap-in do zadaného datového proudu.|  
|[CSnapInItemImpl::GetResultPaneInfo](#getresultpaneinfo)|Načte `RESULTDATAITEM` strukturu modulu snap-in.|  
|[CSnapInItemImpl::GetResultViewType](#getresultviewtype)|Určuje typ zobrazení používané v podokně výsledků.|  
|[CSnapInItemImpl::GetScopePaneInfo](#getscopepaneinfo)|Načte `SCOPEDATAITEM` strukturu modulu snap-in.|  
|[CSnapInItemImpl::Notify](#notify)|Je voláno konzoly upozornit modul snap-in akcí provedených uživatelem.|  
|[CSnapInItemImpl::QueryPagesFor](#querypagesfor)|Volá se, pokud uzel modulu snap-in podporuje stránky vlastností.|  
|[CSnapInItemImpl::SetMenuInsertionFlags](#setmenuinsertionflags)|Upraví příznaky vložení nabídky pro objekt modulu snap-in.|  
|[CSnapInItemImpl::SetToolbarButtonInfo](#settoolbarbuttoninfo)|Nastaví informace zadané tlačítka.|  
|[CSnapInItemImpl::UpdateMenuState](#updatemenustate)|Aktualizuje stav položky kontextové nabídky.|  
|[CSnapInItemImpl::UpdateToolbarButton](#updatetoolbarbutton)|Aktualizuje stav zadaného tlačítka.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[CSnapInItemImpl::m_bstrDisplayName](#m_bstrdisplayname)|Název objektu modulu snap-in.|  
|[CSnapInItemImpl::m_resultDataItem](#m_resultdataitem)|Windows `RESULTDATAITEM` struktura používá `CSnapInItemImpl` objektu.|  
|[CSnapInItemImpl::m_scopeDataItem](#m_scopedataitem)|Windows `SCOPEDATAITEM` struktura používá `CSnapInItemImpl` objektu.|  
  
## <a name="remarks"></a>Poznámky  
 `CSnapInItemImpl` poskytuje základní implementaci pro objekt uzel modulu snap-in, jako je přidání položek nabídky a panely nástrojů a příkazů pro modul snap-in uzel, který má odpovídajícího popisovače funkce předávání. Tyto funkce jsou implementované pomocí několika různých rozhraní a namapujte typy. Výchozí implementace zpracovává oznámení zaslaná z objektu uzlu určování správné instanci odvozené třídy a pak předávání zpráv na správné instanci.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `CSnapInItem`  
  
 `CSnapInItemImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlsnap.h  
  
##  <a name="addmenuitems"></a>  CSnapInItemImpl::AddMenuItems  
 Tato metoda implementuje funkci Win32 [IExtendContextMenu::AddMenuItems](http://msdn.microsoft.com/library/aa814841).  
  
```
AddMenuItems(  
    LPCONTEXTMENUCALLBACK piCallback,
    long* pInsertionAllowed,
    DATA_OBJECT_TYPES type);
```  
  
### <a name="parameters"></a>Parametry  
 *piCallback*  
 [in] Ukazatel `IContextMenuCallback` , který můžete přidat položky do kontextové nabídky.  
  
 *pInsertionAllowed*  
 [out v] Identifikuje definované Microsoft Management Console MMC, položka nabídky vložení body, které lze použít. To může být kombinací následujících příznaků:  
  
- V horní části místní nabídka může být vložen CCM_INSERTIONALLOWED_TOP položky.  
  
- CCM_INSERTIONALLOWED_NEW položky může být vložen do podnabídky vytvořit nový.  
  
- V podnabídce úloh lze vložit CCM_INSERTIONALLOWED_TASK položky.  
  
- V nabídce Zobrazit panel nástrojů nebo v podnabídce zobrazení místní nabídky podokna výsledků lze vložit CCM_INSERTIONALLOWED_VIEW položky.  
  
 *Typ*  
 [in] Určuje typ objektu. Může mít jednu z následujících hodnot:  
  
- CCT_SCOPE datový objekt oboru podokno kontextu.  
  
- CCT_RESULT datový objekt kontextu podokno výsledků.  
  
- CCT_SNAPIN_MANAGER datového objektu pro modul snap-in Správce kontextu.  
  
- CCT_UNINITIALIZED datový objekt je neplatného typu.  
  
##  <a name="command"></a>  CSnapInItemImpl::Command  
 Tato metoda implementuje funkci Win32 [IExtendContextMenu::Command](http://msdn.microsoft.com/library/aa814842).  
  
```
Command(long lCommandID, DATA_OBJECT_TYPES type);
```  
  
### <a name="parameters"></a>Parametry  
 *lCommandID*  
 [in] Určuje identifikátor příkazu položky nabídky.  
  
 *Typ*  
 [in] Určuje typ objektu. Může mít jednu z následujících hodnot:  
  
- CCT_SCOPE datový objekt oboru podokno kontextu.  
  
- CCT_RESULT datový objekt kontextu podokno výsledků.  
  
- CCT_SNAPIN_MANAGER datového objektu pro modul snap-in Správce kontextu.  
  
- CCT_UNINITIALIZED datový objekt je neplatného typu.  
  
##  <a name="createpropertypages"></a>  CSnapInItemImpl::CreatePropertyPages  
 Tato metoda implementuje funkci Win32 [IExtendPropertySheet::CreatePropertyPages](http://msdn.microsoft.com/library/aa814846).  
  
```
CreatePropertyPages(  
    LPPROPERTYSHEETCALLBACK lpProvider,
    long handle,
    IUnknown* pUnk,
    DATA_OBJECT_TYPES type);
```  
  
### <a name="parameters"></a>Parametry  
 *lpProvider*  
 [in] Ukazatel `IPropertySheetCallback` rozhraní.  
  
 *Popisovač*  
 [in] Určuje popisovač používaný ke směrování zprávy oznámení MMCN_PROPERTY_CHANGE na třídu příslušná data.  
  
 *pUnk*  
 [in] Ukazatel `IExtendPropertySheet` rozhraní na objekt, který obsahuje informace o kontextu uzlu.  
  
 *Typ*  
 [in] Určuje typ objektu. Může mít jednu z následujících hodnot:  
  
- CCT_SCOPE datový objekt oboru podokno kontextu.  
  
- CCT_RESULT datový objekt kontextu podokno výsledků.  
  
- CCT_SNAPIN_MANAGER datového objektu pro modul snap-in Správce kontextu.  
  
- CCT_UNINITIALIZED datový objekt je neplatného typu.  
  
##  <a name="csnapinitemimpl"></a>  CSnapInItemImpl::CSnapInItemImpl  
 Vytvoří `CSnapInItemImpl` objektu.  
  
```
CSnapInItemImpl();
```  
  
##  <a name="filldata"></a>  CSnapInItemImpl::FillData  
 Tato funkce je volána k načtení informací o položce.  
  
```
FillData(CLIPFORMAT cf, LPSTREAM pStream);
```  
  
### <a name="parameters"></a>Parametry  
 *CF*  
 [in] Formát (text, formátovaný text nebo formátovaný text položky OLE) do schránky.  
  
 *pStream*  
 [in] Ukazatel na datový proud obsahující data objektu.  
  
### <a name="remarks"></a>Poznámky  
 Pokud chcete tuto funkci správně implementovat, zkopírujte správné informace do datového proudu (*pStream*), v závislosti na formát schránky indikován *cf*.  
  
##  <a name="getresultviewtype"></a>  CSnapInItemImpl::GetResultViewType  
 Voláním této funkce se načíst typ zobrazení v podokně výsledků objektu modulu snap-in.  
  
```
GetResultViewType(
    LPOLESTR* ppViewType,
    long* pViewOptions);
```  
  
### <a name="parameters"></a>Parametry  
 *ppViewType*  
 [out] Ukazatel na adresu typu vrácené zobrazení.  
  
 *pViewOptions*  
 [out] Ukazatel na MMC_VIEW_OPTIONS výčet, který poskytuje možnosti určené vlastnící modul snap-in konzole. Tato hodnota může být jedna z následujících akcí:  
  
- MMC_VIEW_OPTIONS_NOLISTVIEWS = 0x00000001 informuje konzolu, nepoužívejte nabízí ten samý standardní seznam možností zobrazení v **zobrazení** nabídky. Umožňuje modulu snap-in k zobrazení vlastní vlastních zobrazení pouze v podokně výsledků. Toto je pouze možnost příznak definované v tuto chvíli.  
  
- MMC_VIEW_OPTIONS_NONE = 0 umožňuje zobrazit výchozí možnosti.  
  
##  <a name="getscopepaneinfo"></a>  CSnapInItemImpl::GetScopePaneInfo  
 Voláním této funkce načtete `SCOPEDATAITEM` strukturu modulu snap-in.  
  
```
GetScopePaneInfo (SCOPEDATAITEM* pScopeDataItem);
```  
  
### <a name="parameters"></a>Parametry  
 *pScopeDataItem*  
 [out] Ukazatel `SCOPEDATAITEM` struktury `CSnapInItemImpl` objektu.  
  
##  <a name="getresultpaneinfo"></a>  CSnapInItemImpl::GetResultPaneInfo  
 Voláním této funkce načtete `RESULTDATAITEM` strukturu modulu snap-in.  
  
```
GetResultPaneInfo (RESULTDATAITEM* pResultDataItem);
```  
  
### <a name="parameters"></a>Parametry  
 *pResultDataItem*  
 [out] Ukazatel `RESULTDATAITEM` struktury `CSnapInItemImpl` objektu.  
  
##  <a name="m_bstrdisplayname"></a>  CSnapInItemImpl::m_bstrDisplayName  
 Obsahuje řetězec zobrazený u položky uzlu.  
  
```
CComBSTR m_bstrDisplayName;
```  
  
##  <a name="m_scopedataitem"></a>  CSnapInItemImpl::m_scopeDataItem  
 `SCOPEDATAITEM` Struktura modul snap-in datového objektu.  
  
```
SCOPEDATAITEM m_scopeDataItem;
```  
  
##  <a name="m_resultdataitem"></a>  CSnapInItemImpl::m_resultDataItem  
 [RESULTDATAITEM](http://msdn.microsoft.com/library/aa815165) struktura modul snap-in datového objektu.  
  
```
RESULTDATAITEM m_resultDataItem;
```  
  
##  <a name="notify"></a>  CSnapInItemImpl::Notify  
 Volá se, když modul snap-in objektu je reagovali na ni uživatelem.  
  
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
 *event*  
 [in] Určuje akci provedenou uživatelem. Je možné následující oznámení:  
  
- MMCN_ACTIVATE odesílá se, když se okna aktivovat a deaktivovat.  
  
- MMCN_ADD_IMAGES odesílat přidat Image do podokna výsledků.  
  
- MMCN_BTN_CLICK posílají, když uživatel klikne jedno z tlačítek panelu nástrojů.  
  
- MMCN_CLICK posílají, když uživatel stiskne tlačítko myši na položku zobrazení seznamu.  
  
- MMCN_DBLCLICK posílají, když uživatel dvakrát klikne tlačítkem myši na položku zobrazení seznamu.  
  
- MMCN_DELETE odeslané k informování modulu snap-in, která má být objekt odstraněn.  
  
- MMCN_EXPAND zasílat do složky se musí rozšířit nebo zakázku.  
  
- MMCN_MINIMIZED odesílá se, když je okno se rychle minimalizovat nebo maximalizované.  
  
- MMCN_PROPERTY_CHANGE odesílat oznámení objekt modulu snap-in, který zobrazení objektu modulu snap-in se chystá změna.  
  
- MMCN_REMOVE_CHILDREN posílají, když modul snap-in musíte odstranit celý podstrom přidané pod určeného uzlu.  
  
- MMCN_RENAME odešle dotaz pro přejmenování při prvním a druhém provedete přejmenování.  
  
- MMCN_SELECT posílají, když je vybraná položka v podokně zobrazení oboru nebo výsledek.  
  
- MMCN_SHOW posílají, když vybraná nebo vybraná poprvé rozsah položky.  
  
- MMCN_VIEW_CHANGE posílají, když modul snap-in můžete aktualizovat všechna zobrazení když dojde ke změně.  
  
 *arg*  
 [in] Závisí na typu oznámení.  
  
 *Param*  
 [in] Závisí na typu oznámení.  
  
 *pComponentData*  
 [out] Ukazatel na objekt implementace `IComponentData`. Tento parametr hodnotu NULL, pokud není se předalo oznámení `IComponentData::Notify`.  
  
 *pComponent*  
 [out] Ukazatel na objekt, který implementuje `IComponent`. Tento parametr hodnotu NULL, pokud není se předalo oznámení `IComponent::Notify`.  
  
 *Typ*  
 [in] Určuje typ objektu. Může mít jednu z následujících hodnot:  
  
- CCT_SCOPE datový objekt oboru podokno kontextu.  
  
- CCT_RESULT datový objekt kontextu podokno výsledků.  
  
- CCT_SNAPIN_MANAGER datového objektu pro modul snap-in Správce kontextu.  
  
- CCT_UNINITIALIZED datový objekt je neplatného typu.  
  
##  <a name="querypagesfor"></a>  CSnapInItemImpl::QueryPagesFor  
 Volá se, pokud uzel modulu snap-in podporuje stránky vlastností.  
  
```
QueryPagesFor(DATA_OBJECT_TYPES type);
```  
  
##  <a name="setmenuinsertionflags"></a>  CSnapInItemImpl::SetMenuInsertionFlags  
 Voláním této funkce upravit příznaky vložení nabídky, určené *pInsertionAllowed*, pro objekt modulu snap-in.  
  
```
void SetMenuInsertionFlags(  
    bool bBeforeInsertion,
    long* pInsertionAllowed);
```  
  
### <a name="parameters"></a>Parametry  
 *bBeforeInsertion*  
 [in] Nenulové, pokud funkce by měla být volána před položky budou přidány do kontextové nabídky; jinak 0.  
  
 *pInsertionAllowed*  
 [out v] Identifikuje definované Microsoft Management Console MMC, položka nabídky vložení body, které lze použít. To může být kombinací následujících příznaků:  
  
- V horní části místní nabídka může být vložen CCM_INSERTIONALLOWED_TOP položky.  
  
- CCM_INSERTIONALLOWED_NEW položky může být vložen do podnabídky vytvořit nový.  
  
- V podnabídce úloh lze vložit CCM_INSERTIONALLOWED_TASK položky.  
  
- V nabídce Zobrazit panel nástrojů nebo v podnabídce zobrazení místní nabídky podokna výsledků lze vložit CCM_INSERTIONALLOWED_VIEW položky.  
  
### <a name="remarks"></a>Poznámky  
 Pokud vyvíjíte primární modul snap-in, můžete resetovat některý z příznaků vložení jako způsob, jak omezit druh položky nabídky, které můžete přidat rozšíření třetích stran. Například primární modul snap-in můžete vymazat příznak CCM_INSERTIONALLOWED_NEW pro zabránění přidávání vlastních vytvořit nové položky nabídky rozšíření.  
  
 By se neměly pokoušet provést nastavení bitů *pInsertionAllowed* , které byly původně vymazána. Budoucí verze konzoly MMC může pomocí bits není aktuálně definován, takže byste neměli měnit bitů, které nejsou aktuálně definován.  
  
##  <a name="settoolbarbuttoninfo"></a>  CSnapInItemImpl::SetToolbarButtonInfo  
 Voláním této funkce upravit všechny styly tlačítek panelu nástrojů, objektu modulu snap-in, před vytvořením panelu nástrojů.  
  
```
void SetToolbarButtonInfo(  
    UINT id,
    BYTE* fsState,
    BYTE* fsType);
```  
  
### <a name="parameters"></a>Parametry  
 *id*  
 [in] ID tlačítko panelu nástrojů, která se má nastavit.  
  
 *fsState*  
 [in] Příznaky stav tlačítka. Může být jeden nebo více z následujících akcí:  
  
- TBSTATE_CHECKED tlačítko stylu TBSTYLE_CHECKED a stisknutí se.  
  
- TBSTATE_ENABLED tlačítko přijímá vstup uživatele. Tlačítko, které nemá tento stav nepřijímá vstup uživatele a nejde aktivovat.  
  
- TBSTATE_HIDDEN tlačítko není viditelný a nemůže přijímat uživatelský vstup.  
  
- TBSTATE_INDETERMINATE tlačítko nejde aktivovat.  
  
- TBSTATE_PRESSED, které stisknutí tlačítka.  
  
- Konec řádku A TBSTATE_WRAP následuje tlačítka. Tlačítka musí mít také TBSTATE_ENABLED.  
  
 *fsType*  
 [in] Příznaky stav tlačítka. Může být jeden nebo více z následujících akcí:  
  
- TBSTYLE_BUTTON vytvoří standardní tlačítko.  
  
- Vytvoří TBSTYLE_CHECK tlačítko, které přepíná mezi stavů pressed a není stisknuta pokaždé, když uživatel na něj klikne. Je ve stavu při stisknutí tlačítka má jinou barvu pozadí.  
  
- Stisknutí TBSTYLE_CHECKGROUP vytvoří, které se stiskne tlačítko kontroly, který zůstává až do dalšího tlačítka ve skupině.  
  
- Stisknutí TBSTYLE_GROUP vytvoří, které stisknutí tlačítka, který zůstane až do dalšího tlačítka ve skupině.  
  
- TBSTYLE_SEP vytvoří oddělovač, poskytuje malé mezeru mezi skupinami tlačítko. Tlačítko, které má tento styl nepřijímá vstup uživatele.  
  
##  <a name="updatemenustate"></a>  CSnapInItemImpl::UpdateMenuState  
 Voláním této funkce Upravit položku nabídky, než je vložen do místní nabídky objektu modulu snap-in.  
  
```
void UpdateMenuState(  
    UINT id,
    LPTSTR pBuf,
    UINT* flags);
```  
  
### <a name="parameters"></a>Parametry  
 *id*  
 [in] ID položky nabídky, která se má nastavit.  
  
 *pBuf*  
 [in] Ukazatel na řetězec pro položky nabídky aktualizace.  
  
 *příznaky*  
 [in] Určuje příznaky nový stav. To může být kombinací následujících příznaků:  
  
- MF_POPUP Určuje, že se jedná o podnabídku v místní nabídce. Položky nabídky, body vložení a další podnabídek může přidat do podnabídky pomocí jeho `lCommandID` jako jejich `IInsertionPointID`.  
  
- MF_BITMAP a MF_OWNERDRAW tyto příznaky nejsou povolené a bude mít za následek E_INVALIDARG návratovou hodnotu.  
  
- MF_SEPARATOR kreslení vodorovné zřejmý. Pouze `IContextMenuProvider` může přidání položek nabídky s MF_SEPARATOR sadou.  
  
- MF_CHECKED zaškrtne políčko vedle položky nabídky.  
  
- Zakáže MF_DISABLED položku nabídky, nelze vybrat, ale příznak není šedé ho.  
  
- MF_ENABLED umožňuje položky nabídky, takže ho nejde ani zvolit, obnovení z šedě stavu.  
  
- MF_GRAYED zakáže položky nabídky graying ji proto nelze vybrat.  
  
- Stejné jako MF_MENUBREAK příznak pro panel nabídek MF_MENUBARBREAK funkce. Rozevírací nabídky, podnabídky nebo místní nabídku nového sloupce, který je oddělená od starý sloupec svislou čárou.  
  
- MF_MENUBREAK umístí položku na nový řádek (pro panel nabídek) nebo v novém sloupci (pro rozevírací nabídky, podnabídky nebo nabídku) bez oddělení sloupců.  
  
- MF_UNCHECKED neumístí zaškrtávací políčko vedle položky (výchozí).  
  
 Následující skupiny příznaky nelze použít společně:  
  
- MF_DISABLED MF_ENABLED a MF_GRAYED.  
  
- MF_MENUBARBREAK a MF_MENUBREAK.  
  
- MF_CHECKED a MF_UNCHECKED.  
  
##  <a name="updatetoolbarbutton"></a>  CSnapInItemImpl::UpdateToolbarButton  
 Voláním této funkce Upravit tlačítka panelu nástrojů, modul snap-in objektu, než se zobrazí.  
  
```
BOOL UpdateToolbarButton(UINT id, BYTE fsState);
```  
  
### <a name="parameters"></a>Parametry  
 *id*  
 Určuje ID tlačítko na panelu nástrojů tlačítko Aktualizovat.  
  
 *fsState*  
 Určuje stav tlačítka panelu nástrojů. Pokud tento stav je možné nastavit, vrátí hodnotu TRUE. To může být kombinací následujících příznaků:  
  
- POVOLIT tlačítko přijímá vstup uživatele. Tlačítko, které nemá tento stav nepřijímá vstup uživatele a nejde aktivovat.  
  
- ZAŠKRTNUTO tlačítko má styl zaškrtnutí a stisknutí se.  
  
- SKRYTÉ tlačítko není viditelný a nemůže přijímat uživatelský vstup.  
  
- NEURČITÁ tlačítko nejde aktivovat.  
  
- BUTTONPRESSED, které stisknutí tlačítka.  
  
## <a name="see-also"></a>Viz také  
 [Přehled tříd](../../atl/atl-class-overview.md)
