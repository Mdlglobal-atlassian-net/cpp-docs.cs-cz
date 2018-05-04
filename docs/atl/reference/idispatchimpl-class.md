---
title: Třída IDispatchImpl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IDispatchImpl
- ATLCOM/ATL::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::IDispatchImpl
- ATLCOM/ATL::IDispatchImpl::GetIDsOfNames
- ATLCOM/ATL::IDispatchImpl::GetTypeInfo
- ATLCOM/ATL::IDispatchImpl::GetTypeInfoCount
- ATLCOM/ATL::IDispatchImpl::Invoke
dev_langs:
- C++
helpviewer_keywords:
- dual interfaces, classes
- IDispatchImpl class
- IDispatch class support in ATL
ms.assetid: 8108eb36-1228-4127-a203-3ab5ba488892
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7fddf556eba07264f6ea0b01edea3e3d1e8a3a7b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="idispatchimpl-class"></a>IDispatchImpl – třída
Poskytuje výchozí implementaci pro `IDispatch` součástí duální rozhraní.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template<class T,
        const IID* piid= &__uuidof(T),
        const GUID* plibid = &CAtlModule::m_libid,
        WORD wMajor = 1,
        WORD wMinor = 0, 
        class tihclass = CComTypeInfoHolder>
class ATL_NO_VTABLE IDispatchImpl : public T
```  
  
#### <a name="parameters"></a>Parametry  
 [v] `T`  
 Duální rozhraní.  
  
 [v] `piid`  
 Ukazatel na identifikátory IID `T`.  
  
 [v] `plibid`  
 Ukazatel na ID KNIHOVNY knihovny typů, který obsahuje informace o rozhraní. Ve výchozím nastavení je předaná knihovny typů úrovni serveru.  
  
 [v] `wMajor`  
 Hlavní verze knihovny typů. Výchozí hodnota je 1.  
  
 [v] `wMinor`  
 Vedlejší verze knihovny typů. Výchozí hodnota je 0.  
  
 [v] `tihclass`  
 Třída, která slouží ke správě informací o typu pro `T`. Výchozí hodnota je `CComTypeInfoHolder`.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[IDispatchImpl::IDispatchImpl](#idispatchimpl)|Konstruktor Volání `AddRef` na proměnnou chráněného člena, který spravuje informace o typu pro duální rozhraní. Volání destruktoru `Release`.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IDispatchImpl::GetIDsOfNames](#getidsofnames)|Mapuje sadu názvů na odpovídající sadu identifikátorů pro rozesílání.|  
|[IDispatchImpl::GetTypeInfo](#gettypeinfo)|Načte informace o typu pro duální rozhraní.|  
|[IDispatchImpl::GetTypeInfoCount](#gettypeinfocount)|Určuje, zda je k dispozici pro duální rozhraní informací o typu.|  
|[IDispatchImpl::Invoke](#invoke)|Poskytuje přístup k metody a vlastnosti, které jsou vystavené duální rozhraní.|  
  
## <a name="remarks"></a>Poznámky  
 `IDispatchImpl` poskytuje výchozí implementaci pro `IDispatch` součástí libovolné duální rozhraní v objektu. Duální rozhraní je odvozena z `IDispatch` a používá jenom automatizace kompatibilní s typy. Podobně jako dispinterface podporuje rozhraní dual časná vazba a pozdní vazba; duální rozhraní však také podporuje vtable vazby.  
  
 Následující příklad ukazuje Typická implementace `IDispatchImpl`.  
  
 [!code-cpp[NVC_ATL_COM#47](../../atl/codesnippet/cpp/idispatchimpl-class_1.h)]  
  
 Ve výchozím nastavení `IDispatchImpl` třída vyhledá informace o typu `T` v registru. Chcete-li implementovat registrace rozhraní, můžete použít `IDispatchImpl` třída není potřeba přístup k registru pomocí předdefinovaných verze čísla. Pokud vytvoříte `IDispatchImpl` objekt, který má 0xFFFF jako hodnota `wMajor` a 0xFFFF hodnotu `wMinor`, `IDispatchImpl` třída načte knihovny typů ze souboru .dll místo registru.  
  
 `IDispatchImpl` obsahuje statický člen typu `CComTypeInfoHolder` který spravuje informace o typu pro duální rozhraní. Pokud máte více objektů, které implementují duální stejné rozhraní, pouze jedna instance `CComTypeInfoHolder` se používá.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `T`  
  
 `IDispatchImpl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="getidsofnames"></a>  IDispatchImpl::GetIDsOfNames  
 Mapuje sadu názvů na odpovídající sadu identifikátorů pro rozesílání.  
  
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
  
##  <a name="gettypeinfo"></a>  IDispatchImpl::GetTypeInfo  
 Načte informace o typu pro duální rozhraní.  
  
```
STDMETHOD(GetTypeInfo)(
    UINT itinfo,
    LCID lcid,
    ITypeInfo** pptinfo);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IDispatch::GetTypeInfo](http://msdn.microsoft.com/en-us/cc1ec9aa-6c40-4e70-819c-a7c6dd6b8c99) ve Windows SDK.  
  
##  <a name="gettypeinfocount"></a>  IDispatchImpl::GetTypeInfoCount  
 Určuje, zda je k dispozici pro duální rozhraní informací o typu.  
  
```
STDMETHOD(GetTypeInfoCount)(UINT* pctinfo);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu `IDispatch::GetTypeInfoCount` ve Windows SDK.  
  
##  <a name="idispatchimpl"></a>  IDispatchImpl::IDispatchImpl  
 Konstruktor Volání `AddRef` na proměnnou chráněného člena, který spravuje informace o typu pro duální rozhraní. Volání destruktoru **verze**.  
  
```
IDispatchImpl();
```  
  
##  <a name="invoke"></a>  IDispatchImpl::Invoke  
 Poskytuje přístup k metody a vlastnosti, které jsou vystavené duální rozhraní.  
  
```
STDMETHOD(Invoke)(
    DISPID dispidMember,
    REFIID riid,
    LCID lcid,
    WORD wFlags,
    DISPPARAMS* pdispparams,
    VARIANT* pvarResult,
    EXCEPINFO* pexcepinfo,
    UINT* puArgErr);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [volání metody IDispatch::Invoke](http://msdn.microsoft.com/en-us/964ade8e-9d8a-4d32-bd47-aa678912a54d) ve Windows SDK.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)
