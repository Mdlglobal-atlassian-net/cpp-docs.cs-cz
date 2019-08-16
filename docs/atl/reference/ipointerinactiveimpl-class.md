---
title: IPointerInactiveImpl – třída
ms.date: 11/04/2016
f1_keywords:
- IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl
- ATLCTL/ATL::IPointerInactiveImpl::GetActivationPolicy
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveMouseMove
- ATLCTL/ATL::IPointerInactiveImpl::OnInactiveSetCursor
helpviewer_keywords:
- IPointerInactive ATL implementation
- inactive objects
- IPointerInactiveImpl class
ms.assetid: e1fe9ea6-d38a-4527-9112-eb344771e0b7
ms.openlocfilehash: 6fb5d9f2bcbdeda61f32947bf339d134c4924b72
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495658"
---
# <a name="ipointerinactiveimpl-class"></a>IPointerInactiveImpl – třída

Tato třída implementuje `IUnknown` a metody rozhraní [IPointerInactive](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive) .

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IPointerInactiveImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, která je `IPointerInactiveImpl`odvozena z.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[IPointerInactiveImpl::GetActivationPolicy](#getactivationpolicy)|Načte aktuální zásady aktivace pro objekt. Implementace ATL Vrátí E_NOTIMPL.|
|[IPointerInactiveImpl::OnInactiveMouseMove](#oninactivemousemove)|Upozorní objekt, že v něm byl přesunut ukazatel myši, což značí, že objekt může aktivovat události myši. Implementace ATL Vrátí E_NOTIMPL.|
|[IPointerInactiveImpl::OnInactiveSetCursor](#oninactivesetcursor)|Nastaví ukazatel myši na neaktivní objekt. Implementace ATL Vrátí E_NOTIMPL.|

## <a name="remarks"></a>Poznámky

Neaktivním objektem je jeden, který se jednoduše načte nebo spustí. Na rozdíl od aktivního objektu nemůže neaktivní objekt přijímat zprávy myši a klávesnice systému Windows. Proto neaktivní objekty využívají méně prostředků a jsou obvykle efektivnější.

Rozhraní [IPointerInactive](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive) umožňuje objektu podporovat minimální úroveň interakce myši, ale zbývající neaktivní. Tato funkce je zvláště užitečná pro ovládací prvky.

`IPointerInactiveImpl` Třída`IPointerInactive` implementuje metody pouhým vrácením E_NOTIMPL. Nicméně implementuje `IUnknown` odesláním informací do zařízení výpisu paměti v sestavení ladění.

**Související články** [Kurz ATL](../../atl/active-template-library-atl-tutorial.md), [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IPointerInactive`

`IPointerInactiveImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl. h

##  <a name="getactivationpolicy"></a>IPointerInactiveImpl::GetActivationPolicy

Načte aktuální zásady aktivace pro objekt.

```
HRESULT GetActivationPolicy(DWORD* pdwPolicy);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Viz [IPointerInactive:: GetActivationPolicy](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-getactivationpolicy) v Windows SDK.

##  <a name="oninactivemousemove"></a>  IPointerInactiveImpl::OnInactiveMouseMove

Upozorní objekt, že v něm byl přesunut ukazatel myši, což značí, že objekt může aktivovat události myši.

```
HRESULT OnInactiveMouseMove(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Viz [IPointerInactive:: OnInactiveMouseMove](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-oninactivemousemove) v Windows SDK.

##  <a name="oninactivesetcursor"></a>  IPointerInactiveImpl::OnInactiveSetCursor

Nastaví ukazatel myši na neaktivní objekt.

```
HRESULT OnInactiveSetCursor(
    LPCRECT pRectBounds,
    long x,
    long y,
    DWORD dwMouseMsg,
    BOOL fSetAlways);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Viz [IPointerInactive:: OnInactiveSetCursor](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-oninactivesetcursor) v Windows SDK.

## <a name="see-also"></a>Viz také:

[Přehled třídy](../../atl/atl-class-overview.md)
