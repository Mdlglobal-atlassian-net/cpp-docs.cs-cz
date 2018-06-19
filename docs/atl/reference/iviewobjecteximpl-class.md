---
title: Třída IViewObjectExImpl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- ActiveX controls [C++], drawing
- IViewObjectEx ATL implementation
- advise sinks
- IViewObjectExImpl class
ms.assetid: ad6de760-1ee5-4883-b033-ae57beffc369
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c51bc9e5feb02d837c37341b82a1fc19a3cea558
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32365908"
---
# <a name="iviewobjecteximpl-class"></a>IViewObjectExImpl – třída
Tato třída implementuje **IUnknown** a poskytuje výchozí implementaci [IViewObject](http://msdn.microsoft.com/library/windows/desktop/ms680763), [IViewObject2](http://msdn.microsoft.com/library/windows/desktop/ms691318), a [IViewObjectEx](http://msdn.microsoft.com/library/windows/desktop/ms682375)rozhraní.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T>  
class ATL_NO_VTABLE IViewObjectExImpl 
   : public IViewObjectEx
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Vlastní třídy odvozené od `IViewObjectExImpl`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IViewObjectExImpl::Draw](#draw)|Nakreslí znázornění ovládacího prvku do kontextu zařízení.|  
|[IViewObjectExImpl::Freeze](#freeze)|Tak se nezmění, dokud se zablokuje vykresleného reprezentace ovládacího prvku `Unfreeze`. Implementace ATL vrátí **E_NOTIMPL**.|  
|[IViewObjectExImpl::GetAdvise](#getadvise)|Načte stávající poradní podřízený připojení k řízení, pokud existuje.|  
|[IViewObjectExImpl::GetColorSet](#getcolorset)|Vrátí logickou palety používá pro vykreslování ovládacího prvku. Implementace ATL vrátí **E_NOTIMPL**.|  
|[IViewObjectExImpl::GetExtent](#getextent)|Načte velikost zobrazení ovládacího prvku v jednotkách HIMETRIC (0,01 milimetru na jednotku) z datový člen třídy ovládacího prvku [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).|  
|[IViewObjectExImpl::GetNaturalExtent](#getnaturalextent)|Poskytuje pomocné parametry velikosti z kontejneru pro objekt, který chcete použít jako uživatel změní jeho velikost.|  
|[IViewObjectExImpl::GetRect](#getrect)|Vrátí obdélníku popisující požadovaný kreslení aspekt. Implementace ATL vrátí **E_NOTIMPL**.|  
|[IViewObjectExImpl::GetViewStatus](#getviewstatus)|Vrací informace o krytí objektu a které kreslení aspekty jsou podporovány.|  
|[IViewObjectExImpl::QueryHitPoint](#queryhitpoint)|Zkontroluje, zda se zadaný bod je v zadané rámeček a vrátí [HITRESULT](http://msdn.microsoft.com/library/windows/desktop/ms682187) hodnotu `pHitResult`.|  
|[IViewObjectExImpl::QueryHitRect](#queryhitrect)|Ověří, zda obdélník zobrazení ovládacího prvku překrývá libovolného bodu v zadaném umístění rámeček a vrátí **HITRESULT** hodnotu `pHitResult`.|  
|[IViewObjectExImpl::SetAdvise](#setadvise)|Nastaví připojení mezi ovládacího prvku a jímky doporučení, jímky můžete oznámení o změnách v zobrazení ovládacího prvku.|  
|[IViewObjectExImpl::Unfreeze](#unfreeze)|Zruší ukotvení vykresleného reprezentace ovládacího prvku. Implementace ATL vrátí **E_NOTIMPL**.|  
  
## <a name="remarks"></a>Poznámky  
 [IViewObject](http://msdn.microsoft.com/library/windows/desktop/ms680763), [IViewObject2](http://msdn.microsoft.com/library/windows/desktop/ms691318), a [IViewObjectEx](http://msdn.microsoft.com/library/windows/desktop/ms682375) rozhraní povolit ovládacího prvku zobrazení samotného přímo a k vytváření a správě jímky doporučení pro upozornění kontejner změny v zobrazení ovládacího prvku. **IViewObjectEx** rozhraní poskytuje podporu pro rozšířené řízení funkcí například blikání kreslení, ovládací prvky obdélníkový a transparentní a stiskněte klávesu testování (například jak zavřít klikněte na tlačítko myši musí být třeba zvažovat řízení). Třída `IViewObjectExImpl` poskytuje výchozí implementaci těchto rozhraní a implementuje **IUnknown** posíláním informací o k výpisu zařízení ladění sestavení.  
  
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
 Tato metoda volá **CComControl::OnDrawAdvanced** který volá třída ovládacích prvků `OnDraw` metoda. `OnDraw` Metody se automaticky přidá do vaší třídy ovládací prvek při vytváření vlastního ovládacího prvku pomocí Průvodce ovládacím prvkem ATL. V Průvodci výchozí `OnDraw` nevykresluje obdélníku s popiskem "ATL 3.0".  
  
 V tématu [IViewObject::Draw](http://msdn.microsoft.com/library/windows/desktop/ms688655) ve Windows SDK.  
  
##  <a name="freeze"></a>  IViewObjectExImpl::Freeze  
 Tak se nezmění, dokud se zablokuje vykresleného reprezentace ovládacího prvku `Unfreeze`. Implementace ATL vrátí **E_NOTIMPL**.  
  
```
STDMETHOD(Freeze)(
    DWORD /* dwAspect */,
    LONG /* lindex */,
    void* /* pvAspect */,
    DWORD* /* pdwFreeze */);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IViewObject::Freeze](http://msdn.microsoft.com/library/windows/desktop/ms688728) ve Windows SDK.  
  
##  <a name="getadvise"></a>  IViewObjectExImpl::GetAdvise  
 Načte stávající poradní podřízený připojení k řízení, pokud existuje.  
  
```
STDMETHOD(GetAdvise)(
    DWORD* /* pAspects */,
    DWORD* /* pAdvf */,
    IAdviseSink** /* ppAdvSink */);
```  
  
### <a name="remarks"></a>Poznámky  
 Poradní jímky je uložen v datový člen třídy ovládacího prvku [CComControlBase::m_spAdviseSink](../../atl/reference/ccomcontrolbase-class.md#m_spadvisesink).  
  
 V tématu [IViewObject::GetAdvise](http://msdn.microsoft.com/library/windows/desktop/ms692772) ve Windows SDK.  
  
##  <a name="getcolorset"></a>  IViewObjectExImpl::GetColorSet  
 Vrátí logickou palety používá pro vykreslování ovládacího prvku. Implementace ATL vrátí **E_NOTIMPL**.  
  
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
 V tématu [IViewObject::GetColorSet](http://msdn.microsoft.com/library/windows/desktop/ms686553) ve Windows SDK.  
  
##  <a name="getextent"></a>  IViewObjectExImpl::GetExtent  
 Načte velikost zobrazení ovládacího prvku v jednotkách HIMETRIC (0,01 milimetru na jednotku) z datový člen třídy ovládacího prvku [CComControlBase::m_sizeExtent](../../atl/reference/ccomcontrolbase-class.md#m_sizeextent).  
  
```
STDMETHOD(GetExtent)(
    DWORD /* dwDrawAspect */,
    LONG /* lindex */,
    DVTARGETDEVICE* /* ptd */,
    LPSIZEL* lpsizel);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IViewObject2::GetExtent](http://msdn.microsoft.com/library/windows/desktop/ms684032) ve Windows SDK.  
  
##  <a name="getnaturalextent"></a>  IViewObjectExImpl::GetNaturalExtent  
 Poskytuje pomocné parametry velikosti z kontejneru pro objekt, který chcete použít jako uživatel změní jeho velikost.  
  
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
 Pokud `dwAspect` je `DVASPECT_CONTENT` a *pExtentInfo -> dwExtentMode* je **DVEXTENT_CONTENT**, nastaví * `psizel` k – datový člen třídy ovládacího prvku [CComControlBase: : m_sizeNatural](../../atl/reference/ccomcontrolbase-class.md#m_sizenatural). Jinak vrátí chybu `HRESULT`.  
  
 V tématu [IViewObjectEx::GetNaturalExtent](http://msdn.microsoft.com/library/windows/desktop/ms683718) ve Windows SDK.  
  
##  <a name="getrect"></a>  IViewObjectExImpl::GetRect  
 Vrátí obdélníku popisující požadovaný kreslení aspekt. Implementace ATL vrátí **E_NOTIMPL**.  
  
```
STDMETHOD(GetRect)(DWORD /* dwAspect */, LPRECTL /* pRect */);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IViewObjectEx::GetRect](http://msdn.microsoft.com/library/windows/desktop/ms695246) ve Windows SDK.  
  
##  <a name="getviewstatus"></a>  IViewObjectExImpl::GetViewStatus  
 Vrací informace o krytí objektu a které kreslení aspekty jsou podporovány.  
  
```
STDMETHOD(GetViewStatus)(DWORD* pdwStatus);
```  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení, nastaví ATL `pdwStatus` k označení, že podporuje ovládací prvek **VIEWSTATUS_OPAQUE** (možné hodnoty jsou v [stavu](http://msdn.microsoft.com/library/windows/desktop/ms687201) výčet).  
  
 V tématu [IViewObjectEx::GetViewStatus](http://msdn.microsoft.com/library/windows/desktop/ms693371) ve Windows SDK.  
  
##  <a name="queryhitpoint"></a>  IViewObjectExImpl::QueryHitPoint  
 Zkontroluje, zda se zadaný bod je v zadané rámeček a vrátí [HITRESULT](http://msdn.microsoft.com/library/windows/desktop/ms682187) hodnotu `pHitResult`.  
  
```
STDMETHOD(QueryHitPoint)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    POINT ptlLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```  
  
### <a name="remarks"></a>Poznámky  
 Hodnota může být buď **HITRESULT_HIT** nebo **HITRESULT_OUTSIDE**.  
  
 Pokud `dwAspect` rovná [DVASPECT_CONTENT](http://msdn.microsoft.com/library/windows/desktop/ms690318), vrátí metoda `S_OK`. Jinak, vrátí metoda **E_FAIL**.  
  
 V tématu [IViewObjectEx::QueryHitPoint](http://msdn.microsoft.com/library/windows/desktop/ms691209) ve Windows SDK.  
  
##  <a name="queryhitrect"></a>  IViewObjectExImpl::QueryHitRect  
 Ověří, zda obdélník zobrazení ovládacího prvku překrývá libovolného bodu v zadaném umístění rámeček a vrátí [HITRESULT](http://msdn.microsoft.com/library/windows/desktop/ms682187) hodnotu `pHitResult`.  
  
```
STDMETHOD(QueryHitRect)(
    DWORD dwAspect,
    LPCRECT pRectBounds,
    LPRECT prcLoc,
    LONG /* lCloseHit */,
    DWORD* /* pHitResult */);
```  
  
### <a name="remarks"></a>Poznámky  
 Hodnota může být buď **HITRESULT_HIT** nebo **HITRESULT_OUTSIDE**.  
  
 Pokud `dwAspect` rovná [DVASPECT_CONTENT](http://msdn.microsoft.com/library/windows/desktop/ms690318), vrátí metoda `S_OK`. Jinak, vrátí metoda **E_FAIL**.  
  
 V tématu [IViewObjectEx::QueryHitRect](http://msdn.microsoft.com/library/windows/desktop/ms693797) ve Windows SDK.  
  
##  <a name="setadvise"></a>  IViewObjectExImpl::SetAdvise  
 Nastaví připojení mezi ovládacího prvku a jímky doporučení, jímky můžete oznámení o změnách v zobrazení ovládacího prvku.  
  
```
STDMETHOD(SetAdvise)(
    DWORD /* aspects */,
    DWORD /* advf */,
    IAdviseSink* pAdvSink);
```  
  
### <a name="remarks"></a>Poznámky  

 Ukazatele myši [IAdviseSink](http://msdn.microsoft.com/library/windows/desktop/ms692513) rozhraní jímce doporučení je uložen v datový člen třídy ovládacího prvku [CComControlBase::m_spAdviseSink](ccomcontrolbase-class.md#m_spadvisesink).  

  
 V tématu [IViewObject::SetAdvise](http://msdn.microsoft.com/library/windows/desktop/ms683950) ve Windows SDK.  
  
##  <a name="unfreeze"></a>  IViewObjectExImpl::Unfreeze  
 Zruší ukotvení vykresleného reprezentace ovládacího prvku. Implementace ATL vrátí **E_NOTIMPL**.  
  
```
STDMETHOD(Unfreeze)(DWORD /* dwFreeze */);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IViewObject::Unfreeze](http://msdn.microsoft.com/library/windows/desktop/ms686641) ve Windows SDK.  
  
##  <a name="closehandle"></a>  IWorkerThreadClient::CloseHandle  
 Implementujte tuto metodu zavřít popisovač přidružené k tomuto objektu.  
  
```
HRESULT CloseHandle(HANDLE hHandle);
```  
  
### <a name="parameters"></a>Parametry  
 *hHandle*  
 Popisovač bude uzavřen.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK na úspěch nebo Chyba HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Popisovač předaná této metodě je dříve spojené s tímto objektem voláním [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).  
  
### <a name="example"></a>Příklad  
 Následující kód ukazuje jednoduchou implementaci `IWorkerThreadClient::CloseHandle`.  
  
 [!code-cpp[NVC_ATL_Utilities#135](../../atl/codesnippet/cpp/iviewobjecteximpl-class_1.cpp)]  
  
##  <a name="execute"></a>  IWorkerThreadClient::Execute  
 Implementujte tuto metodu ke spouštění kódu, když se změní na signál popisovač přidružené k tomuto objektu.  
  
```
HRESULT Execute(DWORD_PTR dwParam, HANDLE hObject);
```  
  
### <a name="parameters"></a>Parametry  
 `dwParam`  
 Tento parametr.  
  
 `hObject`  
 Obslužná rutina, který má být signál.  
  
### <a name="return-value"></a>Návratová hodnota  
 Vrátí S_OK na úspěch nebo Chyba HRESULT při selhání.  
  
### <a name="remarks"></a>Poznámky  
 Popisovač a DWORD/ukazatele předaná této metodě byly dříve přidružená k tomuto objektu voláním [CWorkerThread::AddHandle](../../atl/reference/cworkerthread-class.md#addhandle).  
  
### <a name="example"></a>Příklad  
 Následující kód ukazuje jednoduchou implementaci `IWorkerThreadClient::Execute`.  
  
 [!code-cpp[NVC_ATL_Utilities#136](../../atl/codesnippet/cpp/iviewobjecteximpl-class_2.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [CComControl – třída](../../atl/reference/ccomcontrol-class.md)   
 [Rozhraní ovládací prvky ActiveX](http://msdn.microsoft.com/library/windows/desktop/ms692724)   
 [Kurz](../../atl/active-template-library-atl-tutorial.md)   
 [Vytvoření projektu knihovny ATL](../../atl/reference/creating-an-atl-project.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)
