---
title: Ipersistpropertybagimpl – třída
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
ms.openlocfilehash: 569a24fd08801de952e998f772afbc3478096628
ms.sourcegitcommit: ecf274bcfe3a977c48745aaa243e5e731f1fdc5f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2019
ms.locfileid: "66503148"
---
# <a name="ipersistpropertybagimpl-class"></a>Ipersistpropertybagimpl – třída

Tato třída implementuje `IUnknown` a umožňuje uložit do kontejneru objektů klientem poskytnutý její vlastnosti.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class T>
class ATL_NO_VTABLE IPersistPropertyBagImpl : public IPersistPropertyBag
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída odvozena od `IPersistPropertyBagImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[IPersistPropertyBagImpl::GetClassID](#getclassid)|Načte identifikátor CLSID objektu.|
|[IPersistPropertyBagImpl::InitNew](#initnew)|Inicializuje nově vytvořený objekt. Implementace knihovny ATL vrátí hodnotu S_OK.|
|[IPersistPropertyBagImpl::Load](#load)|Načte vlastnosti objektu z kontejneru objektů dodaná klientem.|
|[IPersistPropertyBagImpl::Save](#save)|Uloží vlastností objektu do kontejneru objektů dodaná klientem.|

## <a name="remarks"></a>Poznámky

[IPersistPropertyBag](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768205\(v=vs.85\)) rozhraní umožňuje uložit do kontejneru objektů klientem poskytnutý její vlastnosti. Třída `IPersistPropertyBagImpl` poskytuje výchozí implementaci tohoto rozhraní a implementuje `IUnknown` posíláním informací o k výpisu paměti zařízení v ladění sestavení.

`IPersistPropertyBag` funguje ve spojení s [IPropertyBag](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768196\(v=vs.85\)) a [IErrorLog](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768231\(v=vs.85\)). Tato druhá možnost dvě rozhraní musí být implementované klientem. Prostřednictvím `IPropertyBag`, klient ukládá a načítá jednotlivých vlastností objektu. Prostřednictvím `IErrorLog`, objektu a klienta můžete podávat zprávy o chybách byla zjištěna.

**Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IPersistPropertyBag`

`IPersistPropertyBagImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcom

##  <a name="getclassid"></a>  IPersistPropertyBagImpl::GetClassID

Načte identifikátor CLSID objektu.

```
STDMETHOD(GetClassID)(CLSID* pClassID);
```

### <a name="remarks"></a>Poznámky

Zobrazit [IPersist::GetClassID](/windows/desktop/api/objidl/nf-objidl-ipersist-getclassid) ve Windows SDK.

##  <a name="initnew"></a>  IPersistPropertyBagImpl::InitNew

Inicializuje nově vytvořený objekt.

```
STDMETHOD(InitNew)();
```

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK.

### <a name="remarks"></a>Poznámky

Zobrazit [IPersistPropertyBag::InitNew](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768204\(v=vs.85\)) ve Windows SDK.

##  <a name="load"></a>  IPersistPropertyBagImpl::Load

Načte vlastnosti objektu z kontejneru objektů dodaná klientem.

```
STDMETHOD(Load)(LPPROPERTYBAG pPropBag, LPERRORLOG pErrorLog);
```

### <a name="remarks"></a>Poznámky

Mapy vlastností objektu ATL používá pro načtení těchto informací.

Zobrazit [IPersistPropertyBag::Load](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768206\(v=vs.85\)) ve Windows SDK.

##  <a name="save"></a>  IPersistPropertyBagImpl::Save

Uloží vlastností objektu do kontejneru objektů dodaná klientem.

```
STDMETHOD(Save)(
    LPPROPERTYBAG pPropBag,
    BOOL fClearDirty,
    BOOL fSaveAllProperties);
```

### <a name="remarks"></a>Poznámky

Mapy vlastností objektu ATL používá k ukládání příslušných informací. Ve výchozím nastavení, tato metoda šetří všechny vlastnosti, bez ohledu na hodnotu *fSaveAllProperties*.

Zobrazit [IPersistPropertyBag::Save](/previous-versions/windows/internet-explorer/ie-developer/platform-apis/aa768207\(v=vs.85\)) ve Windows SDK.

## <a name="see-also"></a>Viz také:

[BEGIN_PROP_MAP](property-map-macros.md#begin_prop_map)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
