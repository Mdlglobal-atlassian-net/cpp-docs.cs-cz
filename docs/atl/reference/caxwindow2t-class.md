---
title: Třída CAxWindow2T
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
ms.openlocfilehash: 14080b624132979df533135bc1eef108dc793398
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81318702"
---
# <a name="caxwindow2t-class"></a>Třída CAxWindow2T

Tato třída poskytuje metody pro manipulaci s oknem, které je hostitelem ovládacího prvku ActiveX, a má také podporu pro hostování licencovaných ovládacích prvků ActiveX.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class TBase = CWindow>
    class CAxWindow2T :
    public CAxWindowT<TBase>
```

#### <a name="parameters"></a>Parametry

*TBase*<br/>
Třída, ze `CAxWindowT` které odvozuje.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[CAxWindow2T::CAxWindow2T](#caxwindow2t)|Vytvoří `CAxWindow2T` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CAxWindow2T::Vytvořit](#create)|Vytvoří okno hostitele.|
|[CAxWindow2T::CreateControlLic](#createcontrollic)|Vytvoří, licencuje a hostuje ovládací prvek ActiveX v zadaném okně.|
|[CAxWindow2T::CreateControlLicEx](#createcontrollicex)|Vytvoří licencovaný ovládací prvek ActiveX, inicializuje jej, hostuje v zadaném okně a načítá ukazatel rozhraní (nebo ukazatele) z ovládacího prvku.|
|[CAxWindow2T::GetWndClassName](#getwndclassname)|Statická metoda, která načte název třídy okna.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[CAxWindow2T::operátor =](#operator_eq)|Přiřadí HWND existujícímu `CAxWindow2T` objektu.|

## <a name="remarks"></a>Poznámky

`CAxWindow2T`poskytuje metody pro manipulaci s oknem, které je hostitelem ovládacího prvku ActiveX. `CAxWindow2T`má také podporu pro hostování licencovaných ovládacích prvků ActiveX. Hosting je poskytován " **AtlAxWinLic80**", který `CAxWindow2T`je zabalen .

Třída `CAxWindow2` je implementována jako `CAxWindow2T` specializace třídy. Tato specializace je deklarována jako:

`typedef CAxWindow2T <CWindow> CAxWindow2;`

> [!NOTE]
> `CAxWindowT`členové jsou dokumentovány pod [CAxWindow](../../atl/reference/caxwindow-class.md).

Viz [Hostování ovládacích prvků ActiveX pomocí ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pro ukázku, která používá členy této třídy.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`TBase`

`CAxWindowT`

`CAxWindow2T`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

## <a name="caxwindow2tcaxwindow2t"></a><a name="caxwindow2t"></a>CAxWindow2T::CAxWindow2T

Vytvoří `CAxWindow2T` objekt.

```
CAxWindow2T(HWND  hWnd = NULL) : CAxWindowT<TBase>(hWnd)
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
Popisovač existujícího okna.

## <a name="caxwindow2tcreate"></a><a name="create"></a>CAxWindow2T::Vytvořit

Vytvoří okno hostitele.

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

`CAxWindow2T::Create`volání [CWindow::Create](../../atl/reference/cwindow-class.md#create) s parametrem *LpstrWndClass* LPCTSTR nastaveným na`AtlAxWinLic80`třídu okna, která poskytuje hostování ovládacího prvku ( ).

Viz `CWindow::Create` popis parametrů a vrácené hodnoty.

**Poznámka:** Pokud 0 se používá jako hodnota pro *MenuOrID* parametr, musí být zadán jako 0U (výchozí hodnota), aby se zabránilo chybě kompilátoru.

### <a name="example"></a>Příklad

Viz [Hostování ovládacích prvků ActiveX pomocí ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pro ukázku, která používá `CAxWindow2T::Create`.

## <a name="caxwindow2tcreatecontrollic"></a><a name="createcontrollic"></a>CAxWindow2T::CreateControlLic

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
Licenční klíč pro ovládací prvek; Null při vytváření nelicencovaného ovládacího prvku.

### <a name="remarks"></a>Poznámky

Viz [CAxWindow::CreateControl](../../atl/reference/caxwindow-class.md#createcontrol) pro popis zbývajících parametrů a vrácené hodnoty.

### <a name="example"></a>Příklad

Viz [Hostování ovládacích prvků ActiveX pomocí ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pro ukázku, která používá `CAxWindow2T::CreateControlLic`.

## <a name="caxwindow2tcreatecontrollicex"></a><a name="createcontrollicex"></a>CAxWindow2T::CreateControlLicEx

Vytvoří licencovaný ovládací prvek ActiveX, inicializuje jej, hostuje v zadaném okně a načítá ukazatel rozhraní (nebo ukazatele) z ovládacího prvku.

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
Licenční klíč pro ovládací prvek; Null při vytváření nelicencovaného ovládacího prvku.

### <a name="remarks"></a>Poznámky

Viz [CAxWindow::CreateControlEx](../../atl/reference/caxwindow-class.md#createcontrolex) popis zbývajících parametrů a vrácené hodnoty.

### <a name="example"></a>Příklad

Viz [Hostování ovládacích prvků ActiveX pomocí ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) pro ukázku, která používá `CAxWindow2T::CreateControlLicEx`.

## <a name="caxwindow2tgetwndclassname"></a><a name="getwndclassname"></a>CAxWindow2T::GetWndClassName

Načte název třídy okna.

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na řetězec obsahující název třídy okna`AtlAxWinLic80`( ), který může hostovat licencované a nelicencované ovládací prvky ActiveX.

## <a name="caxwindow2toperator-"></a><a name="operator_eq"></a>CAxWindow2T::operátor =

Přiřadí HWND existujícímu `CAxWindow2T` objektu.

```
CAxWindow2T<TBase>& operator= (HWND hWnd);
```

### <a name="parameters"></a>Parametry

*Hwnd*<br/>
Popisovač existujícího okna.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Nejčastější dotazy týkající se omezení řízení](../../atl/atl-control-containment-faq.md)
