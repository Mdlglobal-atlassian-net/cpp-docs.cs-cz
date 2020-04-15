---
title: Třída IDispEventImpl
ms.date: 11/04/2016
f1_keywords:
- IDispEventImpl
- ATLCOM/ATL::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::GetFuncInfoFromId
- ATLCOM/ATL::IDispEventImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventImpl::GetUserDefinedType
helpviewer_keywords:
- IDispEventImpl class
ms.assetid: a64b5288-35cb-4638-aad6-2d15b1c7cf7b
ms.openlocfilehash: fa6e9f972accd0115d9f1e3248bd97ddde0c3c63
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81329755"
---
# <a name="idispeventimpl-class"></a>Třída IDispEventImpl

Tato třída poskytuje implementace `IDispatch` metod.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <UINT nID, class T,
    const IID* pdiid = &IID_NULL,
    const GUID* plibid = &GUID_NULL,
    WORD wMajor = 0,
    WORD wMinor = 0,
    class tihclass = CcomTypeInfoHolder>
class ATL_NO_VTABLE IDispEventImpl : public IDispEventSimpleImpl<nID, T, pdiid>
```

#### <a name="parameters"></a>Parametry

*Nid*<br/>
Jedinečný identifikátor zdrojového objektu. Pokud `IDispEventImpl` je základní třída pro složený ovládací prvek, použijte ID prostředku požadovaného obsaženého ovládacího prvku pro tento parametr. V ostatních případech použijte libovolné kladné celé číslo.

*T*<br/>
Třída uživatele, která je odvozena `IDispEventImpl`z .

*pdiid*<br/>
Ukazatel na IID dispinterface události implementované touto třídou. Toto rozhraní musí být definováno v knihovně typů označené *plibid*, *wMajor*a *wMinor*.

*plibid*<br/>
Ukazatel na knihovnu typů, která definuje rozhraní odeslání, na které odkazuje *pdiid*. Pokud **&GUID_NULL**, knihovna typů se načte z objektu, který události získá.

*wMajor*<br/>
Hlavní verze knihovny typů. Výchozí hodnota je 0.

*wMenší*<br/>
Dílčí verze knihovny typů. Výchozí hodnota je 0.

*tihclass*<br/>
Třída slouží ke správě informací o typu pro *T*. Výchozí hodnota je třída `CComTypeInfoHolder`typu ; Tento parametr šablony však můžete přepsat poskytnutím jiné `CComTypeInfoHolder`třídy než .

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Name (Název)|Popis|
|----------|-----------------|
|[IDispEventImpl::_tihclass](../../atl/reference/idispeventimpl-class.md)|Třída slouží ke správě informací o typu. Ve výchozím `CComTypeInfoHolder`nastavení .|

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[IDispEventImpl::IDispEventImpl](#idispeventimpl)|Konstruktor|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[IDispEventImpl::GetFuncInfoFromId](#getfuncinfofromid)|Vyhledá index funkce pro zadaný identifikátor odeslání.|
|[IDispEventImpl::GetIDsOfNames](#getidsofnames)|Mapuje jeden člen a volitelnou sadu názvů argumentů na odpovídající sadu celé hodované dispid.|
|[IDispEventImpl::GetTypeInfo](#gettypeinfo)|Načte informace o typu objektu.|
|[IDispEventImpl::GetTypeInfoCount](#gettypeinfocount)|Načte počet rozhraní informací o typu.|
|[IDispEventImpl::GetUserDefinedType](#getuserdefinedtype)|Načte základní typ uživatelem definovaného typu.|

## <a name="remarks"></a>Poznámky

`IDispEventImpl`Poskytuje způsob implementace rozhraní dispinterface události bez nutnosti zadat kód implementace pro každou metodu nebo událost v tomto rozhraní. `IDispEventImpl`poskytuje implementace `IDispatch` metod. Potřebujete pouze zadat implementace pro události, které máte zájem o zpracování.

`IDispEventImpl`pracuje ve spojení s mapou jímky událostí ve vaší třídě směrovat události na příslušnou funkci obslužné rutiny. Chcete-li použít tuto třídu:

Přidejte [SINK_ENTRY](composite-control-macros.md#sink_entry) nebo [SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex) makro do mapy jímky událostí pro každou událost na každém objektu, který chcete zpracovat. Při `IDispEventImpl` použití jako základní třídy složené ovládacíprvek, můžete volat [AtlAdviseSinkMap](connection-point-global-functions.md#atladvisesinkmap) navázat a přerušit připojení se zdroji událostí pro všechny položky v mapě jímky událostí. V ostatních případech nebo pro větší kontrolu, volání [DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise) navázat spojení mezi zdrojový objekt a základní třídy. Volání [DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise) přerušit připojení.

Musíte odvodit z `IDispEventImpl` (pomocí jedinečné hodnoty pro *nID*) pro každý objekt, pro který je třeba zpracovat události. Základní třídu můžete znovu použít tím, že uporadíte proti jednomu zdrojovému objektu a pak budete poskytovat poradenství proti jinému zdrojovému `IDispEventImpl` objektu, ale maximální počet zdrojových objektů, které mohou být zpracovány jedním objektem najednou, je omezen počtem základních tříd.

`IDispEventImpl`poskytuje stejné funkce jako [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md), s výjimkou získá informace o typu rozhraní z knihovny typů, nikoli s jeho dodáním jako ukazatel na [_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md) struktury. Použijte, `IDispEventSimpleImpl` pokud nemáte knihovnu typů popisující rozhraní událostí nebo chcete vyhnout režii spojené s použitím knihovny typů.

> [!NOTE]
> `IDispEventImpl`a `IDispEventSimpleImpl` poskytují vlastní `IUnknown::QueryInterface` implementaci `IDispEventImpl` umožňující `IDispEventSimpleImpl` každé a základní třídy fungovat jako samostatná identita COM a zároveň umožňuje přímý přístup ke členům třídy v hlavním objektu COM.

CE ATL implementace jímky událostí ActiveX podporuje pouze vrácené hodnoty typu HRESULT nebo void z metody obslužné rutiny události; všechny ostatní vrácená hodnota není podporována a její chování není definováno.

Další informace naleznete [v tématu Supporting IDispEventImpl](../../atl/supporting-idispeventimpl.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`_IDispEvent`

`_IDispEventLocator`

[IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)

`IDispEventImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="idispeventimplgetfuncinfofromid"></a><a name="getfuncinfofromid"></a>IDispEventImpl::GetFuncInfoFromId

Vyhledá index funkce pro zadaný identifikátor odeslání.

```
HRESULT GetFuncInfoFromId(
    const IID& iid,
    DISPID dispidMember,
    LCID lcid,
    _ATL_FUNC_INFO& info);
```

### <a name="parameters"></a>Parametry

*Iid*<br/>
[v] Odkaz na ID funkce.

*člen nečekána*<br/>
[v] ID odeslání funkce.

*lcid*<br/>
[v] Kontext národního prostředí ID funkce.

*Info*<br/>
[v] Struktura označující, jak je funkce volána.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

## <a name="idispeventimplgetidsofnames"></a><a name="getidsofnames"></a>IDispEventImpl::GetIDsOfNames

Mapuje jeden člen a volitelnou sadu názvů argumentů na odpovídající sadu celé hospodařící DISPID, které lze použít při následných voláních [na IDispatch::Invoke](/windows/win32/api/oaidl/nf-oaidl-idispatch-invoke).

```
STDMETHOD(GetIDsOfNames)(
    REFIID riid,
    LPOLESTR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID* rgdispid);
```

### <a name="remarks"></a>Poznámky

Viz [IDispatch::GetIDsOfNames](/windows/win32/api/oaidl/nf-oaidl-idispatch-getidsofnames) v sadě Windows SDK.

## <a name="idispeventimplgettypeinfo"></a><a name="gettypeinfo"></a>IDispEventImpl::GetTypeInfo

Načte informace o typu objektu, který lze použít k získání informací o typu pro rozhraní.

```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```

### <a name="remarks"></a>Poznámky

## <a name="idispeventimplgettypeinfocount"></a><a name="gettypeinfocount"></a>IDispEventImpl::GetTypeInfoCount

Získá počet rozhraní typu informací, které objekt poskytuje (0 nebo 1).

```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```

### <a name="remarks"></a>Poznámky

Viz [IDispatch::GetTypeInfoCount](/windows/win32/api/oaidl/nf-oaidl-idispatch-gettypeinfocount) v sadě Windows SDK.

## <a name="idispeventimplgetuserdefinedtype"></a><a name="getuserdefinedtype"></a>IDispEventImpl::GetUserDefinedType

Načte základní typ uživatelem definovaného typu.

```
VARTYPE GetUserDefinedType(
    ITypeInfo* pTI,
    HREFTYPE hrt);
```

### <a name="parameters"></a>Parametry

*Pti*<br/>
[v] Ukazatel na rozhraní [ITypeInfo](/windows/win32/api/oaidl/nn-oaidl-itypeinfo) obsahující uživatelem definovaný typ.

*Hrt*<br/>
[v] Popisovač popisu typu, který má být načten.

### <a name="return-value"></a>Návratová hodnota

Typ varianty.

### <a name="remarks"></a>Poznámky

Viz [iTypeInfo::GetreftypeInfo](/windows/win32/api/oaidl/nf-oaidl-itypeinfo-getreftypeinfo).

## <a name="idispeventimplidispeventimpl"></a><a name="idispeventimpl"></a>IDispEventImpl::IDispEventImpl

Konstruktor Ukládá hodnoty parametrů šablony třídy *plibid*, *pdiid*, *wMajor*a *wMinor*.

```
IDispEventImpl();
```

## <a name="idispeventimpltihclass"></a><a name="tihclass"></a>IDispEventImpl::tihclass

Tento typedef je instancí třídy parametru šablony třídy *tihclass*.

```
typedef tihclass _tihclass;
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení `CComTypeInfoHolder`je třída . `CComTypeInfoHolder`spravuje informace o typu pro třídu.

## <a name="see-also"></a>Viz také

[_ATL_FUNC_INFO struktura](../../atl/reference/atl-func-info-structure.md)<br/>
[Třída IDispatchimpl](../../atl/reference/idispatchimpl-class.md)<br/>
[Třída IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)<br/>
[SINK_ENTRY](composite-control-macros.md#sink_entry)<br/>
[SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)<br/>
[SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
