---
title: Třída iPropertyPageimpl
ms.date: 11/04/2016
f1_keywords:
- IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl::IPropertyPageImpl
- ATLCTL/ATL::IPropertyPageImpl::Activate
- ATLCTL/ATL::IPropertyPageImpl::Apply
- ATLCTL/ATL::IPropertyPageImpl::Deactivate
- ATLCTL/ATL::IPropertyPageImpl::GetPageInfo
- ATLCTL/ATL::IPropertyPageImpl::Help
- ATLCTL/ATL::IPropertyPageImpl::IsPageDirty
- ATLCTL/ATL::IPropertyPageImpl::Move
- ATLCTL/ATL::IPropertyPageImpl::SetDirty
- ATLCTL/ATL::IPropertyPageImpl::SetObjects
- ATLCTL/ATL::IPropertyPageImpl::SetPageSite
- ATLCTL/ATL::IPropertyPageImpl::Show
- ATLCTL/ATL::IPropertyPageImpl::TranslateAccelerator
- ATLCTL/ATL::IPropertyPageImpl::m_bDirty
- ATLCTL/ATL::IPropertyPageImpl::m_dwDocString
- ATLCTL/ATL::IPropertyPageImpl::m_dwHelpContext
- ATLCTL/ATL::IPropertyPageImpl::m_dwHelpFile
- ATLCTL/ATL::IPropertyPageImpl::m_dwTitle
- ATLCTL/ATL::IPropertyPageImpl::m_nObjects
- ATLCTL/ATL::IPropertyPageImpl::m_pPageSite
- ATLCTL/ATL::IPropertyPageImpl::m_ppUnk
- ATLCTL/ATL::IPropertyPageImpl::m_size
helpviewer_keywords:
- property pages
- IPropertyPage ATL implementation
- IPropertyPageImpl class
ms.assetid: f9b7c8b1-7a04-4eab-aa63-63efddb740fa
ms.openlocfilehash: 154bfb5beb258ff26649f44f0bd4c23fb8708977
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/22/2020
ms.locfileid: "81745860"
---
# <a name="ipropertypageimpl-class"></a>Třída iPropertyPageimpl

Tato třída `IUnknown` implementuje a poskytuje výchozí implementaci rozhraní [IPropertyPage.](/windows/win32/api/ocidl/nn-ocidl-ipropertypage)

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IPropertyPageImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, odvozená z `IPropertyPageImpl`.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[iPropertyPageimpl::iPropertyPageImpl](#ipropertypageimpl)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[iPropertyPageImpl::Aktivovat](#activate)|Vytvoří okno dialogového okna pro stránku vlastností.|
|[iPropertyPageImpl::Použít](#apply)|Aplikuje aktuální hodnoty stránky vlastností `SetObjects`na podkladové objekty určené prostřednictvím aplikace . Implementace ATL vrátí S_OK.|
|[IPropertyPageImpl::Deaktivovat](#deactivate)|Zničí okno vytvořené `Activate`pomocí .|
|[iPropertyPageimpl::GetPageInfo](#getpageinfo)|Načte informace o stránce vlastností.|
|[IPropertyPageImpl::Nápověda](#help)|Vyvolá nápovědu systému Windows pro stránku vlastností.|
|[iPropertyPageimpl::IsPageDirty](#ispagedirty)|Označuje, zda se stránka vlastností od aktivace změnila.|
|[iPropertyPageImpl::Přesunout](#move)|Umístí a změní velikost dialogového okna stránky vlastností.|
|[iPropertyPageimpl::SetDirty](#setdirty)|Označí stav stránky vlastností jako změněný nebo nezměněný.|
|[iPropertyPageImpl::SetObjects](#setobjects)|Poskytuje pole `IUnknown` ukazatelů pro objekty přidružené ke stránce vlastností. Tyto objekty přijímají aktuální hodnoty stránky `Apply`vlastností prostřednictvím volání .|
|[iPropertyPageimpl::SetPageSite](#setpagesite)|Poskytuje stránku vlastností s ukazatelem, `IPropertyPageSite` jehož prostřednictvím stránka vlastností komunikuje s rámcem vlastností.|
|[iPropertyPageImpl::Zobrazit](#show)|Zviditelní nebo zneviditelní dialogové okno stránky vlastností.|
|[IPropertyPageImpl::TranslateAccelerator](#translateaccelerator)|Zpracuje zadaný stisk klávesy.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[IPropertyPageImpl::m_bDirty](#m_bdirty)|Určuje, zda se stav stránky vlastností změnil.|
|[IPropertyPageImpl::m_dwDocString](#m_dwdocstring)|Ukládá identifikátor prostředku přidružený k textovému řetězci popisujícímu stránku vlastností.|
|[IPropertyPageImpl::m_dwHelpContext](#m_dwhelpcontext)|Ukládá identifikátor kontextu pro téma nápovědy přidružené ke stránce vlastností.|
|[IPropertyPageImpl::m_dwHelpFile](#m_dwhelpfile)|Ukládá identifikátor prostředku přidružený k názvu souboru nápovědy popisujícístránku vlastností.|
|[IPropertyPageImpl::m_dwTitle](#m_dwtitle)|Uloží identifikátor prostředku přidružený k textovému řetězci, který se zobrazí na kartě stránky vlastností.|
|[IPropertyPageImpl::m_nObjects](#m_nobjects)|Ukládá počet objektů přidružených ke stránce vlastností.|
|[IPropertyPageImpl::m_pPageSite](#m_ppagesite)|Odkazuje na `IPropertyPageSite` rozhraní, přes které stránka vlastností komunikuje s rámcem vlastností.|
|[IPropertyPageImpl::m_ppUnk](#m_ppunk)|Odkazuje na pole `IUnknown` ukazatelů na objekty přidružené ke stránce vlastností.|
|[IPropertyPageImpl::m_size](#m_size)|Uloží výšku a šířku dialogového okna stránky vlastností v obrazových bodech.|

## <a name="remarks"></a>Poznámky

Rozhraní [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) umožňuje objektu spravovat určitou stránku vlastností v seznamu vlastností. Třída `IPropertyPageImpl` poskytuje výchozí implementaci tohoto rozhraní `IUnknown` a implementuje odesláním informací do zařízení s výpisem stavu paměti v sestavení ladění.

**Související články** [ATL Výuka](../../atl/active-template-library-atl-tutorial.md), [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IPropertyPage`

`IPropertyPageImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

## <a name="ipropertypageimplactivate"></a><a name="activate"></a>iPropertyPageImpl::Aktivovat

Vytvoří okno dialogového okna pro stránku vlastností.

```
HRESULT Activate(
    HWND hWndParent,
    LPCRECT pRect,
    BOOL bModal);
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení je dialogové okno vždy bezmodého, bez ohledu na hodnotu parametru *bModal.*

Viz [IPropertyPage::Activate](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-activate) v sadě Windows SDK.

## <a name="ipropertypageimplapply"></a><a name="apply"></a>iPropertyPageImpl::Použít

Aplikuje aktuální hodnoty stránky vlastností `SetObjects`na podkladové objekty určené prostřednictvím aplikace .

```
HRESULT Apply();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Viz [IPropertyPage::Apply](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-apply) in the Windows SDK.

## <a name="ipropertypageimpldeactivate"></a><a name="deactivate"></a>IPropertyPageImpl::Deaktivovat

Zničí okno dialogového okna vytvořené [pomocí aplikace Aktivovat](#activate).

```
HRESULT Deactivate();
```

### <a name="remarks"></a>Poznámky

Viz [IPropertyPage::Deactivate](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-deactivate) v sadě Windows SDK.

## <a name="ipropertypageimplgetpageinfo"></a><a name="getpageinfo"></a>iPropertyPageimpl::GetPageInfo

Vyplní strukturu *pPageInfo* informacemi obsaženými v datových členech.

```
HRESULT GetPageInfo(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>Poznámky

`GetPageInfo`načte prostředky řetězce přidružené k [m_dwDocString](#m_dwdocstring), [m_dwHelpFile](#m_dwhelpfile)a [m_dwTitle](#m_dwtitle).

Viz [IPropertyPage::GetPageInfo](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-getpageinfo) v sadě Windows SDK.

## <a name="ipropertypageimplhelp"></a><a name="help"></a>IPropertyPageImpl::Nápověda

Vyvolá nápovědu systému Windows pro stránku vlastností.

```
HRESULT Help(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>Poznámky

Viz [IPropertyPage::Nápověda](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-help) v sadě Windows SDK.

## <a name="ipropertypageimplipropertypageimpl"></a><a name="ipropertypageimpl"></a>iPropertyPageimpl::iPropertyPageImpl

Konstruktor

```
IPropertyPageImpl();
```

### <a name="remarks"></a>Poznámky

Inicializuje všechny datové členy.

## <a name="ipropertypageimplispagedirty"></a><a name="ispagedirty"></a>iPropertyPageimpl::IsPageDirty

Označuje, zda se stránka vlastností od aktivace změnila.

```
HRESULT IsPageDirty(void);
```

### <a name="remarks"></a>Poznámky

`IsPageDirty`vrátí S_OK, pokud se stránka od aktivace změnila.

## <a name="ipropertypageimplm_bdirty"></a><a name="m_bdirty"></a>IPropertyPageImpl::m_bDirty

Určuje, zda se stav stránky vlastností změnil.

```
BOOL m_bDirty;
```

## <a name="ipropertypageimplm_nobjects"></a><a name="m_nobjects"></a>IPropertyPageImpl::m_nObjects

Ukládá počet objektů přidružených ke stránce vlastností.

```
ULONG m_nObjects;
```

## <a name="ipropertypageimplm_dwhelpcontext"></a><a name="m_dwhelpcontext"></a>IPropertyPageImpl::m_dwHelpContext

Ukládá identifikátor kontextu pro téma nápovědy přidružené ke stránce vlastností.

```
DWORD m_dwHelpContext;
```

## <a name="ipropertypageimplm_dwdocstring"></a><a name="m_dwdocstring"></a>IPropertyPageImpl::m_dwDocString

Ukládá identifikátor prostředku přidružený k textovému řetězci popisujícímu stránku vlastností.

```
UINT m_dwDocString;
```

## <a name="ipropertypageimplm_dwhelpfile"></a><a name="m_dwhelpfile"></a>IPropertyPageImpl::m_dwHelpFile

Ukládá identifikátor prostředku přidružený k názvu souboru nápovědy popisujícístránku vlastností.

```
UINT m_dwHelpFile;
```

## <a name="ipropertypageimplm_dwtitle"></a><a name="m_dwtitle"></a>IPropertyPageImpl::m_dwTitle

Uloží identifikátor prostředku přidružený k textovému řetězci, který se zobrazí na kartě stránky vlastností.

```
UINT m_dwTitle;
```

## <a name="ipropertypageimplm_ppagesite"></a><a name="m_ppagesite"></a>IPropertyPageImpl::m_pPageSite

Odkazuje na rozhraní [IPropertyPageSite,](/windows/win32/api/ocidl/nn-ocidl-ipropertypagesite) jehož prostřednictvím stránka vlastností komunikuje s rámcem vlastností.

```
IPropertyPageSite* m_pPageSite;
```

## <a name="ipropertypageimplm_ppunk"></a><a name="m_ppunk"></a>IPropertyPageImpl::m_ppUnk

Odkazuje na pole `IUnknown` ukazatelů na objekty přidružené ke stránce vlastností.

```
IUnknown** m_ppUnk;
```

## <a name="ipropertypageimplm_size"></a><a name="m_size"></a>IPropertyPageImpl::m_size

Uloží výšku a šířku dialogového okna stránky vlastností v obrazových bodech.

```
SIZE m_size;
```

## <a name="ipropertypageimplmove"></a><a name="move"></a>iPropertyPageImpl::Přesunout

Umístí a změní velikost dialogového okna stránky vlastností.

```
HRESULT Move(LPCRECT pRect);
```

### <a name="remarks"></a>Poznámky

Viz [IPropertyPage::Move](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-move) in the Windows SDK.

## <a name="ipropertypageimplsetdirty"></a><a name="setdirty"></a>iPropertyPageimpl::SetDirty

Označí stav stránky vlastností jako změněný nebo nezměněný v závislosti na hodnotě *bDirty*.

```cpp
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>Parametry

*bDirty*<br/>
[v] Pokud true, stav stránky vlastností je označen jako změněn. V opačném případě je označen jako nezměněné.

### <a name="remarks"></a>Poznámky

V případě `SetDirty` potřeby informuje rámeček, že stránka vlastností byla změněna.

## <a name="ipropertypageimplsetobjects"></a><a name="setobjects"></a>iPropertyPageImpl::SetObjects

Poskytuje pole `IUnknown` ukazatelů pro objekty přidružené ke stránce vlastností.

```
HRESULT SetObjects(ULONG nObjects, IUnknown** ppUnk);
```

### <a name="remarks"></a>Poznámky

Viz [IPropertyPage::SetObjects](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-setobjects) v sadě Windows SDK.

## <a name="ipropertypageimplsetpagesite"></a><a name="setpagesite"></a>iPropertyPageimpl::SetPageSite

Poskytuje stránku vlastností ukazatel [IPropertyPageSite,](/windows/win32/api/ocidl/nn-ocidl-ipropertypagesite) jehož prostřednictvím stránka vlastností komunikuje s rámcem vlastností.

```
HRESULT SetPageSite(IPropertyPageSite* pPageSite);
```

### <a name="remarks"></a>Poznámky

Viz [IPropertyPage::SetPageSite](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-setpagesite) v sadě Windows SDK.

## <a name="ipropertypageimplshow"></a><a name="show"></a>iPropertyPageImpl::Zobrazit

Zviditelní nebo zneviditelní dialogové okno stránky vlastností.

```
HRESULT Show(UINT nCmdShow);
```

### <a name="remarks"></a>Poznámky

Viz [IPropertyPage::Show](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-show) v sadě Windows SDK.

## <a name="ipropertypageimpltranslateaccelerator"></a><a name="translateaccelerator"></a>IPropertyPageImpl::TranslateAccelerator

Zpracuje stisknutí `pMsg`klávesy určené v .

```
HRESULT TranslateAccelerator(MSG* pMsg);
```

### <a name="remarks"></a>Poznámky

Viz [IPropertyPage::TranslateAccelerator](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-translateaccelerator) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Třída iPropertyPage2impl](../../atl/reference/ipropertypage2impl-class.md)<br/>
[Třída IperPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl – třída](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
