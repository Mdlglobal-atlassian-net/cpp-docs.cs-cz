---
title: Třída IPointerInactiveImpl
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
ms.openlocfilehash: 229b8c6803aa7b3817cb3d95474bde0502829f8b
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326452"
---
# <a name="ipointerinactiveimpl-class"></a>Třída IPointerInactiveImpl

Tato třída `IUnknown` implementuje a metody rozhraní [IPointerInactive.](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive)

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class IPointerInactiveImpl
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, odvozená z `IPointerInactiveImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[IPointerInactiveImpl::GetActivationPolicy](#getactivationpolicy)|Načte aktuální zásady aktivace objektu. Implementace ATL vrátí E_NOTIMPL.|
|[IPointerInactiveImpl::OnInactiveMouseMove](#oninactivemousemove)|Upozorní objekt, který se přes něj přesunul ukazatel myši, což znamená, že objekt může vypálit události myši. Implementace ATL vrátí E_NOTIMPL.|
|[IPointerInactiveImpl::OnInactiveSetCursor](#oninactivesetcursor)|Nastaví ukazatel myši pro neaktivní objekt. Implementace ATL vrátí E_NOTIMPL.|

## <a name="remarks"></a>Poznámky

Neaktivní objekt je objekt, který je jednoduše načten nebo spuštěn. Na rozdíl od aktivního objektu nemůže neaktivní objekt přijímat zprávy myši a klávesnice systému Windows. Neaktivní objekty tedy používají méně prostředků a jsou obvykle efektivnější.

[Rozhraní IPointerInactive](/windows/win32/api/ocidl/nn-ocidl-ipointerinactive) umožňuje objektu podporovat minimální úroveň interakce myši při zachování neaktivní. Tato funkce je zvláště užitečná pro ovládací prvky.

Class `IPointerInactiveImpl` implementuje `IPointerInactive` metody jednoduše vrácení min. E_NOTIMPL. Však implementuje `IUnknown` odesláním informací do zařízení výpisu v sestavení ladění.

**Související články** [ATL Výuka](../../atl/active-template-library-atl-tutorial.md), [Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IPointerInactive`

`IPointerInactiveImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

## <a name="ipointerinactiveimplgetactivationpolicy"></a><a name="getactivationpolicy"></a>IPointerInactiveImpl::GetActivationPolicy

Načte aktuální zásady aktivace objektu.

```
HRESULT GetActivationPolicy(DWORD* pdwPolicy);
```

### <a name="return-value"></a>Návratová hodnota

Vrátí E_NOTIMPL.

### <a name="remarks"></a>Poznámky

Viz [IPointerInactive::GetActivationPolicy](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-getactivationpolicy) v sadě Windows SDK.

## <a name="ipointerinactiveimploninactivemousemove"></a><a name="oninactivemousemove"></a>IPointerInactiveImpl::OnInactiveMouseMove

Upozorní objekt, který se přes něj přesunul ukazatel myši, což znamená, že objekt může vypálit události myši.

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

Viz [IPointerInactive::OnInactiveMouseMove](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-oninactivemousemove) v sadě Windows SDK.

## <a name="ipointerinactiveimploninactivesetcursor"></a><a name="oninactivesetcursor"></a>IPointerInactiveImpl::OnInactiveSetCursor

Nastaví ukazatel myši pro neaktivní objekt.

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

Viz [IPointerInactive::OnInactiveSetCursor](/windows/win32/api/ocidl/nf-ocidl-ipointerinactive-oninactivesetcursor) v sadě Windows SDK.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
