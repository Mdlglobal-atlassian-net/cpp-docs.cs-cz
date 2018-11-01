---
title: Ipointerinactiveimpl – třída
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
ms.openlocfilehash: 2c072dd158616b04d10e4aed091c7e26a3512ce1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50487890"
---
# <a name="ipointerinactiveimpl-class"></a>Ipointerinactiveimpl – třída

Tato třída implementuje `IUnknown` a [IPointerInactive](/windows/desktop/api/ocidl/nn-ocidl-ipointerinactive) metody rozhraní.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IPointerInactiveImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída odvozena od `IPointerInactiveImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IPointerInactiveImpl::GetActivationPolicy](#getactivationpolicy)|Načte aktuální zásady aktivace pro objekt. Implementace knihovny ATL vrátí E_NOTIMPL.|
|[IPointerInactiveImpl::OnInactiveMouseMove](#oninactivemousemove)|Upozorní, že objekt, který se přesunul ukazatel myši nad ním, označující objekt může vyvolat události myši. Implementace knihovny ATL vrátí E_NOTIMPL.|
|[IPointerInactiveImpl::OnInactiveSetCursor](#oninactivesetcursor)|Nastaví ukazatel myši pro aktivní objekt. Implementace knihovny ATL vrátí E_NOTIMPL.|

## <a name="remarks"></a>Poznámky

Neaktivním objektem je takový, který je jednoduše načíst nebo spuštěné. Na rozdíl od aktivního objektu neaktivním objektem nemůže přijímat zprávy myši a klávesnice Windows. Díky tomu se neaktivní objekty používají méně prostředků a jsou obvykle mnohem efektivnější.

[IPointerInactive](/windows/desktop/api/ocidl/nn-ocidl-ipointerinactive) rozhraní umožňuje podporu minimální úroveň interakce s myší zbývající neaktivní. Tato funkce je zvláště užitečná pro ovládací prvky.

Třída `IPointerInactiveImpl` implementuje `IPointerInactive` metody jednoduše vrácením E_NOTIMPL. Nicméně, implementuje `IUnknown` posíláním informací o k výpisu paměti zařízení v ladění sestavení.

**Související články** [ATL – tutoriál](../../atl/active-template-library-atl-tutorial.md), [vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IPointerInactive`

`IPointerInactiveImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

##  <a name="getactivationpolicy"></a>  IPointerInactiveImpl::GetActivationPolicy

Načte aktuální zásady aktivace pro objekt.

```
HRESULT GetActivationPolicy(DWORD* pdwPolicy);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Zobrazit [IPointerInactive::GetActivationPolicy](/windows/desktop/api/ocidl/nf-ocidl-ipointerinactive-getactivationpolicy) ve Windows SDK.

##  <a name="oninactivemousemove"></a>  IPointerInactiveImpl::OnInactiveMouseMove

Upozorní, že objekt, který se přesunul ukazatel myši nad ním, označující objekt může vyvolat události myši.

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

Zobrazit [IPointerInactive::OnInactiveMouseMove](/windows/desktop/api/ocidl/nf-ocidl-ipointerinactive-oninactivemousemove) ve Windows SDK.

##  <a name="oninactivesetcursor"></a>  IPointerInactiveImpl::OnInactiveSetCursor

Nastaví ukazatel myši pro aktivní objekt.

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

Zobrazit [IPointerInactive::OnInactiveSetCursor](/windows/desktop/api/ocidl/nf-ocidl-ipointerinactive-oninactivesetcursor) ve Windows SDK.

## <a name="see-also"></a>Viz také

[Přehled tříd](../../atl/atl-class-overview.md)
