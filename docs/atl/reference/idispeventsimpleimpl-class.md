---
title: Třída IDispEventSimpleImpl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IDispEventSimpleImpl
- ATLCOM/ATL::IDispEventSimpleImpl
- ATLCOM/ATL::IDispEventSimpleImpl::Advise
- ATLCOM/ATL::IDispEventSimpleImpl::DispEventAdvise
- ATLCOM/ATL::IDispEventSimpleImpl::DispEventUnadvise
- ATLCOM/ATL::IDispEventSimpleImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventSimpleImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventSimpleImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventSimpleImpl::Invoke
- ATLCOM/ATL::IDispEventSimpleImpl::Unadvise
dev_langs:
- C++
helpviewer_keywords:
- IDispEventSimpleImpl class
ms.assetid: 971d82b7-a921-47fa-a4d8-909bed377ab0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 89f565c1e32f1208fbb039321d26b9175596d57e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="idispeventsimpleimpl-class"></a>IDispEventSimpleImpl – třída
Tato třída poskytuje implementace `IDispatch` metody bez získávání informací o typu z knihovny typů.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <UINT nID, class T, const IID* pdiid>  
class ATL_NO_VTABLE IDispEventSimpleImpl : public _IDispEventLocator<nID, pdiid>
```    
  
#### <a name="parameters"></a>Parametry  
 `nID`  
 Jedinečný identifikátor pro zdrojový objekt. Když `IDispEventSimpleImpl` je základní třídou pro složeného ovládacího prvku, použijte ID prostředku požadované obsažené ovládací prvek pro tento parametr. V ostatních případech použijte libovolné kladné celé číslo.  
  
 `T`  
 Třída uživatele, který je odvozený od `IDispEventSimpleImpl`.  
  
 `pdiid`  
 Ukazatel na identifikátory IID dispinterface událostí implementována touto třídou.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IDispEventSimpleImpl::Advise](#advise)|Naváže připojení se výchozí zdroj události.|  
|[IDispEventSimpleImpl::DispEventAdvise](#dispeventadvise)|Naváže připojení se zdroji událostí.|  
|[IDispEventSimpleImpl::DispEventUnadvise](#dispeventunadvise)|Dělí připojení ke zdroji události.|  
|[IDispEventSimpleImpl::GetIDsOfNames](#getidsofnames)|Vrátí **E_NOTIMPL**.|  
|[IDispEventSimpleImpl::GetTypeInfo](#gettypeinfo)|Vrátí **E_NOTIMPL**.|  
|[IDispEventSimpleImpl::GetTypeInfoCount](#gettypeinfocount)|Vrátí **E_NOTIMPL**.|  
|[IDispEventSimpleImpl::Invoke](#invoke)|Mapy jímek uvedené události volání obslužné rutiny událostí.|  
|[IDispEventSimpleImpl::Unadvise](#unadvise)|Dělí připojení ke zdroji událostí výchozí.|  
  
## <a name="remarks"></a>Poznámky  
 `IDispEventSimpleImpl` poskytuje způsob implementace dispinterface události, aniž byste si, jak zadat kód implementace pro každý metoda/událost na tomto rozhraní. `IDispEventSimpleImpl` poskytuje implementaci `IDispatch` metody. Stačí zadat implementace události, které mají být při zpracování.  
  
 `IDispEventSimpleImpl` funguje ve spojení s mapy jímek událostí ve třídě události trasy k funkci příslušnou obslužnou rutinu. K použití této třídy:  
  
-   Přidat [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info) makra mapy jímek událostí pro každou jednotlivou událost na každém objektu, který chcete zpracovávat.  
  
-   Zadejte informace o typu pro každou jednotlivou událost předáním ukazatel na [_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md) struktura jako parametr pro každou položku. Na x86 platformy, `_ATL_FUNC_INFO.cc` hodnota musí být CC_CDECL s voláním metody __stdcall funkce zpětného volání.  
  
-   Volání [DispEventAdvise](#dispeventadvise) k navázání připojení mezi zdrojový objekt a základní třídy.  
  
-   Volání [DispEventUnadvise](#dispeventunadvise) k přerušení připojení.  
  
 Musí být odvozeny od `IDispEventSimpleImpl` (pomocí jedinečnou hodnotu pro `nID`) pro každý objekt, pro kterou je potřeba zpracování událostí. Základní třída můžete znovu použít, unadvising proti jeden zdrojový objekt, který pak radí proti objekt jiný zdroj, ale maximální počet objektů zdroje, které mohou být zpracovány v jednom okamžiku jeden objekt, je omezen počet `IDispEventSimpleImpl` základní třídy.  
  
 **IDispEventSimplImpl** poskytuje stejné funkce jako [IDispEventImpl](../../atl/reference/idispeventimpl-class.md), s výjimkou nedostane typ informace o rozhraní z knihovny typů. Průvodců generování kódu pouze na základě `IDispEventImpl`, ale můžete použít `IDispEventSimpleImpl` přidáním kód ručně. Použití `IDispEventSimpleImpl` když nemáte knihovny typů popisující rozhraní události nebo chtít vyhnout režie spojená s použitím knihovny typů.  
  
> [!NOTE]
> `IDispEventImpl` a `IDispEventSimpleImpl` zadejte vlastní implementaci **IUnknown::QueryInterface** povolení jednotlivých `IDispEventImpl` nebo `IDispEventSimpleImpl` základní třída tak, aby fungoval jako samostatné identity COM zároveň umožňuje přímý přístup ke členům třídy v hlavní objektu COM.  
  
 Implementace CE ATL ActiveX událostí jímky pouze podporuje návratové hodnoty typu HRESULT nebo void z vaší metody obslužná rutina události; všechny ostatní návratové hodnoty není podporován a jeho chování není definováno.  
  
 Další informace najdete v tématu [podpora IDispEventImpl](../../atl/supporting-idispeventimpl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `_IDispEvent`  
  
 `_IDispEventLocator`  
  
 `IDispEventSimpleImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="advise"></a>  IDispEventSimpleImpl::Advise  
 Voláním této metody lze navázat připojení ke zdroji události, která je reprezentována *pUnk*.  
  
```
HRESULT Advise(IUnknown* pUnk);
```  
  
### <a name="parameters"></a>Parametry  
 *pUnk*  
 [v] Ukazatel **IUnknown** rozhraní objektu zdroje událostí.  
  
### <a name="return-value"></a>Návratová hodnota  
 `S_OK` nebo jakákoli chyba `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Po vytvoření připojení k vyvolání událostí z *pUnk* budou směrovány do obslužné rutiny v třídě prostřednictvím mapy jímek událostí.  
  
> [!NOTE]
>  Pokud vaše třída odvozena z několika `IDispEventSimpleImpl` třídy, budete muset odstranit nejednoznačnost volání této metody podle rozsahu volání s určité základní třídy vás zajímá.  
  
 `Advise` Vytvoří připojení ke zdroji události výchozí získává identifikátory IID výchozí zdroj události objektu určeného [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).  
  
##  <a name="dispeventadvise"></a>  IDispEventSimpleImpl::DispEventAdvise  
 Voláním této metody lze navázat připojení ke zdroji události, která je reprezentována *pUnk*.  
  
```
HRESULT DispEventAdvise(IUnknown* pUnk  const IID* piid);
```  
  
### <a name="parameters"></a>Parametry  
 *pUnk*  
 [v] Ukazatel **IUnknown** rozhraní objektu zdroje událostí.  
  
 `piid`  
 Ukazatel na identifikátory IID objektu zdroje událostí.  
  
### <a name="return-value"></a>Návratová hodnota  
 `S_OK` nebo jakákoli chyba `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Následně vyvolání událostí z *pUnk* budou směrovány do obslužné rutiny v třídě prostřednictvím mapy jímek událostí.  
  
> [!NOTE]
>  Pokud vaše třída odvozena z několika `IDispEventSimpleImpl` třídy, budete muset odstranit nejednoznačnost volání této metody podle rozsahu volání s určité základní třídy vás zajímá.  
  
 `DispEventAdvise` Vytvoří připojení ke zdroji události zadaný v `pdiid`.  
  
##  <a name="dispeventunadvise"></a>  IDispEventSimpleImpl::DispEventUnadvise  
 Dělí připojení ke zdroji události, která je reprezentována *pUnk*.  
  
```
HRESULT DispEventUnadvise(IUnknown* pUnk  const IID* piid);
```  
  
### <a name="parameters"></a>Parametry  
 *pUnk*  
 [v] Ukazatel **IUnknown** rozhraní objektu zdroje událostí.  
  
 `piid`  
 Ukazatel na identifikátory IID objektu zdroje událostí.  
  
### <a name="return-value"></a>Návratová hodnota  
 `S_OK` nebo jakákoli chyba `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Po připojení je přerušené, události již nebudou směrovány k funkcím obslužných rutin, které jsou uvedené v mapy jímek událostí.  
  
> [!NOTE]
>  Pokud vaše třída odvozena z několika `IDispEventSimpleImpl` třídy, budete muset odstranit nejednoznačnost volání této metody podle rozsahu volání s určité základní třídy vás zajímá.  
  
 `DispEventAdvise` dělí připojení, který byl vytvořen s zdroj událostí uvedený v `pdiid`.  
  
##  <a name="getidsofnames"></a>  IDispEventSimpleImpl::GetIDsOfNames  
 Tato implementace **funkce IDispatch::GetIDsOfNames** vrátí **E_NOTIMPL**.  
  
```
STDMETHOD(GetIDsOfNames)(
    REFIID /* riid */,
    LPOLESTR* /* rgszNames */,
    UINT /* cNames */,
    LCID /* lcid */,
    DISPID* /* rgdispid */);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [funkce IDispatch::GetIDsOfNames](http://msdn.microsoft.com/en-us/6f6cf233-3481-436e-8d6a-51f93bf91619) ve Windows SDK.  
  
##  <a name="gettypeinfo"></a>  IDispEventSimpleImpl::GetTypeInfo  
 Tato implementace **IDispatch::GetTypeInfo** vrátí **E_NOTIMPL**.  
  
```
STDMETHOD(GetTypeInfo)(
    UINT /* itinfo */,
    LCID /* lcid */,
    ITypeInfo** /* pptinfo */);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IDispatch::GetTypeInfo](http://msdn.microsoft.com/en-us/cc1ec9aa-6c40-4e70-819c-a7c6dd6b8c99) ve Windows SDK.  
  
##  <a name="gettypeinfocount"></a>  IDispEventSimpleImpl::GetTypeInfoCount  
 Tato implementace **IDispatch::GetTypeInfoCount** vrátí **E_NOTIMPL**.  
  
```
STDMETHOD(GetTypeInfoCount)(UINT* /* pctinfo */);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IDispatch::GetTypeInfoCount](http://msdn.microsoft.com/en-us/da876d53-cb8a-465c-a43e-c0eb272e2a12) ve Windows SDK.  
  
##  <a name="invoke"></a>  IDispEventSimpleImpl::Invoke  
 Tato implementace **volání metody IDispatch::Invoke** volání obslužné rutiny událostí uvedené události podřízený mapy.  
  
```
STDMETHOD(Invoke)(
    DISPID dispidMember,
    REFIID /* riid */,
    LCID lcid,
    WORD /* wFlags */,
    DISPPARMS* pdispparams,
    VARIANT* pvarResult,
    EXCEPINFO* /* pexcepinfo */,
    UINT* /* puArgErr */);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [volání metody IDispatch::Invoke](http://msdn.microsoft.com/en-us/964ade8e-9d8a-4d32-bd47-aa678912a54d).  
  
##  <a name="unadvise"></a>  IDispEventSimpleImpl::Unadvise  
 Dělí připojení ke zdroji události, která je reprezentována *pUnk*.  
  
```
HRESULT Unadvise(IUnknown* pUnk);
```  
  
### <a name="parameters"></a>Parametry  
 *pUnk*  
 [v] Ukazatel **IUnknown** rozhraní objektu zdroje událostí.  
  
### <a name="return-value"></a>Návratová hodnota  
 `S_OK` nebo jakákoli chyba `HRESULT` hodnotu.  
  
### <a name="remarks"></a>Poznámky  
 Po připojení je přerušené, události již nebudou směrovány k funkcím obslužných rutin, které jsou uvedené v mapy jímek událostí.  
  
> [!NOTE]
>  Pokud vaše třída odvozena z několika `IDispEventSimpleImpl` třídy, budete muset odstranit nejednoznačnost volání této metody podle rozsahu volání s určité základní třídy vás zajímá.  
  
 `Unadvise` dělí připojení, který byl vytvořen s je výchozí zdroj událostí uvedený v `pdiid`.  
  
 **Unavise** zalomení připojení ke zdroji události výchozí získává identifikátory IID výchozí zdroj události objektu určeného [AtlGetObjectSourceInterface](composite-control-global-functions.md#atlgetobjectsourceinterface).  
  
## <a name="see-also"></a>Viz také  
 [Struktura _ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)   
 [IDispatchImpl – třída](../../atl/reference/idispatchimpl-class.md)   
 [IDispEventImpl – třída](../../atl/reference/idispeventimpl-class.md)   
 [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)   
 [Přehled třídy](../../atl/atl-class-overview.md)
