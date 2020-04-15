---
title: Třída IViewObjectEximpl
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
ms.openlocfilehash: 59c5657dcd892544f7e790b52325cb9ecba0dd56
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326345"
---
# <a name="iviewobjecteximpl-class"></a>Třída IViewObjectEximpl

Tato třída `IUnknown` implementuje a poskytuje výchozí implementace rozhraní [IViewObject](/windows/win32/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)a [IViewObjectEx.](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex)

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template<class T>
class ATL_NO_VTABLE IViewObjectExImpl
   : public IViewObjectEx
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Vaše třída, odvozená z `IViewObjectExImpl`.

## <a name="members"></a>Členové

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[IViewObjectExImpl::Draw](#draw)|Nakreslí reprezentaci ovládacího prvku do kontextu zařízení.|
|[IViewObjectEximpl::Zmrazit](#freeze)|Zamrzne vykreslenou reprezentaci ovládacího prvku, takže se nezmění, dokud . `Unfreeze` Implementace ATL vrátí E_NOTIMPL.|
|[iViewObjecteximpl::GetAdvise](#getadvise)|Načte existující připojení jímky informační ho dřezu na ovládací prvek, pokud existuje.|
|[iViewObjectEximpl::GetColorSet](#getcolorset)|Vrátí logickou paletu používanou ovládacím prvkem pro kreslení. Implementace ATL vrátí E_NOTIMPL.|
|[IViewObjectEximpl::GetExtent](#getextent)|Načte velikost zobrazení ovládacího prvku v jednotkách HIMETRIC (0,01 milimetru na jednotku) z datového člena třídy řízení [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).|
|[iViewObjecteximpl::GetNaturalExtent](#getnaturalextent)|Poskytuje rady pro změny velikosti z kontejneru pro objekt použít jako uživatel změní jeho velikost.|
|[IViewObjectExImpl::GetRect](#getrect)|Vrátí obdélník popisující aspekt požadovaného výkresu. Implementace ATL vrátí E_NOTIMPL.|
|[iViewObjecteximpl::GetViewStatus](#getviewstatus)|Vrátí informace o krytí objektu a o tom, jaké aspekty kreslení jsou podporovány.|
|[iViewObjecteximpl::QueryHitPoint](#queryhitpoint)|Zkontroluje, zda je zadaný bod v zadaném `pHitResult`obdélníku, a vrátí hodnotu [HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult) v .|
|[IViewObjectExImpl::QueryHitRect](#queryhitrect)|Zkontroluje, zda obdélník zobrazení ovládacího prvku překrývá libovolný bod `pHitResult`v zadaném obdélníku umístění, a vrátí hodnotu HITRESULT v .|
|[iViewObjecteximpl::SetAdvise](#setadvise)|Nastaví připojení mezi ovládacím prvkem a jímkou doporučení, aby jímka mohla být upozorňována na změny v zobrazení ovládacího prvku.|
|[IViewObjectExImpl::Uvolnit](#unfreeze)|Rozmrazí nakreslené reprezentace ovládacího prvku. Implementace ATL vrátí E_NOTIMPL.|

## <a name="remarks"></a>Poznámky

[Rozhraní IViewObject](/windows/win32/api/oleidl/nn-oleidl-iviewobject), [IViewObject2](/windows/win32/api/oleidl/nn-oleidl-iviewobject2)a [IViewObjectEx](/windows/win32/api/ocidl/nn-ocidl-iviewobjectex) umožňují ovládacímu prvku zobrazit přímo a vytvořit a spravovat jímku doporučení, které upozorní kontejner na změny v ovládacím panelu. Rozhraní `IViewObjectEx` poskytuje podporu pro rozšířené ovládací prvky, jako je kreslení bez blikání, neobdélníkové a průhledné ovládací prvky a testování přístupů (například, jak blízko musí být kliknutí myší, aby bylo považováno za ovládací prvek). Třída `IViewObjectExImpl` poskytuje výchozí implementaci těchto rozhraní `IUnknown` a implementuje odesláním informací do zařízení s výpisem stavu paměti v sestavení ladění.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`IViewObjectEx`

`IViewObjectExImpl`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlctl.h

## <a name="iviewobjecteximpldraw"></a><a name="draw"></a>IViewObjectExImpl::Draw

Nakreslí reprezentaci ovládacího prvku do kontextu zařízení.

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

Tato metoda `CComControl::OnDrawAdvanced` volá, která zase volá `OnDraw` metodu třídy ovládacího prvku. Metoda `OnDraw` je automaticky přidána do třídy ovládacího prvku při vytváření ovládacího prvku pomocí Průvodce řízením ATL. Výchozí `OnDraw` nastavení průvodce nakreslí obdélník s popiskem "ATL 3.0".

Viz [IViewObject::Draw](/windows/win32/api/oleidl/nf-oleidl-iviewobject-draw) v sadě Windows SDK.

## <a name="iviewobjecteximplfreeze"></a><a name="freeze"></a>IViewObjectEximpl::Zmrazit

Zamrzne vykreslenou reprezentaci ovládacího prvku, takže se nezmění, dokud . `Unfreeze` Implementace ATL vrátí E_NOTIMPL.

```
STDMETHOD(Freeze)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DWORD* /* pdwFreeze */);
```

### <a name="remarks"></a>Poznámky

Viz [IViewObject::Freeze](/windows/win32/api/oleidl/nf-oleidl-iviewobject-freeze) v sadě Windows SDK.

## <a name="iviewobjecteximplgetadvise"></a><a name="getadvise"></a>iViewObjecteximpl::GetAdvise

Načte existující připojení jímky informační ho dřezu na ovládací prvek, pokud existuje.

```
STDMETHOD(GetAdvise)(
    DWORD* /* pAspects */,
    DWORD* /* pAdvf */,
    IAdviseSink** /* ppAdvSink */);
```

### <a name="remarks"></a>Poznámky

Jímka informačních zpravodajů je uložena v datovém členu třídy řízení [CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink).

Viz [IViewObject::GetAdvise](/windows/win32/api/oleidl/nf-oleidl-iviewobject-getadvise) v sadě Windows SDK.

## <a name="iviewobjecteximplgetcolorset"></a><a name="getcolorset"></a>iViewObjectEximpl::GetColorSet

Vrátí logickou paletu používanou ovládacím prvkem pro kreslení. Implementace ATL vrátí E_NOTIMPL.

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

Viz [IViewObject::GetColorSet](/windows/win32/api/oleidl/nf-oleidl-iviewobject-getcolorset) v sadě Windows SDK.

## <a name="iviewobjecteximplgetextent"></a><a name="getextent"></a>IViewObjectEximpl::GetExtent

Načte velikost zobrazení ovládacího prvku v jednotkách HIMETRIC (0,01 milimetru na jednotku) z datového člena třídy řízení [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).

```
STDMETHOD(GetExtent)(
    DWORD /* dwDrawAspect */,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    LPSIZEL* lpsizel);
```

### <a name="remarks"></a>Poznámky

Viz [IViewObject2::GetExtent](/windows/win32/api/oleidl/nf-oleidl-iviewobject2-getextent) v sadě Windows SDK.

## <a name="iviewobjecteximplgetnaturalextent"></a><a name="getnaturalextent"></a>iViewObjecteximpl::GetNaturalExtent

Poskytuje rady pro změny velikosti z kontejneru pro objekt použít jako uživatel změní jeho velikost.

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

Pokud `dwAspect` je DVASPECT_CONTENT a *pExtentInfo->dwExtentMode* je DVEXTENT_CONTENT, nastaví * `psizel` na datovém členu třídy ovládacího prvku [CComControlBase::m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural). V opačném případě vrátí chybu HRESULT.

Viz [IViewObjectEx::GetNaturalExtent](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getnaturalextent) v sadě Windows SDK.

## <a name="iviewobjecteximplgetrect"></a><a name="getrect"></a>IViewObjectExImpl::GetRect

Vrátí obdélník popisující aspekt požadovaného výkresu. Implementace ATL vrátí E_NOTIMPL.

```
STDMETHOD(GetRect)(DWORD /* dwAspect */, LPRECTL /* pRect */);
```

### <a name="remarks"></a>Poznámky

Viz [IViewObjectEx::GetRect](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getrect) v sadě Windows SDK.

## <a name="iviewobjecteximplgetviewstatus"></a><a name="getviewstatus"></a>iViewObjecteximpl::GetViewStatus

Vrátí informace o krytí objektu a o tom, jaké aspekty kreslení jsou podporovány.

```
STDMETHOD(GetViewStatus)(DWORD* pdwStatus);
```

### <a name="remarks"></a>Poznámky

Ve výchozím nastavení `pdwStatus` se hodnota ATL nastaví tak, aby označovala, že ovládací prvek podporuje VIEWSTATUS_OPAQUE (možné hodnoty jsou ve výčtu [VIEWSTATUS).](/windows/win32/api/ocidl/ne-ocidl-viewstatus)

Viz [IViewObjectEx::GetViewStatus](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-getviewstatus) v sadě Windows SDK.

## <a name="iviewobjecteximplqueryhitpoint"></a><a name="queryhitpoint"></a>iViewObjecteximpl::QueryHitPoint

Zkontroluje, zda je zadaný bod v zadaném `pHitResult`obdélníku, a vrátí hodnotu [HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult) v .

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

Pokud `dwAspect` se rovná [DVASPECT_CONTENT](/windows/win32/api/wtypes/ne-wtypes-dvaspect), metoda vrátí S_OK. V opačném případě vrátí metoda E_FAIL.

Viz [IViewObjectEx::QueryHitPoint](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-queryhitpoint) v sadě Windows SDK.

## <a name="iviewobjecteximplqueryhitrect"></a><a name="queryhitrect"></a>IViewObjectExImpl::QueryHitRect

Zkontroluje, zda obdélník zobrazení ovládacího prvku překrývá libovolný bod `pHitResult`v zadaném obdélníku umístění, a vrátí hodnotu [HITRESULT](/windows/win32/api/ocidl/ne-ocidl-hitresult) v .

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

Pokud `dwAspect` se rovná [DVASPECT_CONTENT](/windows/win32/api/wtypes/ne-wtypes-dvaspect), metoda vrátí S_OK. V opačném případě vrátí metoda E_FAIL.

Viz [IViewObjectEx::QueryHitRect](/windows/win32/api/ocidl/nf-ocidl-iviewobjectex-queryhitrect) v sadě Windows SDK.

## <a name="iviewobjecteximplsetadvise"></a><a name="setadvise"></a>iViewObjecteximpl::SetAdvise

Nastaví připojení mezi ovládacím prvkem a jímkou doporučení, aby jímka mohla být upozorňována na změny v zobrazení ovládacího prvku.

```
STDMETHOD(SetAdvise)(
    DWORD /* aspects */,
    DWORD /* advf */,
    IAdviseSink* pAdvSink);
```

### <a name="remarks"></a>Poznámky

Ukazatel na rozhraní [IAdviseSink](/windows/win32/api/objidl/nn-objidl-iadvisesink) na jímce advise je uložen v datovém členu třídy ovládacího prvku [CComControlBase::m_spAdviseSink](ccomcontrolbase-class.md#m_spadvisesink).

Viz [IViewObject::SetAdvise](/windows/win32/api/oleidl/nf-oleidl-iviewobject-setadvise) v sadě Windows SDK.

## <a name="iviewobjecteximplunfreeze"></a><a name="unfreeze"></a>IViewObjectExImpl::Uvolnit

Rozmrazí nakreslené reprezentace ovládacího prvku. Implementace ATL vrátí E_NOTIMPL.

```
STDMETHOD(Unfreeze)(DWORD /* dwFreeze */);
```

### <a name="remarks"></a>Poznámky

Viz [IViewObject::Unfreeze](/windows/win32/api/oleidl/nf-oleidl-iviewobject-unfreeze) v sadě Windows SDK.

## <a name="iworkerthreadclientclosehandle"></a><a name="closehandle"></a>IWorkerThreadClient::CloseHandle

Implementujte tuto metodu k uzavření popisovače přidruženého k tomuto objektu.

```
HRESULT CloseHandle(HANDLE hHandle);
```

### <a name="parameters"></a>Parametry

*hHandle*<br/>
Rukojeť, která má být uzavřena.

### <a name="return-value"></a>Návratová hodnota

Vrátit S_OK na úspěch nebo chyba HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Popisovač předaný této metodě byl dříve přidružen k tomuto objektu voláním [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Příklad

Následující kód ukazuje jednoduchou `IWorkerThreadClient::CloseHandle`implementaci .

[!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iviewobjecteximpl-class_1.cpp)]

## <a name="iworkerthreadclientexecute"></a><a name="execute"></a>IWorkerThreadClient::Spustit

Implementujte tuto metodu ke spuštění kódu, když popisovač přidružený k tomuto objektu se stane signalizován.

```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```

### <a name="parameters"></a>Parametry

*dwParam*<br/>
Parametr uživatele.

*hObjekt*<br/>
Rukojeť, která se stala signalizována.

### <a name="return-value"></a>Návratová hodnota

Vrátit S_OK na úspěch nebo chyba HRESULT při selhání.

### <a name="remarks"></a>Poznámky

Popisovač a DWORD/pointer předané této metodě byly dříve přidruženy k tomuto objektu voláním [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).

### <a name="example"></a>Příklad

Následující kód ukazuje jednoduchou `IWorkerThreadClient::Execute`implementaci .

[!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iviewobjecteximpl-class_2.cpp)]

## <a name="see-also"></a>Viz také

[Třída CComControl](../../atl/reference/ccomcontrol-class.md)<br/>
[Rozhraní ovládacích prvků ActiveX](/windows/win32/com/activex-controls-interfaces)<br/>
[Tutorial](../../atl/active-template-library-atl-tutorial.md)<br/>
[Vytvoření projektu ATL](../../atl/reference/creating-an-atl-project.md)<br/>
[Přehled třídy](../../atl/atl-class-overview.md)
