---
title: IPersistPropertyBagImpl – třída
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
ms.openlocfilehash: 15b9c9738d921c4c6f7837f9280c6dd6b09392d6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495767"
---
# <a name="ipersistpropertybagimpl-class"></a>IPersistPropertyBagImpl – třída

Tato třída implementuje `IUnknown` a umožňuje objektu ukládat jeho vlastnosti do kontejneru vlastností dodaných klientem.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE IPersistPropertyBagImpl : public IPersistPropertyBag
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, která je `IPersistPropertyBagImpl`odvozena z.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[IPersistPropertyBagImpl::GetClassID](#getclassid)|Načte CLSID objektu.|
|[IPersistPropertyBagImpl::InitNew](#initnew)|Inicializuje nově vytvořený objekt. Implementace ATL vrací S_OK.|
|[IPersistPropertyBagImpl::Load](#load)|Načte vlastnosti objektu z kontejneru vlastností dodaných klientem.|
|[IPersistPropertyBagImpl::Save](#save)|Uloží vlastnosti objektu do kontejneru vlastností dodaných klientem.|

## <a name="remarks"></a>Poznámky

Rozhraní [IPersistPropertyBag](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768205\(v=vs.85\)) umožňuje objektu ukládat jeho vlastnosti do kontejneru vlastností dodaných klientem. Třída `IPersistPropertyBagImpl` poskytuje výchozí implementaci tohoto rozhraní a implementuje `IUnknown` odesláním informací do zařízení výpisu paměti v sestaveních pro ladění.

`IPersistPropertyBag`funguje ve spojení s [IPropertyBag](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768196\(v=vs.85\)) a [IErrorLog](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768231\(v=vs.85\)). Tato dvě rozhraní musí být implementována klientem nástroje. Prostřednictvím `IPropertyBag`klienta aplikace ukládá a načítá jednotlivé vlastnosti objektu. V `IErrorLog`rámci může objekt i klient hlásit jakékoli zjištěné chyby.

**Související články** [Kurz ATL](../../atl/active-template-library-atl-tutorial.md), [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IPersistPropertyBag`

`IPersistPropertyBagImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom. h

##  <a name="getclassid"></a>IPersistPropertyBagImpl:: GetClassID

Načte CLSID objektu.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Poznámky

Viz [IPersist:: GetClassID](/windows/win32/api/objidl/nf-objidl-ipersist-getclassid) v Windows SDK.

##  <a name="initnew"></a>  IPersistPropertyBagImpl::InitNew

Inicializuje nově vytvořený objekt.

```
STDMETHOD(InitNew)();
```

### <a name="return-value"></a>Návratová hodnota

Vrací hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Viz [IPersistPropertyBag:: InitNew](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768204\(v=vs.85\)) v Windows SDK.

##  <a name="load"></a>IPersistPropertyBagImpl:: Load

Načte vlastnosti objektu z kontejneru vlastností dodaných klientem.

```
STDMETHOD(Load)(LPPROPERTYBAG pPropBag, LPERRORLOG pErrorLog);
```

### <a name="remarks"></a>Poznámky

Knihovna ATL používá k načtení těchto informací mapu vlastností objektu.

Viz [IPersistPropertyBag:: Load](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768206\(v=vs.85\)) in Windows SDK.

##  <a name="save"></a>IPersistPropertyBagImpl:: Save

Uloží vlastnosti objektu do kontejneru vlastností dodaných klientem.

```
STDMETHOD(Save)(
    LPPROPERTYBAG pPropBag,
    BOOL fClearDirty,
    BOOL fSaveAllProperties);
```

### <a name="remarks"></a>Poznámky

ATL používá mapu vlastností objektu k uložení těchto informací. Ve výchozím nastavení tato metoda uloží všechny vlastnosti bez ohledu na hodnotu *fSaveAllProperties*.

Viz [IPersistPropertyBag:: Save](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768207\(v=vs.85\)) in Windows SDK.

## <a name="see-also"></a>Viz také:

[BEGIN_PROP_MAP](property-map-macros.md#begin_prop_map)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
