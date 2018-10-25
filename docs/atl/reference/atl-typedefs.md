---
title: ATL – definice TypeDef | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
dev_langs:
- C++
helpviewer_keywords:
- typedefs, ATL
- typedefs
- ATL, typedefs
ms.assetid: 7dd05baa-3efb-4e3b-af23-793c610f4560
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9835b8cadb5a24aea130b1e32d919ebb49d20293
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065692"
---
# <a name="atl-typedefs"></a>ATL – definice TypeDef

Knihovnu Active Template Library obsahuje následující definice TypeDef.

|||
|-|-|
|[_ATL_BASE_MODULE](#_atl_base_module)|Definice jako definice typu na základě [_atl_base_module70 –](../../atl/reference/atl-base-module70-structure.md).|
|[_ATL_COM_MODULE](#_atl_com_module)|Definice jako definice typu na základě [_atl_com_module70 –](../../atl/reference/atl-com-module70-structure.md).|
|[_ATL_MODULE](#_atl_module)|Definice jako definice typu na základě [_atl_module70 –](../../atl/reference/atl-module70-structure.md).|
|[_ATL_WIN_MODULE](#_atl_win_module)|Definice jako definice typu na základě [_atl_win_module70 –](../../atl/reference/atl-win-module70-structure.md)|
|[ATL_URL_PORT](#atl_url_port)|Typ používaný [CUrl](../../atl/reference/curl-class.md) pro zadáte číslo portu.|
|[CComDispatchDriver](#ccomdispatchdriver)|Tato třída slouží ke správě ukazatele rozhraní modelu COM.|
|[CComGlobalsThreadModel](#ccomglobalsthreadmodel)|Volání metody modelu, bez ohledu na to, používá model vláken odpovídající vlákno.|
|[CComObjectThreadModel](#ccomobjectthreadmodel)|Volání metody modelu, bez ohledu na to, používá model vláken odpovídající vlákno.|
|[CContainedWindow](#ccontainedwindow)|Tato třída je specializací `CContainedWindowT`.|
|[CPath](#cpath)|Specializace [cpatht –](../../atl/reference/cpatht-class.md) pomocí `CString`.|
|[CPathA](#cpatha)|Specializace [cpatht –](../../atl/reference/cpatht-class.md) pomocí `CStringA`.|
|[CPathW](#cpathw)|Specializace [cpatht –](../../atl/reference/cpatht-class.md) pomocí `CStringW`.|
|[CSimpleValArray](#csimplevalarray)|Představuje pole pro ukládání jednoduché typy.|
|[DefaultThreadTraits](#defaultthreadtraits)|Třída vlastností výchozí vlákna.|
|[LPCURL](#lpcurl)|Ukazatel na konstantu [CUrl](../../atl/reference/curl-class.md) objektu.|
|[LPURL](#lpurl)|Ukazatel [CUrl](../../atl/reference/curl-class.md) objektu.|

##  <a name="_atl_base_module"></a>  _ATL_BASE_MODULE

Definuje jako podle _atl_base_module70 – definice typu.

```
typedef ATL::_ATL_BASE_MODULE70 _ATL_BASE_MODULE;
```

### <a name="remarks"></a>Poznámky

Používá se v každém projektu ATL. Na základě [_atl_base_module70 –](../../atl/reference/atl-base-module70-structure.md).

Třídy, které jsou součástí ATL – třídy modulů 7.0 jsou odvozeny z _ATL_BASE_MODULE struktury.  Další informace o ATL – třídy modulů najdete [třídy modulů COM](../../atl/com-modules-classes.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcore.h

##  <a name="_atl_com_module"></a>  _ATL_COM_MODULE

Definuje jako podle _atl_com_module70 – definice typu.

```
typedef ATL::_ATL_COM_MODULE70 _ATL_COM_MODULE;
```

### <a name="remarks"></a>Poznámky

Projekty knihovny ATL, které pomocí funkcí modelu COM používá. Na základě [_atl_com_module70 –](../../atl/reference/atl-com-module70-structure.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="_atl_module"></a>  _ATL_MODULE

Definuje jako podle _atl_module70 – definice typu.

```
typedef ATL::_ATL_MODULE70 _ATL_MODULE;
```

## <a name="requirements"></a>Požadavky

**Záhlaví:**

### <a name="remarks"></a>Poznámky

Na základě [_atl_module70 –](../../atl/reference/atl-module70-structure.md).

##  <a name="_atl_win_module"></a>  _ATL_WIN_MODULE

Definuje jako podle _atl_win_module70 – definice typu.

```
typedef ATL::_ATL_WIN_MODULE70 _ATL_WIN_MODULE;
```

### <a name="remarks"></a>Poznámky

Použít všechny projekty knihovny ATL, která používá oddílová funkce. Na základě [_atl_win_module70 –](../../atl/reference/atl-win-module70-structure.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="atl_url_port"></a>  ATL_URL_PORT

Typ používaný [CUrl](curl-class.md) pro zadáte číslo portu.

```
typedef WORD ATL_URL_PORT;
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlutil.h

##  <a name="ccomdispatchdriver"></a>  CComDispatchDriver

Tato třída slouží ke správě ukazatele rozhraní modelu COM.

```
typedef CComQIPtr<IDispatch, &__uuidof(IDispatch)> CComDispatchDriver;
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="ccomglobalsthreadmodel"></a>  CComGlobalsThreadModel

Volání metody modelu, bez ohledu na to, používá model vláken odpovídající vlákno.

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

V závislosti na modelu vláken, které používá vaše aplikace **typedef** název `CComGlobalsThreadModel` odkazuje buď [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) nebo [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Tyto třídy poskytují další `typedef` názvů, které se odkazují na třídu kritický oddíl.

> [!NOTE]
> `CComGlobalsThreadModel` neodkazuje na třídu [ccommultithreadmodelnocs –](../../atl/reference/ccommultithreadmodelnocs-class.md).

Pomocí `CComGlobalsThreadModel` díky které určení konkrétní třídy modelu vláken. Bez ohledu na to, používá model vláken bude volat odpovídající metody.

Kromě `CComGlobalsThreadModel`, knihovna ATL poskytuje **typedef** název [CComObjectThreadModel](#ccomobjectthreadmodel). Třída odkazovaná každou `typedef` závisí na model vláken použít, jak je znázorněno v následující tabulce:

|– definice typedef|Jeden dělení na vlákna|Práce s vlákny typu Apartment|Bezplatné dělení na vlákna|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`; M = `CComMultiThreadModel`

Použití `CComObjectThreadModel` v rámci jednoho objektu třídy. Použití `CComGlobalsThreadModel` v objektu, která je dostupná globálně vašemu programu, nebo pokud chcete chránit modulu prostředků napříč několika vlákny.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="ccomobjectthreadmodel"></a>  CComObjectThreadModel

Volání metody modelu, bez ohledu na to, používá model vláken odpovídající vlákno.

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

V závislosti na modelu vláken používaný vaší aplikací `typedef` název `CComObjectThreadModel` odkazuje buď [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) nebo [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Tyto třídy poskytují další `typedef` názvů, které se odkazují na třídu kritický oddíl.

> [!NOTE]
> `CComObjectThreadModel` neodkazuje na třídu [ccommultithreadmodelnocs –](../../atl/reference/ccommultithreadmodelnocs-class.md).

Pomocí `CComObjectThreadModel` díky které určení konkrétní třídy modelu vláken. Bez ohledu na to, používá model vláken bude volat odpovídající metody.

Kromě `CComObjectThreadModel`, knihovna ATL poskytuje **typedef** název [CComGlobalsThreadModel](#ccomglobalsthreadmodel). Třída odkazovaná každou **typedef** závisí na model vláken použít, jak je znázorněno v následující tabulce:

|– definice typedef|Jeden dělení na vlákna|Práce s vlákny typu Apartment|Bezplatné dělení na vlákna|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`; M = `CComMultiThreadModel`

Použití `CComObjectThreadModel` v rámci jednoho objektu třídy. Použití `CComGlobalsThreadModel` v objektu, který je buď globálně dostupné vašemu programu, nebo když chcete chránit prostředky modulu napříč více vlákny.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="ccontainedwindow"></a>  CContainedWindow

Tato třída je specializací `CContainedWindowT`.

```
typedef CContainedWindowT<CWindow> CContainedWindow;
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

### <a name="remarks"></a>Poznámky

`CContainedWindow` je specializací [ccontainedwindowt –](../../atl/reference/ccontainedwindowt-class.md). Pokud chcete změnit základní třídu nebo vlastnosti, použijte `CContainedWindowT` přímo.

##  <a name="cpath"></a>  CPath

Specializace [cpatht –](../../atl/reference/cpatht-class.md) pomocí `CString`.

```
typedef CPathT<CString> CPath;
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlpath.h

##  <a name="cpatha"></a>  CPathA

Specializace [cpatht –](../../atl/reference/cpatht-class.md) pomocí `CStringA`.

```
typedef CPathT<CStringA> CPathA;
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlpath.h

##  <a name="cpathw"></a>  CPathW

Specializace [cpatht –](../../atl/reference/cpatht-class.md) pomocí `CStringW`.

```
typedef ATL::CPathT<CStringW> CPathW;
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlpath.h

##  <a name="csimplevalarray"></a>  CSimpleValArray

Představuje pole pro ukládání jednoduché typy.

```
#define CSimpleValArray CSimpleArray
```

### <a name="remarks"></a>Poznámky

`CSimpleValArray` je k dispozici pro vytváření a správu pole obsahující jednoduché datové typy. Je jednoduchý #define z [csimplearray –](../../atl/reference/csimplearray-class.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsimpcoll.h

##  <a name="lpcurl"></a>  LPCURL

Ukazatel na konstantu [CUrl](../../atl/reference/curl-class.md) objektu.

```
typedef const CUrl* LPCURL;
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlutil.h

##  <a name="defaultthreadtraits"></a>  DefaultThreadTraits

Třída vlastností výchozí vlákna.

### <a name="syntax"></a>Syntaxe

```
#if defined(_MT)
   typedef CRTThreadTraits DefaultThreadTraits;
#else
   typedef Win32ThreadTraits DefaultThreadTraits;
#endif
```

## <a name="remarks"></a>Poznámky

Pokud aktuální projekt používá aplikaci s více vlákny CRT, DefaultThreadTraits je definován jako crtthreadtraits –. Win32threadtraits – v opačném případě se používá.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="lpurl"></a>  LPURL

Ukazatel [CUrl](../../atl/reference/curl-class.md) objektu.

```
typedef CUrl* LPURL;
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlutil.h

## <a name="see-also"></a>Viz také

[Desktopové komponenty ATL objektů COM](../../atl/atl-com-desktop-components.md)<br/>
[Funkce](../../atl/reference/atl-functions.md)<br/>
[Globální proměnné](../../atl/reference/atl-global-variables.md)<br/>
[Třídy a struktury](../../atl/reference/atl-classes.md)<br/>
[Makra](../../atl/reference/atl-macros.md)
