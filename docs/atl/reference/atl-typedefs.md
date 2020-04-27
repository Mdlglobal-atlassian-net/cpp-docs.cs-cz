---
title: Definice Typedef ATL
ms.date: 11/04/2016
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
helpviewer_keywords:
- typedefs, ATL
- typedefs
- ATL, typedefs
ms.assetid: 7dd05baa-3efb-4e3b-af23-793c610f4560
ms.openlocfilehash: 26e4e80ed3110351130731e6030427d25fc4a0ea
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168732"
---
# <a name="atl-typedefs"></a>Definice Typedef ATL

Knihovna aktivních šablon obsahuje následující definice typedef.

|||
|-|-|
|[_ATL_BASE_MODULE](#_atl_base_module)|Definováno jako definice typu na základě [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md).|
|[_ATL_COM_MODULE](#_atl_com_module)|Definováno jako definice typu na základě [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md).|
|[_ATL_MODULE](#_atl_module)|Definováno jako definice typu na základě [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md).|
|[_ATL_WIN_MODULE](#_atl_win_module)|Definováno jako definice typu na základě [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|
|[ATL_URL_PORT](#atl_url_port)|Typ použitý [oblým](../../atl/reference/curl-class.md) pro zadání čísla portu.|
|[CComDispatchDriver](#ccomdispatchdriver)|Tato třída spravuje ukazatele rozhraní modelu COM.|
|[CComGlobalsThreadModel](#ccomglobalsthreadmodel)|Volá příslušné metody modelu vlákna bez ohledu na použitý model vláken.|
|[CComObjectThreadModel](#ccomobjectthreadmodel)|Volá příslušné metody modelu vlákna bez ohledu na použitý model vláken.|
|[CContainedWindow](#ccontainedwindow)|Tato třída je specializací `CContainedWindowT`.|
|[CPath](#cpath)|Specializace [CPathT](../../atl/reference/cpatht-class.md) s využitím `CString`.|
|[CPathA](#cpatha)|Specializace [CPathT](../../atl/reference/cpatht-class.md) s využitím `CStringA`.|
|[CPathW](#cpathw)|Specializace [CPathT](../../atl/reference/cpatht-class.md) s využitím `CStringW`.|
|[CSimpleValArray](#csimplevalarray)|Představuje pole pro ukládání jednoduchých typů.|
|[DefaultThreadTraits](#defaultthreadtraits)|Výchozí třída vlastností vlákna.|
|[LPCURL](#lpcurl)|Ukazatel na konstantní objekt [složeného](../../atl/reference/curl-class.md) objektu.|
|[LPURL](#lpurl)|Ukazatel na objekt [složeného](../../atl/reference/curl-class.md) objektu.|

## <a name="_atl_base_module"></a><a name="_atl_base_module"></a>_ATL_BASE_MODULE

Definováno jako definice typu na základě _ATL_BASE_MODULE70.

```cpp
typedef ATL::_ATL_BASE_MODULE70 _ATL_BASE_MODULE;
```

### <a name="remarks"></a>Poznámky

Používá se v každém projektu ATL. Na základě [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md).

Třídy, které jsou součástí tříd modulů ATL 7,0, jsou odvozeny ze struktury _ATL_BASE_MODULE.  Další informace o třídách modulů ATL naleznete v tématu [třídy modulů COM](../../atl/com-modules-classes.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlcore. h

## <a name="_atl_com_module"></a><a name="_atl_com_module"></a>_ATL_COM_MODULE

Definováno jako definice typu na základě _ATL_COM_MODULE70.

```cpp
typedef ATL::_ATL_COM_MODULE70 _ATL_COM_MODULE;
```

### <a name="remarks"></a>Poznámky

Používá se v projektech ATL, které používají funkce COM. Na základě [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

## <a name="_atl_module"></a><a name="_atl_module"></a>_ATL_MODULE

Definováno jako definice typu na základě _ATL_MODULE70.

```cpp
typedef ATL::_ATL_MODULE70 _ATL_MODULE;
```

### <a name="requirements"></a>Požadavky

**Hlaviček**

### <a name="remarks"></a>Poznámky

Na základě [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md).

## <a name="_atl_win_module"></a><a name="_atl_win_module"></a>_ATL_WIN_MODULE

Definováno jako definice typu na základě _ATL_WIN_MODULE70.

```cpp
typedef ATL::_ATL_WIN_MODULE70 _ATL_WIN_MODULE;
```

### <a name="remarks"></a>Poznámky

Používá se v projektech ATL, které používají funkce pro okna. Na základě [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

## <a name="atl_url_port"></a><a name="atl_url_port"></a>ATL_URL_PORT

Typ použitý [oblým](curl-class.md) pro zadání čísla portu.

```cpp
typedef WORD ATL_URL_PORT;
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlutil. h

## <a name="ccomdispatchdriver"></a><a name="ccomdispatchdriver"></a>CComDispatchDriver

Tato třída spravuje ukazatele rozhraní modelu COM.

```cpp
typedef CComQIPtr<IDispatch, &__uuidof(IDispatch)> CComDispatchDriver;
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

## <a name="ccomglobalsthreadmodel"></a><a name="ccomglobalsthreadmodel"></a>CComGlobalsThreadModel

Volá příslušné metody modelu vlákna bez ohledu na použitý model vláken.

```cpp
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

V závislosti na modelu vláken, který používá vaše aplikace `CComGlobalsThreadModel` , název **typedef** odkazuje buď na [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) nebo [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Tyto třídy poskytují další `typedef` názvy pro odkazování na kritickou třídu oddílu.

> [!NOTE]
> `CComGlobalsThreadModel`neodkazuje na třídu [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).

Použití `CComGlobalsThreadModel` zadarmo vám umožní zadat konkrétní třídu modelu vláken. Bez ohledu na použitý model vláken se budou volat příslušné metody.

Kromě `CComGlobalsThreadModel`toho knihovna ATL poskytuje název **typedef** [CComObjectThreadModel](#ccomobjectthreadmodel). Třída, na kterou se `typedef` odkazuje, závisí na použitém modelu vláken, jak je znázorněno v následující tabulce:

| – definice typedef|Jednoduché dělení na vlákna|Dělení na vlákna|Bezplatné dělení na vlákna|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`; M =`CComMultiThreadModel`

Použijte `CComObjectThreadModel` v rámci jedné třídy objektu. Použijte `CComGlobalsThreadModel` v objektu, který je globálně dostupný pro váš program, nebo když chcete chránit prostředky modulů napříč více vlákny.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

## <a name="ccomobjectthreadmodel"></a><a name="ccomobjectthreadmodel"></a>CComObjectThreadModel

Volá příslušné metody modelu vlákna bez ohledu na použitý model vláken.

```cpp
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

V závislosti na modelu vláken používaném aplikací `typedef` se název `CComObjectThreadModel` odkazuje buď na [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) nebo [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Tyto třídy poskytují další `typedef` názvy pro odkazování na kritickou třídu oddílu.

> [!NOTE]
> `CComObjectThreadModel`neodkazuje na třídu [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).

Použití `CComObjectThreadModel` zadarmo vám umožní zadat konkrétní třídu modelu vláken. Bez ohledu na použitý model vláken se budou volat příslušné metody.

Kromě `CComObjectThreadModel`toho knihovna ATL poskytuje název **typedef** [CComGlobalsThreadModel](#ccomglobalsthreadmodel). Třída, na kterou odkazuje každý typ **typedef** , závisí na použitém modelu vláken, jak je znázorněno v následující tabulce:

| – definice typedef|Jednoduché dělení na vlákna|Dělení na vlákna|Bezplatné dělení na vlákna|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`; M =`CComMultiThreadModel`

Použijte `CComObjectThreadModel` v rámci jedné třídy objektu. Použijte `CComGlobalsThreadModel` v objektu, který je globálně k dispozici pro váš program, nebo pokud chcete chránit prostředky modulů napříč více vlákny.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

## <a name="ccontainedwindow"></a><a name="ccontainedwindow"></a>CContainedWindow

Tato třída je specializací `CContainedWindowT`.

```cpp
typedef CContainedWindowT<CWindow> CContainedWindow;
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin. h

### <a name="remarks"></a>Poznámky

`CContainedWindow`je specializací [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md). Pokud chcete změnit základní třídu nebo vlastnosti, použijte `CContainedWindowT` přímo.

## <a name="cpath"></a><a name="cpath"></a>CPath

Specializace [CPathT](../../atl/reference/cpatht-class.md) s využitím `CString`.

```cpp
typedef CPathT<CString> CPath;
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlpath. h

## <a name="cpatha"></a><a name="cpatha"></a>CPathA

Specializace [CPathT](../../atl/reference/cpatht-class.md) s využitím `CStringA`.

```cpp
typedef CPathT<CStringA> CPathA;
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlpath. h

## <a name="cpathw"></a><a name="cpathw"></a>CPathW

Specializace [CPathT](../../atl/reference/cpatht-class.md) s využitím `CStringW`.

```cpp
typedef ATL::CPathT<CStringW> CPathW;
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlpath. h

## <a name="csimplevalarray"></a><a name="csimplevalarray"></a>CSimpleValArray

Představuje pole pro ukládání jednoduchých typů.

```cpp
#define CSimpleValArray CSimpleArray
```

### <a name="remarks"></a>Poznámky

`CSimpleValArray`je k dispozici pro vytváření a správu polí obsahujících jednoduché datové typy. Jedná se o jednoduchou #define [CSimpleArray](../../atl/reference/csimplearray-class.md).

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlsimpcoll. h

## <a name="lpcurl"></a><a name="lpcurl"></a>LPCURL

Ukazatel na konstantní objekt [složeného](../../atl/reference/curl-class.md) objektu.

```cpp
typedef const CUrl* LPCURL;
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlutil. h

## <a name="defaultthreadtraits"></a><a name="defaultthreadtraits"></a>DefaultThreadTraits

Výchozí třída vlastností vlákna.

### <a name="syntax"></a>Syntaxe

```cpp
#if defined(_MT)
   typedef CRTThreadTraits DefaultThreadTraits;
#else
   typedef Win32ThreadTraits DefaultThreadTraits;
#endif
```

## <a name="remarks"></a>Poznámky

Pokud aktuální projekt používá vícevláknové CRT, DefaultThreadTraits je definováno jako CRTThreadTraits. V opačném případě se použije Win32ThreadTraits.

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

## <a name="lpurl"></a><a name="lpurl"></a>LPURL

Ukazatel na objekt [složeného](../../atl/reference/curl-class.md) objektu.

```cpp
typedef CUrl* LPURL;
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** atlutil. h

## <a name="see-also"></a>Viz také

[Desktopové komponenty ATL objektů COM](../../atl/atl-com-desktop-components.md)<br/>
[Functions](../../atl/reference/atl-functions.md)<br/>
[Globální proměnné](../../atl/reference/atl-global-variables.md)<br/>
[Třídy a struktury](../../atl/reference/atl-classes.md)<br/>
[Makra](../../atl/reference/atl-macros.md)
