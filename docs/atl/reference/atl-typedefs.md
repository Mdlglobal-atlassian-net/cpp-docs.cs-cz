---
title: "ATL – definice TypeDef | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlcore/ATL::_ATL_BASE_MODULE
- atlbase/ATL::_ATL_COM_MODULE
- atlbase/ATL::_ATL_MODULE
- atlbase/ATL::_ATL_WIN_MODULE
- atlutil/ATL::ATL_URL_PORT
- atlbase/ATL::CComDispatchDriver
- atlbase/ATL::CComGlobalsThreadModel
- atlbase/ATL::CComObjectThreadModel
- atlwin/ATL::CContainedWindow
- atlpath/ATL::CPath
- atlpath/ATL::CPathA
- atlpath/ATL::CPathW
- " atlsimpcoll/ATL::CSimpleValArray"
- " atlutil/ATL::LPCURL"
- atlbase/ATL::DefaultThreadTraits
- atlutil/ATL::LPURL
dev_langs: C++
helpviewer_keywords:
- typedefs, ATL
- typedefs
- ATL, typedefs
ms.assetid: 7dd05baa-3efb-4e3b-af23-793c610f4560
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: ae5a0d527bd503422176fb01f4024d98100ef351
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="atl-typedefs"></a>ATL – definice TypeDef
Aktivní knihovna šablon obsahuje následující definice TypeDef.  
  
|||  
|-|-|  
|[_ATL_BASE_MODULE](#_atl_base_module)|Definován jako definice typu na základě [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md).|  
|[_ATL_COM_MODULE](#_atl_com_module)|Definován jako definice typu na základě [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md).|  
|[_ATL_MODULE](#_atl_module)|Definován jako definice typu na základě [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md).|  
|[_ATL_WIN_MODULE](#_atl_win_module)|Definován jako definice typu na základě [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|  
|[ATL_URL_PORT](#atl_url_port)|Typ používaný [CUrl](../../atl/reference/curl-class.md) pro zadání číslo portu.|  
|[CComDispatchDriver](#ccomdispatchdriver)|Tato třída spravuje ukazatele rozhraní COM.|  
|[CComGlobalsThreadModel](#ccomglobalsthreadmodel)|Volá metody, modelu, bez ohledu na to, používá model vláken odpovídající vlákno.|  
|[CComObjectThreadModel](#ccomobjectthreadmodel)|Volá metody, modelu, bez ohledu na to, používá model vláken odpovídající vlákno.|  
|[CContainedWindow](#ccontainedwindow)|Tato třída je specializované **CContainedWindowT.**|  
|[CPath](#cpath)|Specializace z [CPathT](../../atl/reference/cpatht-class.md) pomocí `CString`.|  
|[CPathA](#cpatha)|Specializace z [CPathT](../../atl/reference/cpatht-class.md) pomocí `CStringA`.|  
|[CPathW](#cpathw)|Specializace z [CPathT](../../atl/reference/cpatht-class.md) pomocí `CStringW`.|  
|[CSimpleValArray](#csimplevalarray)|Představuje pole pro ukládání jednoduché typy.|  
|[DefaultThreadTraits](#defaultthreadtraits)|Výchozí vlastnosti třídy přístup z více vláken.|  
|[LPCURL](#lpcurl)|Ukazatel na konstantu [CUrl](../../atl/reference/curl-class.md) objektu.|  
|[LPURL](#lpurl)|Ukazatel [CUrl](../../atl/reference/curl-class.md) objektu.|  
  
##  <a name="_atl_base_module"></a>_ATL_BASE_MODULE  
 Definován jako definice typu podle _ATL_BASE_MODULE70.  
  
```   
typedef ATL::_ATL_BASE_MODULE70 _ATL_BASE_MODULE;   
```  
  
### <a name="remarks"></a>Poznámky  
 V každém projektu knihovny ATL použít. Na základě [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md).  
  
 Třídy, které jsou součástí třídy ATL 7.0 modulu odvozen z _ATL_BASE_MODULE struktury.  Další informace o ATL – třídy modulů, najdete v části [COM moduly třídy](../../atl/com-modules-classes.md).  

## <a name="requirements"></a>Požadavky
**Záhlaví:** atlcore.h

##  <a name="_atl_com_module"></a>_ATL_COM_MODULE  
 Definován jako definice typu podle _ATL_COM_MODULE70.  
  
```   
typedef ATL::_ATL_COM_MODULE70 _ATL_COM_MODULE;   
```  
  
### <a name="remarks"></a>Poznámky  
 Projekty knihovny ATL, která používá funkce COM používán. Na základě [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md).  

## <a name="requirements"></a>Požadavky
**Záhlaví:** atlbase.h
  
##  <a name="_atl_module"></a>_ATL_MODULE  
 Definován jako definice typu podle _ATL_MODULE70.  
  
```   
typedef ATL::_ATL_MODULE70 _ATL_MODULE;   
```  
## <a name="requirements"></a>Požadavky
**Hlavičky:** 
  
### <a name="remarks"></a>Poznámky  
 Na základě [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md).  
  
##  <a name="_atl_win_module"></a>_ATL_WIN_MODULE  
 Definován jako definice typu podle _ATL_WIN_MODULE70.  
  
```   
typedef ATL::_ATL_WIN_MODULE70 _ATL_WIN_MODULE; 
 
```  
  
### <a name="remarks"></a>Poznámky  
 Používá všechny projekty knihovny ATL, která používá oddílová funkce. Na základě [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md).  

## <a name="requirements"></a>Požadavky
**Záhlaví:** atlbase.h 
  
##  <a name="atl_url_port"></a>ATL_URL_PORT 
  Typ používaný [CUrl](curl-class.md) pro zadání číslo portu.
```  
typedef WORD ATL_URL_PORT;
```  

## <a name="requirements"></a>Požadavky
**Záhlaví:** atlutil.h

##  <a name="ccomdispatchdriver"></a>CComDispatchDriver  
 Tato třída spravuje ukazatele rozhraní COM.  
  
```   
typedef CComQIPtr<IDispatch, &__uuidof(IDispatch)> CComDispatchDriver;   
```  
## <a name="requirements"></a>Požadavky
**Záhlaví:** atlbase.h
  
##  <a name="ccomglobalsthreadmodel"></a>CComGlobalsThreadModel  
 Volá metody, modelu, bez ohledu na to, používá model vláken odpovídající vlákno.  
  
```   
#if defined(_ATL_SINGLE_THREADED)  
typedef CComSingleThreadModel CComGlobalsThreadModel;  
#elif defined(_ATL_APARTMENT_THREADED)  
typedef CComMultiThreadModel CComGlobalsThreadModel;  
#elif defined(_ATL_FREE_THREADED)  
typedef CComMultiThreadModel CComGlobalsThreadModel;  
#else  
#pragma message ("No global threading model defined")  
#endif   
```  
  
### <a name="remarks"></a>Poznámky  
 V závislosti na modelu vláken používá vaše aplikace `typedef` název `CComGlobalsThreadModel` odkazuje buď [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) nebo [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Tyto třídy poskytují další `typedef` názvy tak, aby odkazovaly třídu kritická sekce.  
  
> [!NOTE]
> `CComGlobalsThreadModel`neodkazuje třídu [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).  
  
 Pomocí `CComGlobalsThreadModel` uvolní můžete zadat určitou třídu modelu vláken. Bez ohledu na to, používá model vláken bude mít název příslušné metody.  
  
 Kromě `CComGlobalsThreadModel`, poskytuje ATL `typedef` název [CComObjectThreadModel](#ccomobjectthreadmodel). Třída odkazuje každý `typedef` závisí na model vláken používaný, jak je znázorněno v následující tabulce:  
  
|– definice typedef|Jeden dělení na vlákna|Dělení objektu Apartment|Volné dělení na vlákna|  
|-------------|----------------------|-------------------------|--------------------|  
|`CComObjectThreadModel`|S|S|M|  
|`CComGlobalsThreadModel`|S|M|M|  
  
 S = `CComSingleThreadModel`; M =`CComMultiThreadModel`  
  
 Použití `CComObjectThreadModel` v rámci jednoho objektu třídy. Použití `CComGlobalsThreadModel` v objektu, která je globálně dostupnou vašeho programu nebo pokud chcete chránit prostředky modulu napříč více vláken.  

## <a name="requirements"></a>Požadavky
**Záhlaví:** atlbase.h
  
##  <a name="ccomobjectthreadmodel"></a>CComObjectThreadModel  
 Volá metody, modelu, bez ohledu na to, používá model vláken odpovídající vlákno.  
  
```   
#if defined(_ATL_SINGLE_THREADED)  
typedef CComSingleThreadModel CComObjectThreadModel;  
#elif defined(_ATL_APARTMENT_THREADED)  
typedef CComSingleThreadModel CComObjectThreadModel;  
#elif defined(_ATL_FREE_THREADED)  
typedef CComMultiThreadModel CComObjectThreadModel;  
#else  
#pragma message ("No global threading model defined")  
#endif   
```  
  
### <a name="remarks"></a>Poznámky  
 V závislosti na modelu vláken používá vaše aplikace `typedef` název `CComObjectThreadModel` odkazuje buď [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) nebo [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Tyto třídy poskytují další `typedef` názvy tak, aby odkazovaly třídu kritická sekce.  
  
> [!NOTE]
> `CComObjectThreadModel`neodkazuje třídu [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).  
  
 Pomocí `CComObjectThreadModel` uvolní můžete zadat určitou třídu modelu vláken. Bez ohledu na to, používá model vláken bude mít název příslušné metody.  
  
 Kromě `CComObjectThreadModel`, poskytuje ATL `typedef` název [CComGlobalsThreadModel](#ccomglobalsthreadmodel). Třída odkazuje každý `typedef` závisí na model vláken používaný, jak je znázorněno v následující tabulce:  
  
|– definice typedef|Jeden dělení na vlákna|Dělení objektu Apartment|Volné dělení na vlákna|  
|-------------|----------------------|-------------------------|--------------------|  
|`CComObjectThreadModel`|S|S|M|  
|`CComGlobalsThreadModel`|S|M|M|  
  
 S = `CComSingleThreadModel`; M =`CComMultiThreadModel`  
  
 Použití `CComObjectThreadModel` v rámci jednoho objektu třídy. Použití `CComGlobalsThreadModel` v objektu, který je buď globálně dostupnou vašeho programu, nebo pokud chcete chránit prostředky modulu napříč více vláken.  

## <a name="requirements"></a>Požadavky
**Záhlaví:** atlbase.h
  
##  <a name="ccontainedwindow"></a>CContainedWindow  
 Tato třída je specializované **CContainedWindowT.**  
  
```   
typedef CContainedWindowT<CWindow> CContainedWindow;   
```  

## <a name="requirements"></a>Požadavky
**Záhlaví:** atlwin.h
  
### <a name="remarks"></a>Poznámky  
 `CContainedWindow`je specializované [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md). Pokud chcete změnit základní třídu nebo vlastnosti, použijte `CContainedWindowT` přímo.  
  
##  <a name="cpath"></a>CPath  
 Specializace z [CPathT](../../atl/reference/cpatht-class.md) pomocí `CString`.  
  
```   
typedef CPathT<CString> CPath;   
```  

## <a name="requirements"></a>Požadavky
**Záhlaví:** atlpath.h
  
##  <a name="cpatha"></a>CPathA  
 Specializace z [CPathT](../../atl/reference/cpatht-class.md) pomocí `CStringA`.  
  
```   
typedef CPathT<CStringA> CPathA;   
```

## <a name="requirements"></a>Požadavky
**Záhlaví:** atlpath.h  
  
##  <a name="cpathw"></a>CPathW  
 Specializace z [CPathT](../../atl/reference/cpatht-class.md) pomocí `CStringW`.  
  
```   
typedef ATL::CPathT<CStringW> CPathW;   
```  
## <a name="requirements"></a>Požadavky
**Záhlaví:** atlpath.h
  
##  <a name="csimplevalarray"></a>CSimpleValArray  
 Představuje pole pro ukládání jednoduché typy.  
  
```   
#define CSimpleValArray CSimpleArray   
```  

  
### <a name="remarks"></a>Poznámky  
 `CSimpleValArray`slouží k vytváření a správě pole obsahující jednoduché datové typy. Je jednoduchý #define z [CSimpleArray](../../atl/reference/csimplearray-class.md).  


## <a name="requirements"></a>Požadavky
**Záhlaví:** atlsimpcoll.h
  
##  <a name="lpcurl"></a>LPCURL  
 Ukazatel na konstantu [CUrl](../../atl/reference/curl-class.md) objektu.  
  
```   
typedef const CUrl* LPCURL;   
```  

## <a name="requirements"></a>Požadavky
**Záhlaví:** atlutil.h

##  <a name="defaultthreadtraits"></a>DefaultThreadTraits
Výchozí vlastnosti třídy přístup z více vláken.

### <a name="syntax"></a>Syntaxe
```  
      #if defined(_MT)  
   typedef CRTThreadTraits DefaultThreadTraits;  
#else  
   typedef Win32ThreadTraits DefaultThreadTraits;  
#endif  
```

## <a name="remarks"></a>Poznámky
Pokud v aktuálním projektu používá s více vlákny CRT, DefaultThreadTraits je definován jako CRTThreadTraits. Win32ThreadTraits, jinak se používá.


## <a name="requirements"></a>Požadavky
**Záhlaví:** atlbase.h
  
##  <a name="lpurl"></a>LPURL  
 Ukazatel [CUrl](../../atl/reference/curl-class.md) objektu.  
  
```   
typedef CUrl* LPURL;   
```  

## <a name="requirements"></a>Požadavky
**Záhlaví:** atlutil.h


## <a name="see-also"></a>Viz také  
 [ATL COM plochy součásti](../../atl/atl-com-desktop-components.md)   
 [Funkce](../../atl/reference/atl-functions.md)   
 [Globální proměnné](../../atl/reference/atl-global-variables.md)   
 [Struktury](../../atl/reference/atl-structures.md)   
 [Makra](../../atl/reference/atl-macros.md)   
 [Třídy](../../atl/reference/atl-classes.md)