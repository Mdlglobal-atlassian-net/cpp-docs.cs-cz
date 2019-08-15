---
title: CSnapInItemImpl – třída
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
ms.openlocfilehash: a9ebcf8827d79a9613ce14251d361dd607aa6af3
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496549"
---
# <a name="csnapinitemimpl-class"></a>CSnapInItemImpl – třída

Tato třída poskytuje metody pro implementaci objektu uzlu modulu snap-in.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T, BOOL bIsExtension = FALSE>
class ATL_NO_VTABLE CSnapInItemImpl : public CSnapInItem
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, která je `CSnapInItemImpl`odvozena z.

*bIsExtension*<br/>
TRUE, pokud je objekt rozšířením snap-in; v opačném případě FALSE.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[CSnapInItemImpl::CSnapInItemImpl](#csnapinitemimpl)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CSnapInItemImpl::AddMenuItems](#addmenuitems)|Přidá položky nabídky do kontextové nabídky.|
|[CSnapInItemImpl::Command](#command)|Volá se konzolou, když je vybraná vlastní položka nabídky.|
|[CSnapInItemImpl::CreatePropertyPages](#createpropertypages)|Přidá stránky do seznamu vlastností modulu snap-in.|
|[CSnapInItemImpl::FillData](#filldata)|Zkopíruje informace o objektu modulu snap-in do zadaného datového proudu.|
|[CSnapInItemImpl::GetResultPaneInfo](#getresultpaneinfo)|`RESULTDATAITEM` Načte strukturu modulu snap-in.|
|[CSnapInItemImpl::GetResultViewType](#getresultviewtype)|Určuje typ zobrazení, které je používáno v podokně výsledků.|
|[CSnapInItemImpl::GetScopePaneInfo](#getscopepaneinfo)|`SCOPEDATAITEM` Načte strukturu modulu snap-in.|
|[CSnapInItemImpl::Notify](#notify)|Volá se konzolou, která upozorní modul snap-in akce provedené uživatelem.|
|[CSnapInItemImpl::QueryPagesFor](#querypagesfor)|Volá se, aby se zobrazilo, jestli uzel modulu snap-in podporuje stránky vlastností.|
|[CSnapInItemImpl::SetMenuInsertionFlags](#setmenuinsertionflags)|Upraví příznaky vložení nabídky pro objekt snap-in.|
|[CSnapInItemImpl::SetToolbarButtonInfo](#settoolbarbuttoninfo)|Nastaví informace o určeném tlačítku panelu nástrojů.|
|[CSnapInItemImpl::UpdateMenuState](#updatemenustate)|Aktualizuje stav položky místní nabídky.|
|[CSnapInItemImpl::UpdateToolbarButton](#updatetoolbarbutton)|Aktualizuje stav zadaného tlačítka panelu nástrojů.|

### <a name="public-data-members"></a>Veřejné datové členy

|Name|Popis|
|----------|-----------------|
|[CSnapInItemImpl::m_bstrDisplayName](#m_bstrdisplayname)|Název objektu modulu snap-in.|
|[CSnapInItemImpl::m_resultDataItem](#m_resultdataitem)|Struktura systému `RESULTDATAITEM` Windows, kterou `CSnapInItemImpl` objekt používá.|
|[CSnapInItemImpl::m_scopeDataItem](#m_scopedataitem)|Struktura systému `SCOPEDATAITEM` Windows, kterou `CSnapInItemImpl` objekt používá.|

## <a name="remarks"></a>Poznámky

`CSnapInItemImpl`poskytuje základní implementaci pro objekt uzlu modulu snap-in, například přidání položek nabídky a panelů nástrojů a příkazy pro přesměrování pro uzel modulu snap-in do příslušné funkce obslužné rutiny. Tyto funkce jsou implementovány pomocí několika různých rozhraní a typů map. Výchozí implementace zpracovává oznámení odeslaná objektu uzlu určením správné instance odvozené třídy a předáním zprávy do správné instance.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`CSnapInItem`

`CSnapInItemImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsnap. h

##  <a name="addmenuitems"></a>CSnapInItemImpl::AddMenuItems

Tato metoda implementuje funkci Win32 [IExtendContextMenu:: AddMenuItems](/windows/win32/api/mmc/nf-mmc-iextendcontextmenu-addmenuitems).

```
AddMenuItems(
    LPCONTEXTMENUCALLBACK piCallback,
    long* pInsertionAllowed,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>Parametry

*piCallback*<br/>
pro Ukazatel na `IContextMenuCallback` , který může přidat položky do kontextové nabídky.

*pInsertionAllowed*<br/>
[in, out] Identifikuje body vkládání v nabídce (Microsoft Management Console) (MMC), které se dají použít. Může se jednat o kombinaci následujících příznaků:

- CCM_INSERTIONALLOWED_TOP položky mohou být vloženy do horní části místní nabídky.

- CCM_INSERTIONALLOWED_NEW položky mohou být vloženy do podnabídky Vytvořit novou.

- Do podnabídky Task lze vkládat CCM_INSERTIONALLOWED_TASK položky.

- Položky CCM_INSERTIONALLOWED_VIEW lze vložit v nabídce zobrazení panelu nástrojů nebo v místní nabídce zobrazení v podokně výsledků.

*type*<br/>
pro Určuje typ objektu. Může mít jednu z následujících hodnot:

- Datový objekt CCT_SCOPE pro kontext podokna oboru

- Datový objekt CCT_RESULT pro kontext podokna výsledků

- Datový objekt CCT_SNAPIN_MANAGER pro kontext Správce modulu snap-in

- Datový objekt CCT_UNINITIALIZED je neplatného typu.

##  <a name="command"></a>CSnapInItemImpl:: – příkaz

Tato metoda implementuje funkci Win32 [IExtendContextMenu:: Command](/windows/win32/api/mmc/nf-mmc-iextendcontextmenu-command).

```
Command(long lCommandID, DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>Parametry

*lCommandID*<br/>
pro Určuje identifikátor příkazu pro položku nabídky.

*type*<br/>
pro Určuje typ objektu. Může mít jednu z následujících hodnot:

- Datový objekt CCT_SCOPE pro kontext podokna oboru

- Datový objekt CCT_RESULT pro kontext podokna výsledků

- Datový objekt CCT_SNAPIN_MANAGER pro kontext Správce modulu snap-in

- Datový objekt CCT_UNINITIALIZED je neplatného typu.

##  <a name="createpropertypages"></a>  CSnapInItemImpl::CreatePropertyPages

Tato metoda implementuje funkci Win32 [IExtendPropertySheet:: CreatePropertyPages](/windows/win32/api/mmc/nn-mmc-iextendpropertysheet2).

```
CreatePropertyPages(
    LPPROPERTYSHEETCALLBACK lpProvider,
    long handle,
    IUnknown* pUnk,
    DATA_OBJECT_TYPES type);
```

### <a name="parameters"></a>Parametry

*lpProvider*<br/>
pro Ukazatel na `IPropertySheetCallback` rozhraní.

*popisovač*<br/>
pro Určuje popisovač použitý ke směrování zprávy oznámení MMCN_PROPERTY_CHANGE do příslušné datové třídy.

*pUnk*<br/>
pro Ukazatel na `IExtendPropertySheet` rozhraní objektu, který obsahuje kontextové informace o uzlu.

*type*<br/>
pro Určuje typ objektu. Může mít jednu z následujících hodnot:

- Datový objekt CCT_SCOPE pro kontext podokna oboru

- Datový objekt CCT_RESULT pro kontext podokna výsledků

- Datový objekt CCT_SNAPIN_MANAGER pro kontext Správce modulu snap-in

- Datový objekt CCT_UNINITIALIZED je neplatného typu.

##  <a name="csnapinitemimpl"></a>CSnapInItemImpl::CSnapInItemImpl

`CSnapInItemImpl` Vytvoří objekt.

```
CSnapInItemImpl();
```

##  <a name="filldata"></a>CSnapInItemImpl::FillData

Tato funkce se volá, aby se načetly informace o položce.

```
FillData(CLIPFORMAT cf, LPSTREAM pStream);
```

### <a name="parameters"></a>Parametry

*cf*<br/>
pro Formát (text, formátovaný text nebo formátovaný text s položkami OLE) schránky.

*pStream*<br/>
pro Ukazatel na datový proud obsahující data objektu.

### <a name="remarks"></a>Poznámky

Pro správnou implementaci této funkce zkopírujte do datového proudu správné informace (*pStream*), a to v závislosti na formátu schránky, který označuje *CF*.

##  <a name="getresultviewtype"></a>  CSnapInItemImpl::GetResultViewType

Voláním této funkce načtete typ zobrazení pro podokno výsledků objektu snap-in.

```
GetResultViewType(
    LPOLESTR* ppViewType,
    long* pViewOptions);
```

### <a name="parameters"></a>Parametry

*ppViewType*<br/>
mimo Ukazatel na adresu vráceného typu zobrazení.

*pViewOptions*<br/>
mimo Ukazatel na výčet MMC_VIEW_OPTIONS, který poskytuje konzolu s možnostmi určenými vlastním modulem snap-in. Tato hodnota může být jedna z následujících:

- MMC_VIEW_OPTIONS_NOLISTVIEWS = 0x00000001 dává konzole pokyn, aby v nabídce **zobrazení** nezobrazovala standardní možnosti zobrazení seznamu. Umožňuje modulu snap-in zobrazit vlastní zobrazení pouze v podokně zobrazení výsledků. Toto je jediný příznak možnosti, který je v tuto chvíli definován.

- MMC_VIEW_OPTIONS_NONE = 0 povoluje výchozí možnosti zobrazení.

##  <a name="getscopepaneinfo"></a>CSnapInItemImpl::GetScopePaneInfo

Voláním této funkce načtete `SCOPEDATAITEM` strukturu modulu snap-in.

```
GetScopePaneInfo (SCOPEDATAITEM* pScopeDataItem);
```

### <a name="parameters"></a>Parametry

*pScopeDataItem*<br/>
mimo Ukazatel na `SCOPEDATAITEM` strukturu `CSnapInItemImpl` objektu.

##  <a name="getresultpaneinfo"></a>CSnapInItemImpl::GetResultPaneInfo

Voláním této funkce načtete `RESULTDATAITEM` strukturu modulu snap-in.

```
GetResultPaneInfo (RESULTDATAITEM* pResultDataItem);
```

### <a name="parameters"></a>Parametry

*pResultDataItem*<br/>
mimo Ukazatel na `RESULTDATAITEM` strukturu `CSnapInItemImpl` objektu.

##  <a name="m_bstrdisplayname"></a>  CSnapInItemImpl::m_bstrDisplayName

Obsahuje řetězec zobrazený pro položku uzlu.

```
CComBSTR m_bstrDisplayName;
```

##  <a name="m_scopedataitem"></a>  CSnapInItemImpl::m_scopeDataItem

`SCOPEDATAITEM` Struktura datového objektu modulu snap-in.

```
SCOPEDATAITEM m_scopeDataItem;
```

##  <a name="m_resultdataitem"></a>  CSnapInItemImpl::m_resultDataItem

Struktura [RESULTDATAITEM](/windows/win32/api/mmc/ns-mmc-resultdataitem) datového objektu modulu snap-in.

```
RESULTDATAITEM m_resultDataItem;
```

##  <a name="notify"></a>CSnapInItemImpl:: Notify

Volá se, když uživatel přijme objekt modulu snap-in.

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
pro Identifikuje akci provedenou uživatelem. Je možné, že jsou k dispozici následující oznámení:

- MMCN_ACTIVATE se pošle, když se aktivuje a deaktivuje okno.

- MMCN_ADD_IMAGES odeslána pro přidání obrázků do podokna výsledků.

- MMCN_BTN_CLICK se odešle, když uživatel klikne na některé z tlačítek panelu nástrojů.

- MMCN_CLICK se pošle, když uživatel klikne na tlačítko myši na položce zobrazení seznamu.

- MMCN_DBLCLICK se pošle, když uživatel dvakrát klikne na tlačítko myši na položce zobrazení seznamu.

- MMCN_DELETE odeslána pro informování modulu snap-in, že by měl být objekt smazán.

- MMCN_EXPAND se posílá, když je potřeba rozbalit nebo sbalit složku.

- MMCN_MINIMIZED se posílá při minimalizaci nebo maximalizaci okna.

- MMCN_PROPERTY_CHANGE odeslána pro upozornění objektu modulu snap-in, který se chystá změnit zobrazení objektu modulu snap-in.

- MMCN_REMOVE_CHILDREN se pošle, když se modul snap-in odstraní celý podstrom, který se přidal pod zadaný uzel.

- MMCN_RENAME odesílá první dotaz na přejmenování a druhý čas k přejmenování.

- MMCN_SELECT odeslána, když je vybrána položka v podokně rozsah nebo zobrazení výsledků.

- MMCN_SHOW odesílá se při prvním výběru nebo výběru položky oboru.

- MMCN_VIEW_CHANGE se odesílá, když modul snap-in může aktualizovat všechna zobrazení, když dojde ke změně.

*ARG*<br/>
pro Závisí na typu oznámení.

*param*<br/>
pro Závisí na typu oznámení.

*pComponentData*<br/>
mimo Ukazatel na implementaci `IComponentData`objektu. Tento parametr má hodnotu NULL, pokud oznámení není předáváno `IComponentData::Notify`.

*pComponent*<br/>
mimo Ukazatel na objekt, který implementuje `IComponent`. Tento parametr má hodnotu NULL, pokud oznámení není předáváno `IComponent::Notify`.

*type*<br/>
pro Určuje typ objektu. Může mít jednu z následujících hodnot:

- Datový objekt CCT_SCOPE pro kontext podokna oboru

- Datový objekt CCT_RESULT pro kontext podokna výsledků

- Datový objekt CCT_SNAPIN_MANAGER pro kontext Správce modulu snap-in

- Datový objekt CCT_UNINITIALIZED je neplatného typu.

##  <a name="querypagesfor"></a>  CSnapInItemImpl::QueryPagesFor

Volá se, aby se zobrazilo, jestli uzel modulu snap-in podporuje stránky vlastností.

```
QueryPagesFor(DATA_OBJECT_TYPES type);
```

##  <a name="setmenuinsertionflags"></a>  CSnapInItemImpl::SetMenuInsertionFlags

Voláním této funkce upravíte příznaky vložení nabídky určené parametrem *pInsertionAllowed*pro objekt modulu snap-in.

```
void SetMenuInsertionFlags(
    bool bBeforeInsertion,
    long* pInsertionAllowed);
```

### <a name="parameters"></a>Parametry

*bBeforeInsertion*<br/>
pro Nenulová, pokud by měla být funkce volána před přidáním položek do místní nabídky; v opačném případě 0.

*pInsertionAllowed*<br/>
[in, out] Identifikuje body vkládání v nabídce (Microsoft Management Console) (MMC), které se dají použít. Může se jednat o kombinaci následujících příznaků:

- CCM_INSERTIONALLOWED_TOP položky mohou být vloženy do horní části místní nabídky.

- CCM_INSERTIONALLOWED_NEW položky mohou být vloženy do podnabídky Vytvořit novou.

- Do podnabídky Task lze vkládat CCM_INSERTIONALLOWED_TASK položky.

- Položky CCM_INSERTIONALLOWED_VIEW lze vložit v nabídce zobrazení panelu nástrojů nebo v místní nabídce zobrazení v podokně výsledků.

### <a name="remarks"></a>Poznámky

Pokud vyvíjíte primární modul snap-in, můžete resetovat libovolné příznaky vložení způsobem, který omezí druh položek nabídky, které může rozšíření třetích stran přidat. Například primární modul snap-in může Vymazat příznak CCM_INSERTIONALLOWED_NEW, aby rozšíření nemohlo přidat vlastní položky nabídky vytvořit nové.

Neměli byste se pokoušet o nastavení bitů v *pInsertionAllowed* , které byly původně smazány. Budoucí verze MMC můžou používat službu BITS, která není aktuálně definována, takže byste neměli měnit bity, které aktuálně nejsou definovány.

##  <a name="settoolbarbuttoninfo"></a>CSnapInItemImpl::SetToolbarButtonInfo

Voláním této funkce upravíte libovolné styly tlačítek panelu nástrojů objektu snap-in před vytvořením panelu nástrojů.

```
void SetToolbarButtonInfo(
    UINT id,
    BYTE* fsState,
    BYTE* fsType);
```

### <a name="parameters"></a>Parametry

*id*<br/>
pro ID tlačítka panelu nástrojů, které se má nastavit

*fsState*<br/>
pro Příznaky stavu tlačítka Může se jednat o jednu nebo více z následujících možností:

- TBSTATE_CHECKED tlačítko má styl TBSTYLE_CHECKED a je stisknuto.

- TBSTATE_ENABLED tlačítko akceptuje vstup uživatele. Tlačítko, které nemá tento stav, nepřijímá vstup uživatele a je šedě.

- TBSTATE_HIDDEN tlačítko není viditelné a nemůže přijmout uživatelský vstup.

- TBSTATE_INDETERMINATE tlačítko je šedé.

- TBSTATE_PRESSED, že se stiskne tlačítko.

- TBSTATE_WRAP zalomení řádku za tlačítkem. Tlačítko musí mít také TBSTATE_ENABLED.

*fsType*<br/>
pro Příznaky stavu tlačítka Může se jednat o jednu nebo více z následujících možností:

- TBSTYLE_BUTTON vytvoří standardní tlačítko pro vložení.

- TBSTYLE_CHECK vytvoří tlačítko, které přepíná mezi stavem stisknuto a nestisknutí pokaždé, když na něj uživatel klikne. Tlačítko má jinou barvu pozadí, když je ve stisknutém stavu.

- TBSTYLE_CHECKGROUP vytvoří tlačítko pro kontrolu, které zůstane stisknuté, dokud se nestiskne jiné tlačítko ve skupině.

- TBSTYLE_GROUP vytvoří tlačítko, které zůstane stisknuté, dokud se nestiskne jiné tlačítko ve skupině.

- TBSTYLE_SEP vytvoří oddělovač, který zadává malou mezeru mezi skupinami tlačítek. Tlačítko, které má tento styl, nepřijímá vstup uživatele.

##  <a name="updatemenustate"></a>CSnapInItemImpl::UpdateMenuState

Voláním této funkce upravíte položku nabídky předtím, než je vložena do kontextové nabídky objektu modulu snap-in.

```
void UpdateMenuState(
    UINT id,
    LPTSTR pBuf,
    UINT* flags);
```

### <a name="parameters"></a>Parametry

*id*<br/>
pro ID položky nabídky, která se má nastavit

*pBuf*<br/>
pro Ukazatel na řetězec pro položku nabídky, která má být aktualizována.

*Flag*<br/>
pro Určuje nové příznaky stavu. Může se jednat o kombinaci následujících příznaků:

- MF_POPUP určuje, že se jedná o podnabídku v místní nabídce. Položky nabídky, body vložení a další podnabídky mohou být přidány do této podnabídky pomocí jejího `lCommandID`. `IInsertionPointID`

- MF_BITMAP a MF_OWNERDRAW tyto příznaky nejsou povoleny a výsledkem bude návratová hodnota E_INVALIDARG.

- MF_SEPARATOR nakreslí horizontální dělicí čáru. Přidávání `IContextMenuProvider` položek nabídky se MF_SEPARATOR sadou je povolené jenom v případě, že je povolený.

- MF_CHECKED umístí značku zaškrtnutí vedle položky nabídky.

- MF_DISABLED zakáže položku nabídky, takže ji nelze vybrat, ale příznak je nešedý.

- MF_ENABLED povolí položku nabídky, aby ji bylo možné vybrat a obnovit z jejího nemonitorovaného stavu.

- MF_GRAYED zakáže položku nabídky, která je šedá, takže ji nelze vybrat.

- MF_MENUBARBREAK funguje stejně jako příznak MF_MENUBREAK pro panel nabídek. V případě rozevírací nabídky, podnabídky nebo místní nabídky je nový sloupec oddělený od starého sloupce svislou čárou.

- MF_MENUBREAK umístí položku na nový řádek (pro panel nabídek) nebo do nového sloupce (u rozevírací nabídky, podnabídky nebo místní nabídky) bez oddělení sloupců.

- MF_UNCHECKED neumístí zaškrtnutí vedle položky (výchozí).

Následující skupiny příznaků nelze použít společně:

- MF_DISABLED, MF_ENABLED a MF_GRAYED.

- MF_MENUBARBREAK a MF_MENUBREAK.

- MF_CHECKED a MF_UNCHECKED.

##  <a name="updatetoolbarbutton"></a>CSnapInItemImpl::UpdateToolbarButton

Voláním této funkce upravíte tlačítko panelu nástrojů objektu snap-in, než se zobrazí.

```
BOOL UpdateToolbarButton(UINT id, BYTE fsState);
```

### <a name="parameters"></a>Parametry

*id*<br/>
Určuje ID tlačítka panelu nástrojů, které se má aktualizovat.

*fsState*<br/>
Určuje stav tlačítka panelu nástrojů. Pokud má být tento stav nastaven, vrátí hodnotu TRUE. Může se jednat o kombinaci následujících příznaků:

- POVOLENÍ tlačítka akceptuje vstup uživatele. Tlačítko, které nemá tento stav, nepřijímá vstup uživatele a je šedě.

- Bylo ZAŠKRTNUTO, že tlačítko má ZKONTROLOVANÝ styl a je stisknuto.

- SKRYTÉ tlačítko není viditelné a nemůže přijímat uživatelský vstup.

- Neurčité tlačítko je šedé.

- BUTTONPRESSED, že se stiskne tlačítko.

## <a name="see-also"></a>Viz také:

[Přehled třídy](../../atl/atl-class-overview.md)
