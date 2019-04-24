---
title: Iviewobjecteximpl – třída
ms.date: 11/04/2016
f1_keywords:
- IViewObjectExImpl
- ATLCTL/ATL::IViewObjectExImpl
- ATLCTL/ATL::IViewObjectExImpl::Draw
- ATLCTL/ATL::IViewObjectExImpl::Freeze
- ATLCTL/ATL::IViewObjectExImpl::GetAdvise
- ATLCTL/ATL::IViewObjectExImpl::GetColorSet
- ATLCTL/ATL::IViewObjectExImpl::GetExtent
- ATLCTL/ATL::IViewObjectExImpl::GetNaturalExtent
- ATLCTL/ATL::IViewObjectExImpl::GetRect
- ATLCTL/ATL::IViewObjectExImpl::GetViewStatus
- ATLCTL/ATL::IViewObjectExImpl::QueryHitPoint
- ATLCTL/ATL::IViewObjectExImpl::QueryHitRect
- ATLCTL/ATL::IViewObjectExImpl::SetAdvise
- ATLCTL/ATL::IViewObjectExImpl::Unfreeze
helpviewer_keywords:
- ActiveX controls [C++], drawing
- IViewObjectEx ATL implementation
- advise sinks
- IViewObjectExImpl class
ms.assetid: ad6de760-1ee5-4883-b033-ae57beffc369
ms.openlocfilehash: 4ed7a7e4a6070ba52c54c4dace687111cf7d33d8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62198210"
---
# <a name="iviewobjecteximpl-class"></a>Iviewobjecteximpl – třída

Tato třída implementuje `IUnknown` a poskytuje výchozí implementaci [IViewObject](/windows/desktop/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/desktop/api/oleidl/nn-oleidl-iviewobject2), a [IViewObjectEx](/windows/desktop/api/ocidl/nn-ocidl-iviewobjectex) rozhraní.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class ATL_NO_VTABLE IViewObjectExImpl
   : public IViewObjectEx
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída odvozena od `IViewObjectExImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[IViewObjectExImpl::Draw](#draw)|Nakreslí znázornění ovládacího prvku do kontextu zařízení.|
|[IViewObjectExImpl::Freeze](#freeze)|Zablokuje vykresleného reprezentace ovládacího prvku, nezmění se do `Unfreeze`. Implementace knihovny ATL vrátí E_NOTIMPL.|
|[IViewObjectExImpl::GetAdvise](#getadvise)|Načte existující připojení advisory jímky na ovládacím prvku, pokud existuje.|
|[IViewObjectExImpl::GetColorSet](#getcolorset)|Vrátí logickou paletu použit v ovládacím prvku pro kreslení. Implementace knihovny ATL vrátí E_NOTIMPL.|
|[IViewObjectExImpl::GetExtent](#getextent)|Získá velikost zobrazení ovládacího prvku v jednotkách HIMETRIC (za jednotku 0,01 milimetru) z datový člen třídy ovládacího prvku [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).|
|[IViewObjectExImpl::GetNaturalExtent](#getnaturalextent)|Poskytuje tipy pro změnu velikosti z kontejneru pro objekt, který chcete použít, protože ji uživatel změní.|
|[IViewObjectExImpl::GetRect](#getrect)|Vrací obdélník popisující požadovaný aspekt kreslení. Implementace knihovny ATL vrátí E_NOTIMPL.|
|[IViewObjectExImpl::GetViewStatus](#getviewstatus)|Vrátí informace o neprůhlednost objektu a jaké aspekty kresby jsou podporované.|
|[IViewObjectExImpl::QueryHitPoint](#queryhitpoint)|Zkontroluje, jestli se zadaný bod je v zadané obdélníku a vrátí [HITRESULT](/windows/desktop/api/ocidl/ne-ocidl-taghitresult) hodnota v `pHitResult`.|
|[IViewObjectExImpl::QueryHitRect](#queryhitrect)|Ověří, zda ovládacího prvku zobrazovací obdélník překrývá libovolný bod v obdélníku zadaného umístění a vrátí hodnotu HITRESULT v `pHitResult`.|
|[IViewObjectExImpl::SetAdvise](#setadvise)|Nastaví spojení mezi ovládacím prvkem a jímky doporučení tak jímka můžete být upozorněni o změnách v zobrazení ovládacího prvku.|
|[IViewObjectExImpl::Unfreeze](#unfreeze)|Zruší ukotvení vykresleného reprezentace ovládacího prvku. Implementace knihovny ATL vrátí E_NOTIMPL.|

## <a name="remarks"></a>Poznámky

[IViewObject](/windows/desktop/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/desktop/api/oleidl/nn-oleidl-iviewobject2), a [IViewObjectEx](/windows/desktop/api/ocidl/nn-ocidl-iviewobjectex) rozhraní umožňují ovládací prvek zobrazení samotného přímo nebo můžete vytvářet a spravovat jímky doporučení upozornit kontejner změny v zobrazení ovládacího prvku. `IViewObjectEx` Rozhraní poskytuje podporu pro rozšířené ovládací prvek funkcí jako jsou blikání kreslení, průhledných a neobdélníkových ovládací prvky a spuštění testu (například jak blízko kliknutí myší musí být považovat na ovládacím prvku). Třída `IViewObjectExImpl` poskytuje výchozí implementaci těchto rozhraní a implementuje `IUnknown` posíláním informací o k výpisu paměti zařízení v ladění sestavení.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IViewObjectEx`

`IViewObjectExImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

##  <a name="draw"></a>  IViewObjectExImpl::Draw

Nakreslí znázornění ovládacího prvku do kontextu zařízení.

```
STDMETHOD(Draw)(
    DWORD dwDrawAspect,
    LONG lindex,
    void* pvAspect,
    DVTARGETDEVICE* ptd,
    HDC hicTargetDev,
    LPCRECTL prcBounds,
    LPCRECTL prcWBounds,
    BOOL(_stdcall* /* pfnContinue*/) (DWORD_PTR dwContinue),
    DWORD_PTR /* dwContinue */);
```

### <a name="remarks"></a>Poznámky

Tato metoda volá `CComControl::OnDrawAdvanced` která pak volá třídy vašeho ovládacího prvku `OnDraw` metody. `OnDraw` Metoda je automaticky přidán do třídy vašeho ovládacího prvku při vytváření ovládacího prvku pomocí Průvodce ovládacími prvky ATL. Průvodce výchozí `OnDraw` kreslení obdélníku s popiskem "ATL 3.0".

Zobrazit [IViewObject::Draw](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-draw) ve Windows SDK.

##  <a name="freeze"></a>  IViewObjectExImpl::Freeze

Zablokuje vykresleného reprezentace ovládacího prvku, nezmění se do `Unfreeze`. Implementace knihovny ATL vrátí E_NOTIMPL.

```
STDMETHOD(Freeze)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DWORD* /* pdwFreeze */);
```

### <a name="remarks"></a>Poznámky

Zobrazit [IViewObject::Freeze](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-freeze) ve Windows SDK.

##  <a name="getadvise"></a>  IViewObjectExImpl::GetAdvise

Načte existující připojení advisory jímky na ovládacím prvku, pokud existuje.

```
STDMETHOD(GetAdvise)(
    DWORD* /* pAspects */,
    DWORD* /* pAdvf */,
    IAdviseSink** /* ppAdvSink */);
```

### <a name="remarks"></a>Poznámky

Poradní jímka jsou uložena v datový člen třídy ovládacího prvku [CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink).

Zobrazit [IViewObject::GetAdvise](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-getadvise) ve Windows SDK.

##  <a name="getcolorset"></a>  IViewObjectExImpl::GetColorSet

Vrátí logickou paletu použit v ovládacím prvku pro kreslení. Implementace knihovny ATL vrátí E_NOTIMPL.

```
STDMETHOD(GetColorSet)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DVTARGETDEVICE* /* ptd */,
    HDC /* hicTargetDevice */,
    LOGPALETTE** /* ppColorSet */);
```

### <a name="remarks"></a>Poznámky

Zobrazit [IViewObject::GetColorSet](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-getcolorset) ve Windows SDK.

##  <a name="getextent"></a>  IViewObjectExImpl::GetExtent

Získá velikost zobrazení ovládacího prvku v jednotkách HIMETRIC (za jednotku 0,01 milimetru) z datový člen třídy ovládacího prvku [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).

```
STDMETHOD(GetExtent)(
    DWORD /* dwDrawAspect */,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    LPSIZEL* lpsizel);
```

### <a name="remarks"></a>Poznámky

Zobrazit [IViewObject2::GetExtent](/windows/desktop/api/oleidl/nf-oleidl-iviewobject2-getextent) ve Windows SDK.

##  <a name="getnaturalextent"></a>  IViewObjectExImpl::GetNaturalExtent

Poskytuje tipy pro změnu velikosti z kontejneru pro objekt, který chcete použít, protože ji uživatel změní.

```
STDMETHOD(GetNaturalExtent)(
    DWORD dwAspect,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    HDC /* hicTargetDevice */,
    DVEXTENTINFO* pExtentInfo,
    LPSIZEL psizel);
```

### <a name="remarks"></a>Poznámky

Pokud `dwAspect` je DVASPECT_CONTENT a *pExtentInfo -> dwExtentMode* DVEXTENT_CONTENT se nastaví * `psizel` na datový člen třídy ovládacího prvku [CComControlBase::m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural). V opačném případě vrátí chybu HRESULT.

Zobrazit [IViewObjectEx::GetNaturalExtent](/windows/desktop/api/ocidl/nf-ocidl-iviewobjectex-getnaturalextent) ve Windows SDK.

##  <a name="getrect"></a>  IViewObjectExImpl::GetRect

Vrací obdélník popisující požadovaný aspekt kreslení. Implementace knihovny ATL vrátí E_NOTIMPL.

```
STDMETHOD(GetRect)(DWORD /* dwAspect */, LPRECTL /* pRect */);
```

### <a name="remarks"></a>Poznámky

Zobrazit [IViewObjectEx::GetRect](/windows/desktop/api/ocidl/nf-ocidl-iviewobjectex-getrect) ve Windows SDK.

##  <a name="getviewstatus"></a>  IViewObjectExImpl::GetViewStatus

Vrátí informace o neprůhlednost objektu a jaké aspekty kresby jsou podporované.

```
STDMETHOD(GetViewStatus)(DWORD* pdwStatus);
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení, nastaví ATL `pdwStatus` do značí, že ovládací prvek podporuje VIEWSTATUS_OPAQUE (možné hodnoty jsou v [které](/windows/desktop/api/ocidl/ne-ocidl-tagviewstatus) výčet).

Zobrazit [IViewObjectEx::GetViewStatus](/windows/desktop/api/ocidl/nf-ocidl-iviewobjectex-getviewstatus) ve Windows SDK.

##  <a name="queryhitpoint"></a>  IViewObjectExImpl::QueryHitPoint

Zkontroluje, jestli se zadaný bod je v zadané obdélníku a vrátí [HITRESULT](/windows/desktop/api/ocidl/ne-ocidl-taghitresult) hodnota v `pHitResult`.

```
STDMETHOD(QueryHitPoint)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    POINT ptlLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```

### <a name="remarks"></a>Poznámky

Hodnota může být HITRESULT_HIT nebo HITRESULT_OUTSIDE.

Pokud `dwAspect` rovná [DVASPECT_CONTENT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect), metoda vrátí hodnotu S_OK. V opačném případě vrátí metoda E_FAIL.

Zobrazit [IViewObjectEx::QueryHitPoint](/windows/desktop/api/ocidl/nf-ocidl-iviewobjectex-queryhitpoint) ve Windows SDK.

##  <a name="queryhitrect"></a>  IViewObjectExImpl::QueryHitRect

Ověří, zda ovládací prvek zobrazovací obdélník překrývá libovolný bod v obdélníku zadaného umístění a vrátí [HITRESULT](/windows/desktop/api/ocidl/ne-ocidl-taghitresult) hodnota v `pHitResult`.

```
STDMETHOD(QueryHitRect)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    LPRECT prcLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```

### <a name="remarks"></a>Poznámky

Hodnota může být HITRESULT_HIT nebo HITRESULT_OUTSIDE.

Pokud `dwAspect` rovná [DVASPECT_CONTENT](/windows/desktop/api/wtypes/ne-wtypes-tagdvaspect), metoda vrátí hodnotu S_OK. V opačném případě vrátí metoda E_FAIL.

Zobrazit [IViewObjectEx::QueryHitRect](/windows/desktop/api/ocidl/nf-ocidl-iviewobjectex-queryhitrect) ve Windows SDK.

##  <a name="setadvise"></a>  IViewObjectExImpl::SetAdvise

Nastaví spojení mezi ovládacím prvkem a jímky doporučení tak jímka můžete být upozorněni o změnách v zobrazení ovládacího prvku.

```
STDMETHOD(SetAdvise)(
    DWORD /* aspects */,
    DWORD /* advf */,
    IAdviseSink* pAdvSink);
```

### <a name="remarks"></a>Poznámky

Ukazatel [IAdviseSink](/windows/desktop/api/objidl/nn-objidl-iadvisesink) rozhraní jímce doporučení je uložena v datovém členovi třídy ovládacího prvku [CComControlBase::m_spAdviseSink](ccomcontrolbase-class.md#m_spadvisesink).

Zobrazit [IViewObject::SetAdvise](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-setadvise) ve Windows SDK.

##  <a name="unfreeze"></a>  IViewObjectExImpl::Unfreeze

Zruší ukotvení vykresleného reprezentace ovládacího prvku. Implementace knihovny ATL vrátí E_NOTIMPL.

```
STDMETHOD(Unfreeze)(DWORD /* dwFreeze */);
```

### <a name="remarks"></a>Poznámky

Zobrazit [IViewObject::Unfreeze](/windows/desktop/api/oleidl/nf-oleidl-iviewobject-unfreeze) ve Windows SDK.

##  <a name="closehandle"></a>  IWorkerThreadClient::CloseHandle

Implementujte tuto metodu za účelem zavřít popisovač asociovaném s tímto objektem.

```
HRESULT CloseHandle(HANDLE hHandle);
```

### <a name="parameters"></a>Parametry

*hHandle*<br/>
Obslužná rutina bude uzavřen.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Popisovač předaný této metodě byla dříve přidružená k tomuto objektu voláním [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Příklad

Následující kód ukazuje jednoduchý provádění `IWorkerThreadClient::CloseHandle`.

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iviewobjecteximpl-class_1.cpp)]

##  <a name="execute"></a>  IWorkerThreadClient::Execute

Implementujte tuto metodu za účelem spouštění kódu, když se stane signalizován popisovač asociovaném s tímto objektem.

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>Parametry

*dwParam*<br/>
Tento parametr.

*hObject*<br/>
Obslužná rutina, která má být signalizovány.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK na úspěch nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Popisovač a DWORD/ukazatel předaný této metodě byly dříve přidružená k tomuto objektu voláním [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Příklad

Následující kód ukazuje jednoduchý provádění `IWorkerThreadClient::Execute`.

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iviewobjecteximpl-class_2.cpp)]

## <a name="see-also"></a>Viz také:

[CComControl – třída](../../atl/reference/ccomcontrol-class.md)<br/>
[Rozhraní – ovládací prvky ActiveX](/windows/desktop/com/activex-controls-interfaces)<br/>
[Kurz](../../atl/active-template-library-atl-tutorial.md)<br/>
[Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)<br/>
[Přehled tříd](../../atl/atl-class-overview.md)
