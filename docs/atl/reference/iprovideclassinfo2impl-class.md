---
title: Třída IProvideClassInfo2Impl | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl::IProvideClassInfo2Impl
- ATLCOM/ATL::IProvideClassInfo2Impl::GetClassInfo
- ATLCOM/ATL::IProvideClassInfo2Impl::GetGUID
- ATLCOM/ATL::IProvideClassInfo2Impl::_tih
dev_langs:
- C++
helpviewer_keywords:
- IProvideClassInfo2Impl class
- IProvideClassInfo2 ATL implementation
- class information, ATL
ms.assetid: d74956e8-9c69-4cba-b99d-ca1ac031bb9d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a970b0258c8d353dabad96d712598416caf2acb4
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361342"
---
# <a name="iprovideclassinfo2impl-class"></a>IProvideClassInfo2Impl – třída
Tato třída poskytuje výchozí implementaci třídy [IProvideClassInfo](http://msdn.microsoft.com/library/windows/desktop/ms687303) a [IProvideClassInfo2](http://msdn.microsoft.com/library/windows/desktop/ms693764) metody.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <const CLSID* pcoclsid,
    const IID* psrcid,
    const GUID* plibid = &CAtlModule::m_libid,
    WORD wMajor = 1,
    WORD wMinor = 0, class tihclass = CComTypeInfoHolder>  
class ATL_NO_VTABLE IProvideClassInfo2Impl : public IProvideClassInfo2
```  
  
#### <a name="parameters"></a>Parametry  
 *pcoclsid*  
 Ukazatel na identifikátor třída typu coclass'.  
  
 *psrcid*  
 Ukazatel na identifikátor třída typu coclass' výchozí odchozí dispinterface.  
  
 `plibid`  
 Ukazatel na ID KNIHOVNY knihovny typů, který obsahuje informace o rozhraní. Ve výchozím nastavení je předaná knihovny typů úrovni serveru.  
  
 `wMajor`  
 Hlavní verze knihovny typů. Výchozí hodnota je 1.  
  
 `wMinor`  
 Vedlejší verze knihovny typů. Výchozí hodnota je 0.  
  
 `tihclass`  
 Třída, která slouží ke správě informací o typu coclass. Výchozí hodnota je `CComTypeInfoHolder`.  
  
## <a name="members"></a>Členové  
  
### <a name="constructors"></a>Konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[IProvideClassInfo2Impl::IProvideClassInfo2Impl](#iprovideclassinfo2impl)|Konstruktor|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[IProvideClassInfo2Impl::GetClassInfo](#getclassinfo)|Načte **ITypeInfo** ukazatel na informace o typu coclass.|  
|[IProvideClassInfo2Impl::GetGUID](#getguid)|Načte identifikátor GUID pro odchozí dispinterface objektu.|  
  
### <a name="protected-data-members"></a>Chráněné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[IProvideClassInfo2Impl::_tih](#_tih)|Spravuje informace o typu coclass.|  
  
## <a name="remarks"></a>Poznámky  
 [IProvideClassInfo2](http://msdn.microsoft.com/library/windows/desktop/ms693764) rozšiřuje rozhraní [IProvideClassInfo](http://msdn.microsoft.com/library/windows/desktop/ms687303) přidáním `GetGUID` metoda. Tato metoda umožňuje klientům pro načtení objektu odchozí rozhraní IID pro jeho výchozí sadu událostí. Třída `IProvideClassInfo2Impl` poskytuje výchozí implementaci třídy **IProvideClassInfo** a `IProvideClassInfo2` metody.  
  
 `IProvideClassInfo2Impl` obsahuje statický člen typu `CComTypeInfoHolder` který spravuje informace o typu coclass.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IProvideClassInfo2`  
  
 `IProvideClassInfo2Impl`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlcom  
  
##  <a name="getclassinfo"></a>  IProvideClassInfo2Impl::GetClassInfo  
 Načte `ITypeInfo` ukazatel na informace o typu coclass.  
  
```
STDMETHOD(GetClassInfo)(ITypeInfo** pptinfo);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IProvideClassInfo::GetClassInfo](http://msdn.microsoft.com/library/windows/desktop/ms690192) ve Windows SDK.  
  
##  <a name="getguid"></a>  IProvideClassInfo2Impl::GetGUID  
 Načte identifikátor GUID pro odchozí dispinterface objektu.  
  
```
STDMETHOD(GetGUID)(
    DWORD dwGuidKind,
    GUID* pGUID);
```  
  
### <a name="remarks"></a>Poznámky  
 V tématu [IProvideClassInfo2::GetGUID](http://msdn.microsoft.com/library/windows/desktop/ms679721) ve Windows SDK.  
  
##  <a name="iprovideclassinfo2impl"></a>  IProvideClassInfo2Impl::IProvideClassInfo2Impl  
 Konstruktor  
  
```
IProvideClassInfo2Impl();
```  
  
### <a name="remarks"></a>Poznámky  
 Volání `AddRef` na [_tih](#_tih) člen. Volání destruktoru **verze**.  
  
##  <a name="_tih"></a>  IProvideClassInfo2Impl::_tih  
 Tento člen statických dat je instance třídy parametr šablony, `tihclass`, který ve výchozím nastavení je `CComTypeInfoHolder`.  
  
```
static  tihclass
    _tih;
```     
  
### <a name="remarks"></a>Poznámky  
 `_tih` Spravuje informace o typu coclass.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)
