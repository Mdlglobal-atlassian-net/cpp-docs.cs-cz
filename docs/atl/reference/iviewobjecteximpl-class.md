---
title: IViewObjectExImpl – třída
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
ms.openlocfilehash: 3aead41f317d175eac9dcb094aa2070d82dc6185
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69495493"
---
# <a name="iviewobjecteximpl-class"></a>IViewObjectExImpl – třída

Tato třída implementuje `IUnknown` a poskytuje výchozí implementace rozhraní [IViewObject](/windows/win32/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)a [IViewObjectEx](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex) .

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class ATL_NO_VTABLE IViewObjectExImpl
   : public IViewObjectEx
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, která je `IViewObjectExImpl`odvozena z.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[IViewObjectExImpl: nezpracované:D](#draw)|Nakreslí reprezentace ovládacího prvku do kontextu zařízení.|
|[IViewObjectExImpl:: zmrazit](#freeze)|Zablokuje vykreslenou reprezentaci ovládacího prvku tak, aby se nezměnila do `Unfreeze`. Implementace ATL Vrátí E_NOTIMPL.|
|[IViewObjectExImpl::GetAdvise](#getadvise)|Načte existující připojení informační jímky na ovládacím prvku, pokud existuje.|
|[IViewObjectExImpl::GetColorSet](#getcolorset)|Vrátí logickou paletu používanou ovládacím prvkem pro kreslení. Implementace ATL Vrátí E_NOTIMPL.|
|[IViewObjectExImpl:: getrozsah](#getextent)|Načte velikost zobrazení ovládacího prvku v jednotkách HIMETRIC (0,01 milimetr na jednotku) z datového členu třídy ovládacího prvku [CComControlBase:: m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).|
|[IViewObjectExImpl::GetNaturalExtent](#getnaturalextent)|Poskytuje tipy pro změnu velikosti z kontejneru pro objekt, který se má použít, když uživatel změní jeho velikost.|
|[IViewObjectExImpl::GetRect](#getrect)|Vrátí obdélník popisující požadovaný aspekt kreslení. Implementace ATL Vrátí E_NOTIMPL.|
|[IViewObjectExImpl::GetViewStatus](#getviewstatus)|Vrátí informace o neprůhlednosti objektu a o tom, jaké aspekty vykreslování jsou podporovány.|
|[IViewObjectExImpl::QueryHitPoint](#queryhitpoint)|Zkontroluje, zda je zadaný bod v zadaném obdélníku a vrátí hodnotu [HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult) v `pHitResult`.|
|[IViewObjectExImpl::QueryHitRect](#queryhitrect)|Kontroluje, zda se obdélník zobrazení ovládacího prvku překrývá s jakýmkoli bodem v zadaném obdélníku umístění a vrátí hodnotu HITRESULT `pHitResult`v.|
|[IViewObjectExImpl::SetAdvise](#setadvise)|Nastaví připojení mezi ovládacím prvkem a jímkou příplatku, aby mohla být jímka upozorněna na změny v zobrazení ovládacího prvku.|
|[IViewObjectExImpl:: unzmrazit](#unfreeze)|Uvolní vykreslenou reprezentaci ovládacího prvku. Implementace ATL Vrátí E_NOTIMPL.|

## <a name="remarks"></a>Poznámky

Rozhraní [IViewObject](/windows/win32/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)a [IViewObjectEx](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex) umožňují ovládacím prvkům, aby se zobrazily přímo, a vytvořila a spravovala jímka Advise, která upozorní kontejner na změny v zobrazení ovládacího prvku. `IViewObjectEx` Rozhraní poskytuje podporu pro rozšířené funkce ovládacího prvku, jako je například kreslení bez blikání, nepravoúhlé a transparentní ovládací prvky, a testování volání (například způsob, jakým je nutné, aby se na ovládacím prvku mohl považovat kliknutí myší zavřít). Třída `IViewObjectExImpl` poskytuje výchozí implementaci těchto rozhraní a implementuje `IUnknown` odesláním informací do zařízení výpisu paměti v sestaveních pro ladění.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IViewObjectEx`

`IViewObjectExImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl. h

##  <a name="draw"></a>IViewObjectExImpl: nezpracované:D

Nakreslí reprezentace ovládacího prvku do kontextu zařízení.

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

Tato metoda volá `CComControl::OnDrawAdvanced` , která zase volá `OnDraw` metodu vaší třídy ovládacího prvku. `OnDraw` Metoda je automaticky přidána do vaší třídy ovládacího prvku při vytvoření ovládacího prvku pomocí Průvodce ovládacím prvkem ATL. Výchozí hodnota `OnDraw` Průvodce nakreslí obdélník s popiskem ATL 3,0.

Viz [IViewObject::D RAW](/windows/win32/api/oleidl/nf-oleidl-iviewobject-draw) v Windows SDK.

##  <a name="freeze"></a>IViewObjectExImpl:: zmrazit

Zablokuje vykreslenou reprezentaci ovládacího prvku tak, aby se nezměnila do `Unfreeze`. Implementace ATL Vrátí E_NOTIMPL.

```
STDMETHOD(Freeze)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DWORD* /* pdwFreeze */);
```

### <a name="remarks"></a>Poznámky

Viz [IViewObject:: zmrazit](/windows/win32/api/oleidl/nf-oleidl-iviewobject-freeze) ve Windows SDK.

##  <a name="getadvise"></a>IViewObjectExImpl:: GetAdvise

Načte existující připojení informační jímky na ovládacím prvku, pokud existuje.

```
STDMETHOD(GetAdvise)(
    DWORD* /* pAspects */,
    DWORD* /* pAdvf */,
    IAdviseSink** /* ppAdvSink */);
```

### <a name="remarks"></a>Poznámky

Informační jímka je uložena v datovém členu třídy ovládacího prvku [CComControlBase:: m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink).

Viz [IViewObject:: GetAdvise](/windows/win32/api/oleidl/nf-oleidl-iviewobject-getadvise) v Windows SDK.

##  <a name="getcolorset"></a>IViewObjectExImpl::GetColorSet

Vrátí logickou paletu používanou ovládacím prvkem pro kreslení. Implementace ATL Vrátí E_NOTIMPL.

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

Viz [IViewObject:: GetColorSet](/windows/win32/api/oleidl/nf-oleidl-iviewobject-getcolorset) v Windows SDK.

##  <a name="getextent"></a>IViewObjectExImpl:: getrozsah

Načte velikost zobrazení ovládacího prvku v jednotkách HIMETRIC (0,01 milimetr na jednotku) z datového členu třídy ovládacího prvku [CComControlBase:: m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).

```
STDMETHOD(GetExtent)(
    DWORD /* dwDrawAspect */,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    LPSIZEL* lpsizel);
```

### <a name="remarks"></a>Poznámky

Viz [IViewObject2:: getrozsah](/windows/win32/api/oleidl/nf-oleidl-iviewobject2-getextent) v Windows SDK.

##  <a name="getnaturalextent"></a>IViewObjectExImpl::GetNaturalExtent

Poskytuje tipy pro změnu velikosti z kontejneru pro objekt, který se má použít, když uživatel změní jeho velikost.

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

Pokud `dwAspect` je DVASPECT_CONTENT a *pExtentInfo-> dwExtentMode* je DVEXTENT_CONTENT, nastaví * `psizel` na datový člen třídy ovládacího prvku [CComControlBase:: m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural). V opačném případě vrátí chybu HRESULT.

Viz [IViewObjectEx:: GetNaturalExtent](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getnaturalextent) v Windows SDK.

##  <a name="getrect"></a>IViewObjectExImpl:: GetRect

Vrátí obdélník popisující požadovaný aspekt kreslení. Implementace ATL Vrátí E_NOTIMPL.

```
STDMETHOD(GetRect)(DWORD /* dwAspect */, LPRECTL /* pRect */);
```

### <a name="remarks"></a>Poznámky

Viz [IViewObjectEx:: GetRect](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getrect) v Windows SDK.

##  <a name="getviewstatus"></a>IViewObjectExImpl::GetViewStatus

Vrátí informace o neprůhlednosti objektu a o tom, jaké aspekty vykreslování jsou podporovány.

```
STDMETHOD(GetViewStatus)(DWORD* pdwStatus);
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení sada ATL `pdwStatus` nastaví, aby označovala, že ovládací prvek podporuje VIEWSTATUS_OPAQUE (možné hodnoty jsou ve výčtu [VIEWSTATUS](/windows/win32/api/ocidl/ne-ocidl-viewstatus) ).

Viz [IViewObjectEx:: GetViewStatus](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getviewstatus) v Windows SDK.

##  <a name="queryhitpoint"></a>  IViewObjectExImpl::QueryHitPoint

Zkontroluje, zda je zadaný bod v zadaném obdélníku a vrátí hodnotu [HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult) v `pHitResult`.

```
STDMETHOD(QueryHitPoint)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    POINT ptlLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```

### <a name="remarks"></a>Poznámky

Hodnota může být buď HITRESULT_HIT, nebo HITRESULT_OUTSIDE.

Pokud `dwAspect` se rovná [DVASPECT_CONTENT](/windows/win32/api/wtypes/ne-wtypes-dvaspect), metoda vrátí hodnotu S_OK. V opačném případě vrátí metoda E_FAIL.

Viz [IViewObjectEx:: QueryHitPoint](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-queryhitpoint) v Windows SDK.

##  <a name="queryhitrect"></a>  IViewObjectExImpl::QueryHitRect

Kontroluje, zda se obdélník zobrazení ovládacího prvku překrývá s jakýmkoli bodem v zadaném obdélníku umístění a [](/windows/win32/api/ocidl/ne-ocidl-hitresult) vrátí hodnotu HITRESULT `pHitResult`v.

```
STDMETHOD(QueryHitRect)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    LPRECT prcLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```

### <a name="remarks"></a>Poznámky

Hodnota může být buď HITRESULT_HIT, nebo HITRESULT_OUTSIDE.

Pokud `dwAspect` se rovná [DVASPECT_CONTENT](/windows/win32/api/wtypes/ne-wtypes-dvaspect), metoda vrátí hodnotu S_OK. V opačném případě vrátí metoda E_FAIL.

Viz [IViewObjectEx:: QueryHitRect](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-queryhitrect) v Windows SDK.

##  <a name="setadvise"></a>IViewObjectExImpl::SetAdvise

Nastaví připojení mezi ovládacím prvkem a jímkou příplatku, aby mohla být jímka upozorněna na změny v zobrazení ovládacího prvku.

```
STDMETHOD(SetAdvise)(
    DWORD /* aspects */,
    DWORD /* advf */,
    IAdviseSink* pAdvSink);
```

### <a name="remarks"></a>Poznámky

Ukazatel na rozhraní [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink) v jímky příjímka je uložen v datovém členu třídy ovládacího prvku [CComControlBase:: m_spAdviseSink](ccomcontrolbase-class.md#m_spadvisesink).

Viz [IViewObject:: SetAdvise](/windows/win32/api/oleidl/nf-oleidl-iviewobject-setadvise) v Windows SDK.

##  <a name="unfreeze"></a>IViewObjectExImpl:: unzmrazit

Uvolní vykreslenou reprezentaci ovládacího prvku. Implementace ATL Vrátí E_NOTIMPL.

```
STDMETHOD(Unfreeze)(DWORD /* dwFreeze */);
```

### <a name="remarks"></a>Poznámky

Viz [IViewObject::](/windows/win32/api/oleidl/nf-oleidl-iviewobject-unfreeze) dismraze v Windows SDK.

##  <a name="closehandle"></a>IWorkerThreadClient:: CloseHandle

Implementací této metody uzavřete popisovač přidružený k tomuto objektu.

```
HRESULT CloseHandle(HANDLE hHandle);
```

### <a name="parameters"></a>Parametry

*hHandle*<br/>
Popisovač, který má být zavřen.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Popisovač předaný této metodě byl dříve přidružen k tomuto objektu voláním metody [CWorkerThread:: AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Příklad

Následující kód ukazuje jednoduchou implementaci `IWorkerThreadClient::CloseHandle`nástroje.

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iviewobjecteximpl-class_1.cpp)]

##  <a name="execute"></a>IWorkerThreadClient:: Execute

Implementujte tuto metodu pro spuštění kódu, když se popisovač přidružený k tomuto objektu zasignalizuje.

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>Parametry

*dwParam*<br/>
Parametr uživatele

*hObject*<br/>
Popisovač, u kterého se stala signál.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu S_OK při úspěchu nebo chybu HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Popisovač a DWORD/ukazatel předaný této metodě byly dříve přidruženy k tomuto objektu voláním metody [CWorkerThread:: AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Příklad

Následující kód ukazuje jednoduchou implementaci `IWorkerThreadClient::Execute`nástroje.

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iviewobjecteximpl-class_2.cpp)]

## <a name="see-also"></a>Viz také:

[CComControl – třída](../../atl/reference/ccomcontrol-class.md)<br/>
[Rozhraní ovládacích prvků ActiveX](/windows/win32/com/activex-controls-interfaces)<br/>
[Kurz](../../atl/active-template-library-atl-tutorial.md)<br/>
[Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
