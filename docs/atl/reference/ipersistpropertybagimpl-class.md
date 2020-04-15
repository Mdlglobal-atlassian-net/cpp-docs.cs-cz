---
title: Třída IPersistPropertyBagImpl
ms.date: 11/04/2016
f1_keywords:
- IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl
- ATLCOM/ATL::IPersistPropertyBagImpl::GetClassID
- ATLCOM/ATL::IPersistPropertyBagImpl::InitNew
- ATLCOM/ATL::IPersistPropertyBagImpl::Load
- ATLCOM/ATL::IPersistPropertyBagImpl::Save
helpviewer_keywords:
- IPersistPropertyBagImpl class
ms.assetid: 712af24d-99f8-40f2-9811-53b3ff6e5b19
ms.openlocfilehash: f656ecc76b175eae523059c60bb8a3efc6f0b312
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326483"
---
# <a name="ipersistpropertybagimpl-class"></a>Třída IPersistPropertyBagImpl

Tato třída `IUnknown` implementuje a umožňuje objektu uložit své vlastnosti do vaku vlastností dodaného klientem.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE IPersistPropertyBagImpl : public IPersistPropertyBag
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, odvozená z `IPersistPropertyBagImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[ipersistpropertybagimpl::GetclassID](#getclassid)|Načte identifikátor CLSID objektu.|
|[IPersistPropertyBagImpl::InitNew](#initnew)|Inicializuje nově vytvořený objekt. Implementace ATL vrátí S_OK.|
|[ipersistpropertybagimpl::Načíst](#load)|Načte vlastnosti objektu z vaku vlastností dodaného klientem.|
|[iPersistPropertyBagimpl::Uložit](#save)|Uloží vlastnosti objektu do vaku vlastností dodaného klientem.|

## <a name="remarks"></a>Poznámky

[Rozhraní IPersistPropertyBag](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768205\(v=vs.85\)) umožňuje objektu uložit jeho vlastnosti do vaku vlastností dodaného klientem. Třída `IPersistPropertyBagImpl` poskytuje výchozí implementaci tohoto rozhraní `IUnknown` a implementuje odesláním informací do zařízení s výpisem stavu paměti v sestavení ladění.

`IPersistPropertyBag`pracuje ve spojení s [IPropertyBag](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768196\(v=vs.85\)) a [IErrorLog](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768231\(v=vs.85\)). Tyto poslední dvě rozhraní musí být implementovány klientem. Prostřednictvím `IPropertyBag`klient uloží a načte jednotlivé vlastnosti objektu. Prostřednictvím `IErrorLog`, objekt i klient může hlásit všechny chyby došlo.

**Související články** [ATL Výuka](../../atl/active-template-library-atl-tutorial.md), [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IPersistPropertyBag`

`IPersistPropertyBagImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom.h

## <a name="ipersistpropertybagimplgetclassid"></a><a name="getclassid"></a>ipersistpropertybagimpl::GetclassID

Načte identifikátor CLSID objektu.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Poznámky

Viz [iPersist::GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) v sadě Windows SDK.

## <a name="ipersistpropertybagimplinitnew"></a><a name="initnew"></a>IPersistPropertyBagImpl::InitNew

Inicializuje nově vytvořený objekt.

```
STDMETHOD(InitNew)();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí S_OK.

### <a name="remarks"></a>Poznámky

Viz [IPersistPropertyBag::InitNew](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768204\(v=vs.85\)) v sadě Windows SDK.

## <a name="ipersistpropertybagimplload"></a><a name="load"></a>ipersistpropertybagimpl::Načíst

Načte vlastnosti objektu z vaku vlastností dodaného klientem.

```
STDMETHOD(Load)(LPPROPERTYBAG pPropBag, LPERRORLOG pErrorLog);
```

### <a name="remarks"></a>Poznámky

Knihovna ATL používá mapu vlastností objektu k načtení těchto informací.

Viz [IPersistPropertyBag::Load](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768206\(v=vs.85\)) in the Windows SDK.

## <a name="ipersistpropertybagimplsave"></a><a name="save"></a>iPersistPropertyBagimpl::Uložit

Uloží vlastnosti objektu do vaku vlastností dodaného klientem.

```
STDMETHOD(Save)(
    LPPROPERTYBAG pPropBag,
    BOOL fClearDirty,
    BOOL fSaveAllProperties);
```

### <a name="remarks"></a>Poznámky

Knihovna ATL používá k ukládání těchto informací mapu vlastností objektu. Ve výchozím nastavení tato metoda uloží všechny vlastnosti bez ohledu na hodnotu *fSaveAllProperties*.

Viz [IPersistPropertyBag::Save](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768207\(v=vs.85\)) in the Windows SDK.

## <a name="see-also"></a>Viz také

[BEGIN_PROP_MAP](property-map-macros.md#begin_prop_map)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
