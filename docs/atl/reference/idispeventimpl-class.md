---
title: "Třída IDispEventImpl | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- IDispEventImpl
- ATLCOM/ATL::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::IDispEventImpl
- ATLCOM/ATL::IDispEventImpl::GetFuncInfoFromId
- ATLCOM/ATL::IDispEventImpl::GetIDsOfNames
- ATLCOM/ATL::IDispEventImpl::GetTypeInfo
- ATLCOM/ATL::IDispEventImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispEventImpl::GetUserDefinedType
dev_langs: C++
helpviewer_keywords: IDispEventImpl class
ms.assetid: a64b5288-35cb-4638-aad6-2d15b1c7cf7b
caps.latest.revision: "22"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f052ddf0194cf28a0845ae51b9503841ca880912
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="idispeventimpl-class"></a>IDispEventImpl – třída
Tato třída poskytuje implementace `IDispatch` metody.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <UINT nID, class T,
    const IID* pdiid = &IID_NULL,
    const GUID* plibid = &GUID_NULL,
    WORD wMajor = 0,
    WORD wMinor = 0, 
    class tihclass = CcomTypeInfoHolder>  
class ATL_NO_VTABLE IDispEventImpl : public IDispEventSimpleImpl<nID, T, pdiid>
```  
  
#### <a name="parameters"></a>Parametry  
 `nID`  
 Jedinečný identifikátor pro zdrojový objekt. Když `IDispEventImpl` je základní třídou pro složeného ovládacího prvku, použijte ID prostředku požadované obsažené ovládací prvek pro tento parametr. V ostatních případech použijte libovolné kladné celé číslo.  
  
 `T`  
 Třída uživatele, který je odvozený od `IDispEventImpl`.  
  
 `pdiid`  
 Ukazatel na identifikátory IID dispinterface událostí implementována touto třídou. Toto rozhraní musí být definována v knihovně typ, který je označený jako `plibid`, `wMajor`, a `wMinor`.  
  
 `plibid`  
 Ukazatel na knihovny typů, která definuje rozhraní dispatch na kterou odkazuje `pdiid`. Pokud **& GUID_NULL**, knihovny typů bude načten z objektu sourcing události.  
  
 `wMajor`  
 Hlavní verze knihovny typů. Výchozí hodnota je 0.  
  
 `wMinor`  
 Vedlejší verze knihovny typů. Výchozí hodnota je 0.  
  
 `tihclass`  
 Třída, která slouží ke správě informací o typu pro `T`. Výchozí hodnota je – třída typu `CComTypeInfoHolder`; však tento parametr šablony můžete přepsat zadáním – třída typu jiné než `CComTypeInfoHolder`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|[IDispEventImpl::_tihclass](../../atl/reference/idispeventimpl-class.md)|Třída, která slouží ke správě informací o typu. Ve výchozím nastavení `CComTypeInfoHolder`.|  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[IDispEventImpl::IDispEventImpl](#idispeventimpl)|Konstruktor|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IDispEventImpl::GetFuncInfoFromId](#getfuncinfofromid)|Vyhledá funkce index pro identifikátor zadaný odesílání.|  
|[IDispEventImpl::GetIDsOfNames](#getidsofnames)|Mapuje odpovídající sadu celé číslo hodnoty dispID jednoho člena a volitelná sada názvy argumentu.|  
|[IDispEventImpl::GetTypeInfo](#gettypeinfo)|Načte informace o typu objektu.|  
|[IDispEventImpl::GetTypeInfoCount](#gettypeinfocount)|Načte počet typ informace rozhraní.|  
|[IDispEventImpl::GetUserDefinedType](#getuserdefinedtype)|Získá základní typ uživatelem definovaného typu.|  
  
## <a name="remarks"></a>Poznámky  
 `IDispEventImpl`poskytuje způsob implementace dispinterface události, aniž byste si, jak zadat kód implementace pro každý metoda/událost na tomto rozhraní. `IDispEventImpl`poskytuje implementaci `IDispatch` metody. Stačí zadat implementace události, které mají být při zpracování.  
  
 `IDispEventImpl`funguje ve spojení s mapy jímek událostí ve třídě události trasy k funkci příslušnou obslužnou rutinu. K použití této třídy:  
  

 Přidat [SINK_ENTRY](composite-control-macros.md#sink_entry) nebo [SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex) makra mapy jímek událostí pro každou jednotlivou událost na každém objektu, který chcete zpracovávat. Při použití `IDispEventImpl` jako základní třída složeného ovládacího prvku, můžete volat [AtlAdviseSinkMap](connection-point-global-functions.md#atladvisesinkmap) k zahájení a přerušení připojení ke zdroji událostí pro všechny položky události jímky mapy. V ostatních případech, nebo větší kontrolu, volání [DispEventAdvise](idispeventsimpleimpl-class.md#dispeventadvise) k navázání připojení mezi zdrojový objekt a základní třídy. Volání [DispEventUnadvise](idispeventsimpleimpl-class.md#dispeventunadvise) k přerušení připojení.  

  
 Musí být odvozeny od `IDispEventImpl` (pomocí jedinečnou hodnotu pro `nID`) pro každý objekt, pro kterou je potřeba zpracování událostí. Základní třída můžete znovu použít, unadvising proti jeden zdrojový objekt, který pak radí proti objekt jiný zdroj, ale maximální počet objektů zdroje, které mohou být zpracovány v jednom okamžiku jeden objekt, je omezen počet `IDispEventImpl` základní třídy.  
  
 `IDispEventImpl`poskytuje stejné funkce jako [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md), s výjimkou získá typ informace o rozhraní z knihovny typů, místo aby ho jako ukazatel na zadána [_ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md) Struktura. Použití `IDispEventSimpleImpl` když nemáte mají knihovny typů popisující rozhraní události nebo chtít vyhnout režie spojená s použitím knihovny typů.  
  
> [!NOTE]
> `IDispEventImpl`a `IDispEventSimpleImpl` zadejte vlastní implementaci **IUnknown::QueryInterface** povolení jednotlivých `IDispEventImpl` a `IDispEventSimpleImpl` základní třída tak, aby fungoval jako samostatné identity COM zároveň umožňuje přímý přístup k – třída Členové v hlavní objektu COM.  
  
 Implementace CE ATL ActiveX událostí jímky pouze podporuje návratové hodnoty typu HRESULT nebo void z vaší metody obslužná rutina události; všechny ostatní návratové hodnoty není podporován a jeho chování není definováno.  
  
 Další informace najdete v tématu [podpora IDispEventImpl](../../atl/supporting-idispeventimpl.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `_IDispEvent`  
  
 `_IDispEventLocator`  
  
 [IDispEventSimpleImpl](../../atl/reference/idispeventsimpleimpl-class.md)  
  
 `IDispEventImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="getfuncinfofromid"></a>IDispEventImpl::GetFuncInfoFromId  
 Vyhledá funkce index pro identifikátor zadaný odesílání.  
  
```
HRESULT GetFuncInfoFromId(
    const IID& iid,
    DISPID dispidMember,
    LCID lcid,
    _ATL_FUNC_INFO& info);
```  
  
### <a name="parameters"></a>Parametry  
 `iid`  
 [v] Odkaz na ID funkce.  
  
 *dispidMember*  
 [v] Odesílání ID funkce.  
  
 `lcid`  
 [v] Národní prostředí kontextu ID funkce.  
  
 `info`  
 [v] Struktura, která určuje, jak je tato funkce volána.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní `HRESULT` hodnotu.  
  
##  <a name="getidsofnames"></a>IDispEventImpl::GetIDsOfNames  
 Mapuje odpovídající sadu celé číslo hodnoty dispID, které se dají použít na následující volání jednoho člena a volitelná sada názvy argumentu [volání metody IDispatch::Invoke](http://msdn.microsoft.com/en-us/964ade8e-9d8a-4d32-bd47-aa678912a54d).  
  
```
STDMETHOD(GetIDsOfNames)(
    REFIID riid,
    LPOLESTR* rgszNames,
    UINT cNames,
    LCID lcid,
    DISPID* rgdispid);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [funkce IDispatch::GetIDsOfNames](http://msdn.microsoft.com/en-us/6f6cf233-3481-436e-8d6a-51f93bf91619) ve Windows SDK.  
  
##  <a name="gettypeinfo"></a>IDispEventImpl::GetTypeInfo  
 Načte informace o typu objektu, který lze použít k získání informací o typu pro rozhraní.  
  
```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```  
  
### <a name="remarks"></a>Poznámky  
  
##  <a name="gettypeinfocount"></a>IDispEventImpl::GetTypeInfoCount  
 Získá počet rozhraní typu informací, které objekt poskytuje (0 nebo 1).  
  
```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IDispatch::GetTypeInfoCount](http://msdn.microsoft.com/en-us/da876d53-cb8a-465c-a43e-c0eb272e2a12) ve Windows SDK.  
  
##  <a name="getuserdefinedtype"></a>IDispEventImpl::GetUserDefinedType  
 Získá základní typ uživatelem definovaného typu.  
  
```
VARTYPE GetUserDefinedType(
    ITypeInfo* pTI,
    HREFTYPE hrt);
```  
  
### <a name="parameters"></a>Parametry  
 `pTI`  
 [v] Ukazatel [ITypeInfo](http://msdn.microsoft.com/en-us/f3356463-3373-4279-bae1-953378aa2680) obsahující typ uživatelské rozhraní.  
  
 *hrt*  
 [v] Popisovač pro popis typu, který má být načtena.  
  
### <a name="return-value"></a>Návratová hodnota  
 Typ variant.  
  
### <a name="remarks"></a>Poznámky  
 V tématu [volání ITypeInfo::GetRefTypeInfo](http://msdn.microsoft.com/en-us/61d3b31d-6591-4e55-9e82-5246a168be00).  
  
##  <a name="idispeventimpl"></a>IDispEventImpl::IDispEventImpl  
 Konstruktor Uloží hodnoty parametrů šablony třídy `plibid`, `pdiid`, `wMajor`, a `wMinor`.  
  
```
IDispEventImpl();
```  
  
##  <a name="tihclass"></a>IDispEventImpl::tihclass  
 Tato definice typu je instance třídy parametr šablony `tihclass`.  
  
```
typedef tihclass _tihclass;
```  
  
### <a name="remarks"></a>Poznámky  
 Ve výchozím nastavení, třída je `CComTypeInfoHolder`. `CComTypeInfoHolder`spravuje informace o typu pro třídu.  
  
## <a name="see-also"></a>Viz také  
 [Struktura _ATL_FUNC_INFO](../../atl/reference/atl-func-info-structure.md)   
 [IDispatchImpl – třída](../../atl/reference/idispatchimpl-class.md)   
 [IDispEventSimpleImpl – třída](../../atl/reference/idispeventsimpleimpl-class.md)   
 [SINK_ENTRY](composite-control-macros.md#sink_entry)   
 [SINK_ENTRY_EX](composite-control-macros.md#sink_entry_ex)   
 [SINK_ENTRY_INFO](composite-control-macros.md#sink_entry_info)   
 [Přehled třídy](../../atl/atl-class-overview.md)