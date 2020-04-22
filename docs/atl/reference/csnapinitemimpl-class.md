---
title: Třída CSnapInItemImpl
ms.date: 11/04/2016
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
helpviewer_keywords:
- snap-ins, data items
- snap-ins, ATL support for
- CSnapInItemImpl class
- snap-ins
ms.assetid: 52caefbd-9eae-49b0-add2-d55524271aa7
ms.openlocfilehash: 04eeba0239789b9f3220b7bfece3eb41dc7f2826
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81746426"
---
# <a name="csnapinitemimpl-class"></a>Třída CSnapInItemImpl

Tato třída poskytuje metody pro implementaci objektu uzlu snap-in.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T, BOOL bIsExtension = FALSE>
class ATL_NO_VTABLE CSnapInItemImpl : public CSnapInItem
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, odvozená z `CSnapInItemImpl`.

*bIsExtension*<br/>
TRUE, pokud je objekt rozšířením modulu snap-in; jinak FALSE.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CSnapinItemimpl::csnapinitemimpl](#csnapinitemimpl)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[cSnapinItemimpl::AddItems](#addmenuitems)|Přidá položky nabídky do místní nabídky.|
|[cSnapinItemimpl::Příkaz](#command)|Volána konzolou, když je vybrána vlastní položka nabídky.|
|[cSnapinItemimpl::CreatePropertyPages](#createpropertypages)|Přidá stránky do seznamu vlastností modulu snap-in.|
|[cSnapinItemimpl::FillData](#filldata)|Zkopíruje informace o objektu modulu snap-in do zadaného datového proudu.|
|[CSnapinItemimpl::GetResultPaneInfo](#getresultpaneinfo)|Načte `RESULTDATAITEM` strukturu modulu snap-in.|
|[CSnapinItemimpl::GetResultViewType](#getresultviewtype)|Určuje typ zobrazení používaného podoknem výsledků.|
|[CSnapinItemimpl::GetScopePaneInfo](#getscopepaneinfo)|Načte `SCOPEDATAITEM` strukturu modulu snap-in.|
|[CSnapinItemimpl::Upozornit](#notify)|Volána konzolou upozornit snap-in akcí prováděných uživatelem.|
|[cSnapinItemimpl::QueryPagesFor](#querypagesfor)|Volána, aby zjistila, zda uzel modulu snap-in podporuje stránky vlastností.|
|[CSnapInItemImpl::SetMenuInsertionFlags](#setmenuinsertionflags)|Upraví příznaky vložení nabídky pro objekt modulu snap-in.|
|[CSnapInItemImpl::SetToolbarButtonInfo](#settoolbarbuttoninfo)|Nastaví informace o zadaném tlačítku panelu nástrojů.|
|[cSnapinItemimpl::UpdateMenuState](#updatemenustate)|Aktualizuje stav položky kontextové nabídky.|
|[CSnapInItemImpl::UpdateToolbarButton](#updatetoolbarbutton)|Aktualizuje stav zadaného tlačítka panelu nástrojů.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[CSnapInItemImpl::m_bstrDisplayName](#m_bstrdisplayname)|Název objektu modulu snap-in.|
|[CSnapInItemImpl::m_resultDataItem](#m_resultdataitem)|Struktura `RESULTDATAITEM` systému Windows `CSnapInItemImpl` používá objekt.|
|[CSnapInItemImpl::m_scopeDataItem](#m_scopedataitem)|Struktura `SCOPEDATAITEM` systému Windows `CSnapInItemImpl` používá objekt.|

## <a name="remarks"></a>Poznámky

`CSnapInItemImpl`Poskytuje základní implementaci pro objekt uzlu modulu snap-in, jako je například přidání položek nabídky a panelů nástrojů a předávání příkazů pro uzel modulu snap-in na příslušnou funkci obslužné rutiny. Tyto funkce jsou implementovány pomocí několika různých rozhraní a typy map. Výchozí implementace zpracovává oznámení odeslaná do objektu uzlu určením správné instance odvozené třídy a následným předáním zprávy do správné instance.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CSnapInItem`

`CSnapInItemImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsnap.h

## <a name="csnapinitemimpladdmenuitems"></a><a name="addmenuitems"></a>cSnapinItemimpl::AddItems

Tato metoda implementuje funkci Win32 [IExtendContextMenu::AddMenuItems](/windows/win32/api/mmc/nf-mmc-iextendcontextmenu-addmenuitems).

```
AddMenuItems(
    LPCONTEXTMENUCALLBACK piCallback,
    long* pInsertionAllowed,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>Parametry

*piCallback*<br/>
[v] Ukazatel na `IContextMenuCallback` který můžete přidat položky do místní nabídky.

*pVložení povoleno*<br/>
[dovnitř, ven] Identifikuje body vložení položky položky mmc (MMC) definované konzolou MMC, které lze použít. Může se jedná o kombinaci následujících příznaků:

- CCM_INSERTIONALLOWED_TOP Položky lze vložit do horní části kontextové nabídky.

- CCM_INSERTIONALLOWED_NEW položky lze vložit do podnabídky Vytvořit nové.

- CCM_INSERTIONALLOWED_TASK položky lze vložit do podnabídky Úkol.

- CCM_INSERTIONALLOWED_VIEW Položky lze vložit do nabídky zobrazení panelu nástrojů nebo do podnabídky Zobrazit v kontextové nabídce podokna výsledků.

*Typ*<br/>
[v] Určuje typ objektu. Může mít jednu z následujících hodnot:

- CCT_SCOPE Datový objekt pro kontext podokna oboru.

- CCT_RESULT Datový objekt pro kontext podokna výsledků.

- CCT_SNAPIN_MANAGER Datový objekt pro kontext správce modulu snap-in.

- CCT_UNINITIALIZED Datový objekt má neplatný typ.

## <a name="csnapinitemimplcommand"></a><a name="command"></a>cSnapinItemimpl::Příkaz

Tato metoda implementuje funkci Win32 [IExtendContextMenu::Command](/windows/win32/api/mmc/nf-mmc-iextendcontextmenu-command).

```
Command(long lCommandID, DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>Parametry

*id příkazu l*<br/>
[v] Určuje identifikátor příkazu položky nabídky.

*Typ*<br/>
[v] Určuje typ objektu. Může mít jednu z následujících hodnot:

- CCT_SCOPE Datový objekt pro kontext podokna oboru.

- CCT_RESULT Datový objekt pro kontext podokna výsledků.

- CCT_SNAPIN_MANAGER Datový objekt pro kontext správce modulu snap-in.

- CCT_UNINITIALIZED Datový objekt má neplatný typ.

## <a name="csnapinitemimplcreatepropertypages"></a><a name="createpropertypages"></a>cSnapinItemimpl::CreatePropertyPages

Tato metoda implementuje funkci [Win32 IExtendPropertySheet::CreatePropertyPages](/windows/win32/api/mmc/nn-mmc-iextendpropertysheet2).

```
CreatePropertyPages(
    LPPROPERTYSHEETCALLBACK lpProvider,
    long handle,
    IUnknown* pUnk,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>Parametry

*lpProvider*<br/>
[v] Ukazatel na `IPropertySheetCallback` rozhraní.

*Zpracování*<br/>
[v] Určuje popisovač používaný ke směrování MMCN_PROPERTY_CHANGE oznamovací zprávy do příslušné třídy dat.

*Punk*<br/>
[v] Ukazatel na `IExtendPropertySheet` rozhraní na objekt, který obsahuje informace o kontextu o uzlu.

*Typ*<br/>
[v] Určuje typ objektu. Může mít jednu z následujících hodnot:

- CCT_SCOPE Datový objekt pro kontext podokna oboru.

- CCT_RESULT Datový objekt pro kontext podokna výsledků.

- CCT_SNAPIN_MANAGER Datový objekt pro kontext správce modulu snap-in.

- CCT_UNINITIALIZED Datový objekt má neplatný typ.

## <a name="csnapinitemimplcsnapinitemimpl"></a><a name="csnapinitemimpl"></a>CSnapinItemimpl::csnapinitemimpl

Vytvoří `CSnapInItemImpl` objekt.

```
CSnapInItemImpl();
```

## <a name="csnapinitemimplfilldata"></a><a name="filldata"></a>cSnapinItemimpl::FillData

Tato funkce je volána k načtení informací o položce.

```
FillData(CLIPFORMAT cf, LPSTREAM pStream);
```

### <a name="parameters"></a>Parametry

*Viz*<br/>
[v] Formát (text, formát RTF nebo formátovaný text s položkami OLE) schránky.

*pStream*<br/>
[v] Ukazatel na datový proud obsahující data objektu.

### <a name="remarks"></a>Poznámky

Chcete-li tuto funkci správně implementovat, zkopírujte správné informace do datového proudu (*pStream*) v závislosti na formátu schránky označeném *cf*.

## <a name="csnapinitemimplgetresultviewtype"></a><a name="getresultviewtype"></a>CSnapinItemimpl::GetResultViewType

Voláním této funkce načtěte typ zobrazení pro podokno výsledků objektu modulu snap-in.

```
GetResultViewType(
    LPOLESTR* ppViewType,
    long* pViewOptions);
```

### <a name="parameters"></a>Parametry

*ppViewType*<br/>
[out] Ukazatel na adresu vráceného typu zobrazení.

*pViewOptions*<br/>
[out] Ukazatel na výčet MMC_VIEW_OPTIONS, který poskytuje konzoli možnosti určené vlastnící modul snap-in. Tato hodnota může být jedna z následujících:

- MMC_VIEW_OPTIONS_NOLISTVIEWS = 0x00000001 Říká konzoli, aby se zdržela prezentace standardních možností zobrazení seznamu v nabídce **Zobrazení.** Umožňuje modulu snap-in zobrazit vlastní zobrazení pouze v podokně zobrazení výsledků. Toto je pouze příznak možnosti definované v tomto okamžiku.

- MMC_VIEW_OPTIONS_NONE = 0 Umožňuje výchozí možnosti zobrazení.

## <a name="csnapinitemimplgetscopepaneinfo"></a><a name="getscopepaneinfo"></a>CSnapinItemimpl::GetScopePaneInfo

Volání této funkce `SCOPEDATAITEM` načíst strukturu modulu snap-in.

```
GetScopePaneInfo (SCOPEDATAITEM* pScopeDataItem);
```

### <a name="parameters"></a>Parametry

*pScopeDataItem*<br/>
[out] Ukazatel na `SCOPEDATAITEM` strukturu objektu. `CSnapInItemImpl`

## <a name="csnapinitemimplgetresultpaneinfo"></a><a name="getresultpaneinfo"></a>CSnapinItemimpl::GetResultPaneInfo

Volání této funkce `RESULTDATAITEM` načíst strukturu modulu snap-in.

```
GetResultPaneInfo (RESULTDATAITEM* pResultDataItem);
```

### <a name="parameters"></a>Parametry

*pResultDataItem*<br/>
[out] Ukazatel na `RESULTDATAITEM` strukturu objektu. `CSnapInItemImpl`

## <a name="csnapinitemimplm_bstrdisplayname"></a><a name="m_bstrdisplayname"></a>CSnapInItemImpl::m_bstrDisplayName

Obsahuje řetězec zobrazený pro položku uzlu.

```
CComBSTR m_bstrDisplayName;
```

## <a name="csnapinitemimplm_scopedataitem"></a><a name="m_scopedataitem"></a>CSnapInItemImpl::m_scopeDataItem

Struktura `SCOPEDATAITEM` datového objektu modulu snap-in.

```
SCOPEDATAITEM m_scopeDataItem;
```

## <a name="csnapinitemimplm_resultdataitem"></a><a name="m_resultdataitem"></a>CSnapInItemImpl::m_resultDataItem

Struktura [RESULTDATAITEM](/windows/win32/api/mmc/ns-mmc-resultdataitem) datového objektu modulu snap-in.

```
RESULTDATAITEM m_resultDataItem;
```

## <a name="csnapinitemimplnotify"></a><a name="notify"></a>CSnapinItemimpl::Upozornit

Volána při akceptovanou objektem modulu snap-in uživatelem.

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

*event*<br/>
[v] Identifikuje akci přijatou uživatelem. Jsou možná následující oznámení:

- MMCN_ACTIVATE Odesláno, když je okno aktivováno a deaktivováno.

- MMCN_ADD_IMAGES Odesláno pro přidání obrázků do podokna výsledků.

- MMCN_BTN_CLICK Odesláno, když uživatel klepne na jedno z tlačítek panelu nástrojů.

- MMCN_CLICK Odesláno, když uživatel klepne na tlačítko myši v položce zobrazení seznamu.

- MMCN_DBLCLICK Odesláno, když uživatel dvakrát klikne na tlačítko myši v položce zobrazení seznamu.

- MMCN_DELETE Odesláno, aby informoval modul snap-in, že objekt by měl být odstraněn.

- MMCN_EXPAND Odesláno, když je potřeba složku rozbalit nebo smluvně smrštit.

- MMCN_MINIMIZED Odesláno, když je okno minimalizováno nebo maximalizováno.

- MMCN_PROPERTY_CHANGE Odesláno, aby upozornil objekt modulu snap-in, že se změní zobrazení objektu modulu snap-in.

- MMCN_REMOVE_CHILDREN Odesláno, když modul snap-in musí odstranit celý podstrom, který přidal pod zadaný uzel.

- MMCN_RENAME Odesláno poprvé dotaz na přejmenování a podruhé provést přejmenování.

- MMCN_SELECT Odesláno, pokud je vybraná položka v podokně zobrazení oboru nebo výsledků.

- MMCN_SHOW Odesláno, když je položka oboru vybrána nebo zrušena poprvé.

- MMCN_VIEW_CHANGE Odesláno, když může modul snap-in aktualizovat všechna zobrazení, když dojde ke změně.

*Arg*<br/>
[v] Závisí na typu oznámení.

*Param*<br/>
[v] Závisí na typu oznámení.

*pComponentData*<br/>
[out] Ukazatel na objekt, `IComponentData`který implementuje . Tento parametr je NULL, pokud oznámení `IComponentData::Notify`není předáván z .

*pKomponenta*<br/>
[out] Ukazatel na objekt, který `IComponent`implementuje . Tento parametr je NULL, pokud oznámení `IComponent::Notify`není předáván z .

*Typ*<br/>
[v] Určuje typ objektu. Může mít jednu z následujících hodnot:

- CCT_SCOPE Datový objekt pro kontext podokna oboru.

- CCT_RESULT Datový objekt pro kontext podokna výsledků.

- CCT_SNAPIN_MANAGER Datový objekt pro kontext správce modulu snap-in.

- CCT_UNINITIALIZED Datový objekt má neplatný typ.

## <a name="csnapinitemimplquerypagesfor"></a><a name="querypagesfor"></a>cSnapinItemimpl::QueryPagesFor

Volána, aby zjistila, zda uzel modulu snap-in podporuje stránky vlastností.

```
QueryPagesFor(DATA_OBJECT_TYPES type);
```

## <a name="csnapinitemimplsetmenuinsertionflags"></a><a name="setmenuinsertionflags"></a>CSnapInItemImpl::SetMenuInsertionFlags

Volání této funkce upravit příznaky vložení nabídky, určené *pInsertionAllowed*, pro objekt modulu snap-in.

```cpp
void SetMenuInsertionFlags(
    bool bBeforeInsertion,
    long* pInsertionAllowed);
```

### <a name="parameters"></a>Parametry

*bBeforeInsertion*<br/>
[v] Nenulová, pokud by funkce měla být volána před přidáním položek do kontextové nabídky; jinak 0.

*pVložení povoleno*<br/>
[dovnitř, ven] Identifikuje body vložení položky položky mmc (MMC) definované konzolou MMC, které lze použít. Může se jedná o kombinaci následujících příznaků:

- CCM_INSERTIONALLOWED_TOP Položky lze vložit do horní části kontextové nabídky.

- CCM_INSERTIONALLOWED_NEW položky lze vložit do podnabídky Vytvořit nové.

- CCM_INSERTIONALLOWED_TASK položky lze vložit do podnabídky Úkol.

- CCM_INSERTIONALLOWED_VIEW Položky lze vložit do nabídky zobrazení panelu nástrojů nebo do podnabídky Zobrazit v kontextové nabídce podokna výsledků.

### <a name="remarks"></a>Poznámky

Pokud vyvíjíte primární modul snap-in, můžete obnovit libovolný z příznaků vložení jako způsob omezení druhu položek nabídky, které může rozšíření jiného výrobce přidat. Primární modul snap-in může například vymazat příznak CCM_INSERTIONALLOWED_NEW, aby rozšíření nemohla přidávat vlastní položky nabídky Vytvořit nové.

Neměli byste se pokoušet nastavit bity v *pInsertionAllowed,* které byly původně vymazány. Budoucí verze konzoly MMC mohou používat bity, které nejsou aktuálně definovány, takže byste neměli měnit bity, které aktuálně nejsou definovány.

## <a name="csnapinitemimplsettoolbarbuttoninfo"></a><a name="settoolbarbuttoninfo"></a>CSnapInItemImpl::SetToolbarButtonInfo

Voláním této funkce můžete před vytvořením panelu nástrojů upravit všechny styly tlačítek panelu nástrojů.

```cpp
void SetToolbarButtonInfo(
    UINT id,
    BYTE* fsState,
    BYTE* fsType);
```

### <a name="parameters"></a>Parametry

*Id*<br/>
[v] ID tlačítka panelu nástrojů, které má být nastaveno.

*fsStát*<br/>
[v] Příznaky stavu tlačítka. Může být jeden nebo více z následujících:

- TBSTATE_CHECKED Tlačítko má TBSTYLE_CHECKED styl a je stisknuto.

- TBSTATE_ENABLED Tlačítko přijímá vstup uživatele. Tlačítko, které nemá tento stav nepřijímá vstup uživatele a je šedě.

- TBSTATE_HIDDEN Tlačítko není viditelné a nemůže přijímat vstup uživatele.

- TBSTATE_INDETERMINATE Tlačítko je šedé.

- TBSTATE_PRESSED Stisknete tlačítko.

- TBSTATE_WRAP Za tlačítkem následuje zalomení řádku. Tlačítko musí mít také TBSTATE_ENABLED.

*fsTyp*<br/>
[v] Příznaky stavu tlačítka. Může být jeden nebo více z následujících:

- TBSTYLE_BUTTON Vytvoří standardní tlačítko.

- TBSTYLE_CHECK Vytvoří tlačítko, které přepíná mezi stisknuté a nestisknuté stavy pokaždé, když na něj uživatel klepne. Tlačítko má jinou barvu pozadí, když je v stisknutém stavu.

- TBSTYLE_CHECKGROUP Vytvoří kontrolní tlačítko, které zůstane stisknuto, dokud nestisknete jiné tlačítko ve skupině.

- TBSTYLE_GROUP Vytvoří tlačítko, které zůstane stisknuto, dokud nestisknete jiné tlačítko ve skupině.

- TBSTYLE_SEP Vytvoří oddělovač, který poskytuje malou mezeru mezi skupinami tlačítek. Tlačítko, které má tento styl neobdrží vstup uživatele.

## <a name="csnapinitemimplupdatemenustate"></a><a name="updatemenustate"></a>cSnapinItemimpl::UpdateMenuState

Voláním této funkce upravte položku nabídky před vložením do kontextové nabídky objektu modulu snap-in.

```cpp
void UpdateMenuState(
    UINT id,
    LPTSTR pBuf,
    UINT* flags);
```

### <a name="parameters"></a>Parametry

*Id*<br/>
[v] ID položky nabídky, která má být nastavena.

*pBuf*<br/>
[v] Ukazatel na řetězec pro položku nabídky, která má být aktualizována.

*příznaky*<br/>
[v] Určuje nové příznaky stavu. Může se jedná o kombinaci následujících příznaků:

- MF_POPUP Určuje, že se jedná o podnabídku v rámci kontextové nabídky. Položky nabídky, kurzor a další podnabídky mohou být přidány `lCommandID` do `IInsertionPointID`této podnabídky pomocí aplikace .

- MF_BITMAP a MF_OWNERDRAW Tyto příznaky nejsou povoleny a bude mít za následek vrácenou hodnotu E_INVALIDARG.

- MF_SEPARATOR nakreslí vodorovnou dělicí čáru. Pouze `IContextMenuProvider` je povoleno přidávat položky nabídky s MF_SEPARATOR nastavena.

- MF_CHECKED Zaškrtne značku vedle položky nabídky.

- MF_DISABLED Zakáže položku nabídky, takže ji nelze vybrat, ale příznak ji nešedne.

- MF_ENABLED Povolí položku nabídky, aby ji bylo možné vybrat, a obnoví ji ze šedě.

- MF_GRAYED Zakáže položku nabídky a zašedlí ji, takže ji nelze vybrat.

- MF_MENUBARBREAK Funguje stejně jako příznak MF_MENUBREAK pro řádek nabídek. V rozevírací nabídce, podnabídce nebo místní nabídce je nový sloupec oddělen od starého sloupce svislou čárou.

- MF_MENUBREAK Umístí položku na nový řádek (pro řádek nabídek) nebo do nového sloupce (pro rozevírací nabídku, podnabídku nebo místní nabídku) bez oddělení sloupců.

- MF_UNCHECKED Nezaškrtá v ní (výchozí).

Následující skupiny příznaků nelze použít společně:

- MF_DISABLED, MF_ENABLED a MF_GRAYED.

- MF_MENUBARBREAK a MF_MENUBREAK.

- MF_CHECKED a MF_UNCHECKED.

## <a name="csnapinitemimplupdatetoolbarbutton"></a><a name="updatetoolbarbutton"></a>CSnapInItemImpl::UpdateToolbarButton

Voláním této funkce můžete před zobrazením upravit tlačítko panelu nástrojů objektu přichycení.

```
BOOL UpdateToolbarButton(UINT id, BYTE fsState);
```

### <a name="parameters"></a>Parametry

*Id*<br/>
Určuje ID tlačítka tlačítka panelu nástrojů, které má být aktualizováno.

*fsStát*<br/>
Určuje stav tlačítka panelu nástrojů. Pokud má být tento stav nastaven, vraťte hodnotu TRUE. Může se jedná o kombinaci následujících příznaků:

- POVOLENO Tlačítko přijímá vstup uživatele. Tlačítko, které nemá tento stav nepřijímá vstup uživatele a je šedě.

- KONTROLA Tlačítko má styl CHECKED a je stisknuto.

- SKRYTÉ Tlačítko není viditelné a nemůže přijímat vstup uživatele.

- NEURČITNe, tlačítko je šedé.

- BUTTONPRESSED Tlačítko je stisknuto.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
