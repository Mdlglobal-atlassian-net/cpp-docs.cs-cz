---
title: CAxWindow2T – třída
ms.date: 11/04/2016
f1_keywords:
- CAxWindow2T
- ATLWIN/ATL::CAxWindow2T
- ATLWIN/ATL::CAxWindow2T::CAxWindow2T
- ATLWIN/ATL::CAxWindow2T::Create
- ATLWIN/ATL::CAxWindow2T::CreateControlLic
- ATLWIN/ATL::CAxWindow2T::CreateControlLicEx
- ATLWIN/ATL::CAxWindow2T::GetWndClassName
helpviewer_keywords:
- CAxWindow2 class
ms.assetid: b87bc943-7991-4537-b902-2138d7f4d837
ms.openlocfilehash: 0d5991dcbf79d1c2415594636a09908586d1dc2f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417990"
---
# <a name="caxwindow2t-class"></a>CAxWindow2T – třída

Tato třída poskytuje metody pro práci s oknem, který je hostitelem ovládacího prvku ActiveX, a také podporuje hostování licencovaných ovládacích prvků ActiveX.

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class TBase = CWindow>
    class CAxWindow2T :
    public CAxWindowT<TBase>
```

#### <a name="parameters"></a>Parametry

*TBase*<br/>
Třída, ze které `CAxWindowT` odvozena.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAxWindow2T::CAxWindow2T](#caxwindow2t)|Vytvoří objekt `CAxWindow2T`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAxWindow2T:: Create](#create)|Vytvoří hostitelské okno.|
|[CAxWindow2T::CreateControlLic](#createcontrollic)|Vytvoří, licencuje a hostuje ovládací prvek ActiveX v zadaném okně.|
|[CAxWindow2T::CreateControlLicEx](#createcontrollicex)|Vytvoří licencovaný ovládací prvek ActiveX, inicializuje ho, hostuje ho v zadaném okně a načte ukazatel rozhraní (nebo ukazatele) z ovládacího prvku.|
|[CAxWindow2T::GetWndClassName](#getwndclassname)|Statická metoda, která načte název třídy okna.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CAxWindow2T:: operator =](#operator_eq)|Přiřadí HWND k existujícímu objektu `CAxWindow2T`.|

## <a name="remarks"></a>Poznámky

`CAxWindow2T` poskytuje metody pro práci s oknem, který je hostitelem ovládacího prvku ActiveX. `CAxWindow2T` také podporuje hostování licencovaných ovládacích prvků ActiveX. Hostování poskytuje " **AtlAxWinLic80**", který je zabalen pomocí `CAxWindow2T`.

`CAxWindow2` třídy je implementována jako specializace `CAxWindow2T` třídy. Tato specializace je deklarována jako:

`typedef CAxWindow2T <CWindow> CAxWindow2;`

> [!NOTE]
> `CAxWindowT` členové jsou popsány v části [CAxWindow](../../atl/reference/caxwindow-class.md).

Viz [hostování ovládacích prvků ActiveX pomocí ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pro ukázku, která používá členy této třídy.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`TBase`

`CAxWindowT`

`CAxWindow2T`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

##  <a name="caxwindow2t"></a>CAxWindow2T::CAxWindow2T

Vytvoří objekt `CAxWindow2T`.

```
CAxWindow2T(HWND  hWnd = NULL) : CAxWindowT<TBase>(hWnd)
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
Popisovač stávajícího okna.

##  <a name="create"></a>CAxWindow2T:: Create

Vytvoří hostitelské okno.

```
HWND Create(
    HWND hWndParent,
    _U_RECT rect = NULL,
    LPCTSTR szWindowName = NULL,
    DWORD dwStyle = 0,
    DWORD dwExStyle = 0,
    _U_MENUorID MenuOrID = 0U,
    LPVOID lpCreateParam = NULL);
```

### <a name="remarks"></a>Poznámky

`CAxWindow2T::Create` volá [CWindow:: Create](../../atl/reference/cwindow-class.md#create) s parametrem *lpstrWndClass* LPCTSTR nastaveným na třídu Window, která poskytuje hostování ovládacího prvku (`AtlAxWinLic80`).

Popis parametrů a návratové hodnoty naleznete v tématu `CWindow::Create`.

**Poznámka:** Pokud se hodnota 0 používá jako hodnota parametru *MenuOrID* , musí být zadána jako 0U (výchozí hodnota), aby se předešlo chybě kompilátoru.

### <a name="example"></a>Příklad

Ukázku, která používá `CAxWindow2T::Create`, najdete v tématu [hostování ovládacích prvků ActiveX pomocí ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) .

##  <a name="createcontrollic"></a>CAxWindow2T::CreateControlLic

Vytvoří, licencuje a hostuje ovládací prvek ActiveX v zadaném okně.

```
HRESULT CreateControlLic(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    BSTR bstrLicKey = NULL);

HRESULT CreateControlLic(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    BSTR bstrLicKey = NULL);
```

### <a name="parameters"></a>Parametry

*bstrLicKey*<br/>
Licenční klíč pro ovládací prvek; Hodnota NULL při vytváření nelicencovaného ovládacího prvku

### <a name="remarks"></a>Poznámky

Popis zbývajících parametrů a návratové hodnoty naleznete v tématu [CAxWindow:: CreateControl](../../atl/reference/caxwindow-class.md#createcontrol) .

### <a name="example"></a>Příklad

Ukázku, která používá `CAxWindow2T::CreateControlLic`, najdete v tématu [hostování ovládacích prvků ActiveX pomocí ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) .

##  <a name="createcontrollicex"></a>CAxWindow2T::CreateControlLicEx

Vytvoří licencovaný ovládací prvek ActiveX, inicializuje ho, hostuje ho v zadaném okně a načte ukazatel rozhraní (nebo ukazatele) z ovládacího prvku.

```
HRESULT CreateControlLicEx(
    LPCOLESTR lpszName,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL,
    BSTR bstrLicKey = NULL);

    HRESULT CreateControlLicEx(
    DWORD dwResID,
    IStream* pStream = NULL,
    IUnknown** ppUnkContainer = NULL,
    IUnknown** ppUnkControl = NULL,
    REFIID iidSink = IID_NULL,
    IUnknown* punkSink = NULL,
    BSTR bstrLickey = NULL);
```

### <a name="parameters"></a>Parametry

*bstrLicKey*<br/>
Licenční klíč pro ovládací prvek; Hodnota NULL při vytváření nelicencovaného ovládacího prvku

### <a name="remarks"></a>Poznámky

Popis zbývajících parametrů a návratové hodnoty naleznete v tématu [CAxWindow:: CreateControlEx](../../atl/reference/caxwindow-class.md#createcontrolex) .

### <a name="example"></a>Příklad

Ukázku, která používá `CAxWindow2T::CreateControlLicEx`, najdete v tématu [hostování ovládacích prvků ActiveX pomocí ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) .

##  <a name="getwndclassname"></a>CAxWindow2T::GetWndClassName

Načte název třídy okna.

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na řetězec obsahující název třídy okna (`AtlAxWinLic80`), která může hostovat licencované a nelicencované ovládací prvky ActiveX.

##  <a name="operator_eq"></a>CAxWindow2T:: operator =

Přiřadí HWND k existujícímu objektu `CAxWindow2T`.

```
CAxWindow2T<TBase>& operator= (HWND hWnd);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
Popisovač stávajícího okna.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Nejčastější dotazy k omezením řízení](../../atl/atl-control-containment-faq.md)
