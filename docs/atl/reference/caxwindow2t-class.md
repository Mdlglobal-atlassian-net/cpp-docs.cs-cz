---
title: CAxWindow2T Class
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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62260025"
---
# <a name="caxwindow2t-class"></a>CAxWindow2T Class

Tato třída poskytuje metody pro práci s okno, které hostuje ovládací prvek ActiveX a také zahrnuje podporu pro hostování licencované ovládací prvky ActiveX.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class TBase = CWindow>
    class CAxWindow2T :
    public CAxWindowT<TBase>
```

#### <a name="parameters"></a>Parametry

*TBase*<br/>
Třída, ze které `CAxWindowT` je odvozena.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[CAxWindow2T::CAxWindow2T](#caxwindow2t)|Vytvoří `CAxWindow2T` objektu.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CAxWindow2T::Create](#create)|Vytvoří okno hostitele.|
|[CAxWindow2T::CreateControlLic](#createcontrollic)|Vytvoří, licencuje a hostuje ovládací prvek ActiveX v zadaném okně.|
|[CAxWindow2T::CreateControlLicEx](#createcontrollicex)|Vytvoří licencovaného ovládacího prvku ActiveX, inicializuje ji, hostuje v zadaném okně a načte ukazatel rozhraní (nebo ukazatele) z ovládacího prvku.|
|[CAxWindow2T::GetWndClassName](#getwndclassname)|Statická metoda, která načte název třídy okna.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[CAxWindow2T::operator =](#operator_eq)|Přiřadí existující popisovačem HWND `CAxWindow2T` objektu.|

## <a name="remarks"></a>Poznámky

`CAxWindow2T` poskytuje metody pro práci, který je hostitelem okna ovládacího prvku ActiveX. `CAxWindow2T` má také podporu hostování licencované ovládací prvky ActiveX. Hostování je poskytován " **AtlAxWinLic80**", která je zabalena `CAxWindow2T`.

Třída `CAxWindow2` je implementovaný jako specializací `CAxWindow2T` třídy. Tato specializace je deklarován jako:

`typedef CAxWindow2T <CWindow> CAxWindow2;`

> [!NOTE]
> `CAxWindowT` Členové jsou popsány v části [caxwindow –](../../atl/reference/caxwindow-class.md).

Zobrazit [hostování ActiveX ovládacích prvků pomocí knihovny ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) ukázku, která používá členy této třídy.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`TBase`

`CAxWindowT`

`CAxWindow2T`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

##  <a name="caxwindow2t"></a>  CAxWindow2T::CAxWindow2T

Vytvoří `CAxWindow2T` objektu.

```
CAxWindow2T(HWND  hWnd = NULL) : CAxWindowT<TBase>(hWnd)
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
Popisovač existujícímu oknu.

##  <a name="create"></a>  CAxWindow2T::Create

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

`CAxWindow2T::Create` volání [CWindow::Create](../../atl/reference/cwindow-class.md#create) s LPCTSTR *lpstrWndClass* parametr nastaven na třídu okna, která poskytuje hostování ovládacího prvku (`AtlAxWinLic80`).

Zobrazit `CWindow::Create` popis parametrů a návratové hodnoty.

**Poznámka:** Pokud se použije jako hodnota 0 *MenuOrID* parametru, musí být zadán jako 0U (výchozí hodnota), aby chybu kompilátoru.

### <a name="example"></a>Příklad

Zobrazit [hostování ActiveX ovládacích prvků pomocí knihovny ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) ukázku, která používá `CAxWindow2T::Create`.

##  <a name="createcontrollic"></a>  CAxWindow2T::CreateControlLic

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
Licenční klíč pro ovládací prvek; Pokud vytváříte nonlicensed ovládacího prvku s hodnotou NULL.

### <a name="remarks"></a>Poznámky

Zobrazit [CAxWindow::CreateControl](../../atl/reference/caxwindow-class.md#createcontrol) popis zbývající parametry a návratové hodnoty.

### <a name="example"></a>Příklad

Zobrazit [hostování ActiveX ovládacích prvků pomocí knihovny ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) ukázku, která používá `CAxWindow2T::CreateControlLic`.

##  <a name="createcontrollicex"></a>  CAxWindow2T::CreateControlLicEx

Vytvoří licencovaného ovládacího prvku ActiveX, inicializuje ji, hostuje v zadaném okně a načte ukazatel rozhraní (nebo ukazatele) z ovládacího prvku.

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
Licenční klíč pro ovládací prvek; Pokud vytváříte nonlicensed ovládacího prvku s hodnotou NULL.

### <a name="remarks"></a>Poznámky

Zobrazit [CAxWindow::CreateControlEx](../../atl/reference/caxwindow-class.md#createcontrolex) popis zbývající parametry a návratové hodnoty.

### <a name="example"></a>Příklad

Zobrazit [hostování ActiveX ovládacích prvků pomocí knihovny ATL AXHost](../../atl/hosting-activex-controls-using-atl-axhost.md) ukázku, která používá `CAxWindow2T::CreateControlLicEx`.

##  <a name="getwndclassname"></a>  CAxWindow2T::GetWndClassName

Načte název třídy okna.

```
static LPCTSTR GetWndClassName();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na řetězec obsahující název třídy okna (`AtlAxWinLic80`), který může hostovat licencovanou a nonlicensed ovládací prvky ActiveX.

##  <a name="operator_eq"></a>  CAxWindow2T::operator =

Přiřadí existující popisovačem HWND `CAxWindow2T` objektu.

```
CAxWindow2T<TBase>& operator= (HWND hWnd);
```

### <a name="parameters"></a>Parametry

*hWnd*<br/>
Popisovač existujícímu oknu.

## <a name="see-also"></a>Viz také:

[Přehled tříd](../../atl/atl-class-overview.md)<br/>
[Nejčastější dotazy k používání kontejnerů ovládacích prvků](../../atl/atl-control-containment-faq.md)
