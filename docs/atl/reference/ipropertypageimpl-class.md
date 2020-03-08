---
title: IPropertyPageImpl – třída
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
ms.openlocfilehash: 69842e77aecaa94be66432e5fbba437a6fa3c5a4
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2020
ms.locfileid: "78864980"
---
# <a name="ipropertypageimpl-class"></a>IPropertyPageImpl – třída

Tato třída implementuje `IUnknown` a poskytuje výchozí implementaci rozhraní [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) .

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IPropertyPageImpl
```

#### <a name="parameters"></a>Parametry

*Š*<br/>
Vaše třída odvozená od `IPropertyPageImpl`.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[IPropertyPageImpl::IPropertyPageImpl](#ipropertypageimpl)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IPropertyPageImpl:: Activate](#activate)|Vytvoří okno dialogového okna pro stránku vlastností.|
|[IPropertyPageImpl:: Apply](#apply)|Použije aktuální hodnoty stránky vlastností na podkladové objekty zadané pomocí `SetObjects`. Implementace ATL vrací S_OK.|
|[IPropertyPageImpl::D eactivate](#deactivate)|Odstraní okno vytvořené pomocí `Activate`.|
|[IPropertyPageImpl::GetPageInfo](#getpageinfo)|Načte informace o stránce vlastností.|
|[IPropertyPageImpl:: help](#help)|Vyvolá nápovědu systému Windows pro stránku vlastností.|
|[IPropertyPageImpl::IsPageDirty](#ispagedirty)|Označuje, zda se stránka vlastností od aktivace změnila.|
|[IPropertyPageImpl:: Move](#move)|Umístí a změní velikost dialogového okna stránky vlastností.|
|[IPropertyPageImpl::SetDirty](#setdirty)|Označí stav stránky vlastností jako změněný nebo beze změny.|
|[IPropertyPageImpl::SetObjects](#setobjects)|Poskytuje pole ukazatelů `IUnknown` pro objekty přidružené k stránce vlastností. Tyto objekty dostanou aktuální hodnoty stránky vlastností prostřednictvím volání `Apply`.|
|[IPropertyPageImpl::SetPageSite](#setpagesite)|Poskytuje stránku vlastností s ukazatelem `IPropertyPageSite`, pomocí kterého stránka vlastností komunikuje s rámcem vlastností.|
|[IPropertyPageImpl:: show](#show)|Nastaví okno stránky vlastností jako viditelné nebo neviditelné.|
|[IPropertyPageImpl::TranslateAccelerator](#translateaccelerator)|Zpracuje zadaný klávesovou zkratku.|

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|[IPropertyPageImpl:: m_bDirty](#m_bdirty)|Určuje, zda došlo ke změně stavu stránky vlastností.|
|[IPropertyPageImpl:: m_dwDocString](#m_dwdocstring)|Ukládá identifikátor prostředku přidružený k textovému řetězci, který popisuje stránku vlastností.|
|[IPropertyPageImpl:: m_dwHelpContext](#m_dwhelpcontext)|Ukládá identifikátor kontextu pro téma nápovědy přidružené k stránce vlastností.|
|[IPropertyPageImpl:: m_dwHelpFile](#m_dwhelpfile)|Ukládá identifikátor prostředku přidružený k názvu souboru s podaným v nápovědě, který popisuje stránku vlastností.|
|[IPropertyPageImpl:: m_dwTitle](#m_dwtitle)|Ukládá identifikátor prostředku přidružený k textovému řetězci, který se zobrazí na kartě stránky vlastností.|
|[IPropertyPageImpl:: m_nObjects](#m_nobjects)|Ukládá počet objektů přidružených k stránce vlastností.|
|[IPropertyPageImpl:: m_pPageSite](#m_ppagesite)|Odkazuje na rozhraní `IPropertyPageSite`, pomocí kterého stránka vlastností komunikuje s rámcem vlastností.|
|[IPropertyPageImpl:: m_ppUnk](#m_ppunk)|Odkazuje na pole ukazatelů `IUnknown` na objekty přidružené k stránce vlastností.|
|[IPropertyPageImpl:: m_size](#m_size)|Ukládá výšku a šířku dialogového okna stránky vlastností (v pixelech).|

## <a name="remarks"></a>Poznámky

Rozhraní [IPropertyPage](/windows/win32/api/ocidl/nn-ocidl-ipropertypage) umožňuje objektu spravovat určitou stránku vlastností v rámci seznamu vlastností. Třída `IPropertyPageImpl` poskytuje výchozí implementaci tohoto rozhraní a implementuje `IUnknown` odesláním informací do zařízení výpisu paměti v sestaveních pro ladění.

Kurz **související články** [ATL](../../atl/active-template-library-atl-tutorial.md), [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IPropertyPage`

`IPropertyPageImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl. h

##  <a name="activate"></a>IPropertyPageImpl:: Activate

Vytvoří okno dialogového okna pro stránku vlastností.

```
HRESULT Activate(
    HWND hWndParent,
    LPCRECT pRect,
    BOOL bModal);
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení je dialogové okno vždy nemodální, bez ohledu na hodnotu parametru *bModal* .

Viz [IPropertyPage:: Activate](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-activate) v Windows SDK.

##  <a name="apply"></a>IPropertyPageImpl:: Apply

Použije aktuální hodnoty stránky vlastností na podkladové objekty zadané pomocí `SetObjects`.

```
HRESULT Apply();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Viz [IPropertyPage:: Apply](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-apply) in Windows SDK.

##  <a name="deactivate"></a>IPropertyPageImpl::D eactivate

Odstraní okno dialogového okna vytvořené pomocí [aktivovat](#activate).

```
HRESULT Deactivate();
```

### <a name="remarks"></a>Poznámky

Viz [IPropertyPage::D eactivate](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-deactivate) v Windows SDK.

##  <a name="getpageinfo"></a>IPropertyPageImpl::GetPageInfo

Vyplní strukturu *pPageInfo* informacemi obsaženými v datových členech.

```
HRESULT GetPageInfo(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>Poznámky

`GetPageInfo` načítá řetězcové prostředky přidružené k [m_dwDocString](#m_dwdocstring), [m_dwHelpFile](#m_dwhelpfile)a [m_dwTitle](#m_dwtitle).

Viz [IPropertyPage:: GetPageInfo](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-getpageinfo) v Windows SDK.

##  <a name="help"></a>IPropertyPageImpl:: help

Vyvolá nápovědu systému Windows pro stránku vlastností.

```
HRESULT Help(PROPPAGEINFO* pPageInfo);
```

### <a name="remarks"></a>Poznámky

Viz [IPropertyPage:: help](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-help) v Windows SDK.

##  <a name="ipropertypageimpl"></a>IPropertyPageImpl::IPropertyPageImpl

Konstruktor

```
IPropertyPageImpl();
```

### <a name="remarks"></a>Poznámky

Inicializuje všechny datové členy.

##  <a name="ispagedirty"></a>IPropertyPageImpl::IsPageDirty

Označuje, zda se stránka vlastností od aktivace změnila.

```
HRESULT IsPageDirty(void);
```

### <a name="remarks"></a>Poznámky

`IsPageDirty` vrátí S_OK, pokud se stránka od aktivace změnila.

##  <a name="m_bdirty"></a>IPropertyPageImpl:: m_bDirty

Určuje, zda došlo ke změně stavu stránky vlastností.

```
BOOL m_bDirty;
```

##  <a name="m_nobjects"></a>IPropertyPageImpl:: m_nObjects

Ukládá počet objektů přidružených k stránce vlastností.

```
ULONG m_nObjects;
```

##  <a name="m_dwhelpcontext"></a>IPropertyPageImpl:: m_dwHelpContext

Ukládá identifikátor kontextu pro téma nápovědy přidružené k stránce vlastností.

```
DWORD m_dwHelpContext;
```

##  <a name="m_dwdocstring"></a>IPropertyPageImpl:: m_dwDocString

Ukládá identifikátor prostředku přidružený k textovému řetězci, který popisuje stránku vlastností.

```
UINT m_dwDocString;
```

##  <a name="m_dwhelpfile"></a>IPropertyPageImpl:: m_dwHelpFile

Ukládá identifikátor prostředku přidružený k názvu souboru s podaným v nápovědě, který popisuje stránku vlastností.

```
UINT m_dwHelpFile;
```

##  <a name="m_dwtitle"></a>IPropertyPageImpl:: m_dwTitle

Ukládá identifikátor prostředku přidružený k textovému řetězci, který se zobrazí na kartě stránky vlastností.

```
UINT m_dwTitle;
```

##  <a name="m_ppagesite"></a>IPropertyPageImpl:: m_pPageSite

Odkazuje na rozhraní [IPropertyPageSite](/windows/win32/api/ocidl/nn-ocidl-ipropertypagesite) , pomocí kterého stránka vlastností komunikuje s rámcem vlastností.

```
IPropertyPageSite* m_pPageSite;
```

##  <a name="m_ppunk"></a>IPropertyPageImpl:: m_ppUnk

Odkazuje na pole ukazatelů `IUnknown` na objekty přidružené k stránce vlastností.

```
IUnknown** m_ppUnk;
```

##  <a name="m_size"></a>IPropertyPageImpl:: m_size

Ukládá výšku a šířku dialogového okna stránky vlastností (v pixelech).

```
SIZE m_size;
```

##  <a name="move"></a>IPropertyPageImpl:: Move

Umístí a změní velikost dialogového okna stránky vlastností.

```
HRESULT Move(LPCRECT pRect);
```

### <a name="remarks"></a>Poznámky

Viz [IPropertyPage:: Move](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-move) in Windows SDK.

##  <a name="setdirty"></a>IPropertyPageImpl::SetDirty

Označí stav stránky vlastností jako změněný nebo nezměněný v závislosti na hodnotě *bDirty*.

```
void SetDirty(BOOL bDirty);
```

### <a name="parameters"></a>Parametry

*bDirty*<br/>
pro V případě hodnoty TRUE je stav stránky vlastností označen jako změněný. V opačném případě je označena jako beze změny.

### <a name="remarks"></a>Poznámky

V případě potřeby `SetDirty` informuje rámec, že se změnila stránka vlastností.

##  <a name="setobjects"></a>IPropertyPageImpl::SetObjects

Poskytuje pole ukazatelů `IUnknown` pro objekty přidružené k stránce vlastností.

```
HRESULT SetObjects(ULONG nObjects, IUnknown** ppUnk);
```

### <a name="remarks"></a>Poznámky

Viz [IPropertyPage:: SetObjects](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-setobjects) v Windows SDK.

##  <a name="setpagesite"></a>IPropertyPageImpl::SetPageSite

Poskytuje stránku vlastností s ukazatelem [IPropertyPageSite](/windows/win32/api/ocidl/nn-ocidl-ipropertypagesite) , pomocí kterého stránka vlastností komunikuje s rámcem vlastností.

```
HRESULT SetPageSite(IPropertyPageSite* pPageSite);
```

### <a name="remarks"></a>Poznámky

Viz [IPropertyPage:: SetPageSite](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-setpagesite) v Windows SDK.

##  <a name="show"></a>IPropertyPageImpl:: show

Nastaví okno stránky vlastností jako viditelné nebo neviditelné.

```
HRESULT Show(UINT nCmdShow);
```

### <a name="remarks"></a>Poznámky

Viz [IPropertyPage:: show](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-show) v Windows SDK.

##  <a name="translateaccelerator"></a>IPropertyPageImpl::TranslateAccelerator

Zpracuje klávesovou zkratku určenou v `pMsg`.

```
HRESULT TranslateAccelerator(MSG* pMsg);
```

### <a name="remarks"></a>Poznámky

Viz [IPropertyPage:: TranslateAccelerator](/windows/win32/api/ocidl/nf-ocidl-ipropertypage-translateaccelerator) v Windows SDK.

## <a name="see-also"></a>Viz také

[IPropertyPage2Impl – třída](../../atl/reference/ipropertypage2impl-class.md)<br/>
[IPerPropertyBrowsingImpl – třída](../../atl/reference/iperpropertybrowsingimpl-class.md)<br/>
[ISpecifyPropertyPagesImpl – třída](../../atl/reference/ispecifypropertypagesimpl-class.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
