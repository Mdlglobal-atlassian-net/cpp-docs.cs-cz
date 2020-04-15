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
ms.openlocfilehash: 5548bee36ac52dbd6add31241714b0404289be45
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81319186"
---
# <a name="atl-typedefs"></a>Definice Typedef ATL

Knihovna aktivních šablon obsahuje následující texty.

|||
|-|-|
|[_ATL_BASE_MODULE](#_atl_base_module)|Definováno jako typedef založené na [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md).|
|[_ATL_COM_MODULE](#_atl_com_module)|Definováno jako typedef založené na [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md).|
|[_ATL_MODULE](#_atl_module)|Definováno jako typedef založené na [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md).|
|[_ATL_WIN_MODULE](#_atl_win_module)|Definováno jako typedef založené na [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md)|
|[ATL_URL_PORT](#atl_url_port)|Typ používaný [CUrl](../../atl/reference/curl-class.md) pro určení čísla portu.|
|[CComDispatchDriver](#ccomdispatchdriver)|Tato třída spravuje ukazatele rozhraní COM.|
|[CComGlobalsThreadModel](#ccomglobalsthreadmodel)|Volá příslušné metody modelu vlákna, bez ohledu na model zřetězení, který se používá.|
|[Model ccomobjectthreadmodelu](#ccomobjectthreadmodel)|Volá příslušné metody modelu vlákna, bez ohledu na model zřetězení, který se používá.|
|[CContainedWindow](#ccontainedwindow)|Tato třída je specializací na `CContainedWindowT`.|
|[CPath](#cpath)|Specializace [CPathT](../../atl/reference/cpatht-class.md) pomocí `CString`.|
|[Cpatha](#cpatha)|Specializace [CPathT](../../atl/reference/cpatht-class.md) pomocí `CStringA`.|
|[CpathW](#cpathw)|Specializace [CPathT](../../atl/reference/cpatht-class.md) pomocí `CStringW`.|
|[CSimpleValArray](#csimplevalarray)|Představuje pole pro ukládání jednoduchých typů.|
|[Výchozí threadtraits](#defaultthreadtraits)|Výchozí vlastnosti vlákna třídy.|
|[LPCURL](#lpcurl)|Ukazatel na konstantní [CUrl](../../atl/reference/curl-class.md) objektu.|
|[LPURL](#lpurl)|Ukazatel na [curl](../../atl/reference/curl-class.md) objekt.|

## <a name="_atl_base_module"></a><a name="_atl_base_module"></a>_ATL_BASE_MODULE

Definováno jako typedef založené na _ATL_BASE_MODULE70.

```
typedef ATL::_ATL_BASE_MODULE70 _ATL_BASE_MODULE;
```

### <a name="remarks"></a>Poznámky

Používá se v každém projektu ATL. Na základě [_ATL_BASE_MODULE70](../../atl/reference/atl-base-module70-structure.md).

Třídy, které jsou součástí tříd modulu ATL 7.0 odvozené z _ATL_BASE_MODULE struktury.  Další informace o třídách modulů ATL naleznete v centru [VIZ Třídy modulů COM](../../atl/com-modules-classes.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlcore.h

## <a name="_atl_com_module"></a><a name="_atl_com_module"></a>_ATL_COM_MODULE

Definováno jako typedef založené na _ATL_COM_MODULE70.

```
typedef ATL::_ATL_COM_MODULE70 _ATL_COM_MODULE;
```

### <a name="remarks"></a>Poznámky

Používá atl projekty, které používají funkce COM. Na základě [_ATL_COM_MODULE70](../../atl/reference/atl-com-module70-structure.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="_atl_module"></a><a name="_atl_module"></a>_ATL_MODULE

Definováno jako typedef založené na _ATL_MODULE70.

```
typedef ATL::_ATL_MODULE70 _ATL_MODULE;
```

## <a name="requirements"></a>Požadavky

**Záhlaví:**

### <a name="remarks"></a>Poznámky

Na základě [_ATL_MODULE70](../../atl/reference/atl-module70-structure.md).

## <a name="_atl_win_module"></a><a name="_atl_win_module"></a>_ATL_WIN_MODULE

Definováno jako typedef založené na _ATL_WIN_MODULE70.

```
typedef ATL::_ATL_WIN_MODULE70 _ATL_WIN_MODULE;
```

### <a name="remarks"></a>Poznámky

Používá se všemi projekty ATL, které používají funkce okna. Na základě [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="atl_url_port"></a><a name="atl_url_port"></a>ATL_URL_PORT

Typ používaný [CUrl](curl-class.md) pro určení čísla portu.

```
typedef WORD ATL_URL_PORT;
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlutil.h

## <a name="ccomdispatchdriver"></a><a name="ccomdispatchdriver"></a>CComDispatchDriver

Tato třída spravuje ukazatele rozhraní COM.

```
typedef CComQIPtr<IDispatch, &__uuidof(IDispatch)> CComDispatchDriver;
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="ccomglobalsthreadmodel"></a><a name="ccomglobalsthreadmodel"></a>CComGlobalsThreadModel

Volá příslušné metody modelu vlákna, bez ohledu na model zřetězení, který se používá.

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

V závislosti na modelu podprocesů používaném vaší `CComGlobalsThreadModel` aplikací odkazuje **název typedef** buď [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) nebo [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Tyto třídy `typedef` poskytují další názvy pro odkaz na třídu kritického oddílu.

> [!NOTE]
> `CComGlobalsThreadModel`neodkazuje na třídu [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).

Použití `CComGlobalsThreadModel` vás osvobodí od určení určité třídy modelu zřetězení. Bez ohledu na model zřetězení, který se používá, budou volány příslušné metody.

Kromě `CComGlobalsThreadModel`, ATL poskytuje **typedef** název [CComObjectThreadModel](#ccomobjectthreadmodel). Třída, na kterou `typedef` každý odkazuje, závisí na použitém modelu závitování, jak je znázorněno v následující tabulce:

| – definice typedef|Jedno závitování|Apartment threading|Volné závitování|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S `CComSingleThreadModel`= ; M=`CComMultiThreadModel`

Použití `CComObjectThreadModel` v rámci jedné třídy objektu. Použijte `CComGlobalsThreadModel` v objektu, který je globálně k dispozici pro váš program, nebo pokud chcete chránit prostředky modulu ve více vláknech.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="ccomobjectthreadmodel"></a><a name="ccomobjectthreadmodel"></a>Model ccomobjectthreadmodelu

Volá příslušné metody modelu vlákna, bez ohledu na model zřetězení, který se používá.

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

V závislosti na modelu podprocesu `typedef` používaného vaší aplikací název `CComObjectThreadModel` odkazuje buď [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) nebo [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md). Tyto třídy `typedef` poskytují další názvy pro odkaz na třídu kritického oddílu.

> [!NOTE]
> `CComObjectThreadModel`neodkazuje na třídu [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).

Použití `CComObjectThreadModel` vás osvobodí od určení určité třídy modelu zřetězení. Bez ohledu na model zřetězení, který se používá, budou volány příslušné metody.

Kromě `CComObjectThreadModel`, ATL poskytuje **typedef** název [CComGlobalsThreadModel](#ccomglobalsthreadmodel). Třída, na kterou odkazuje každý **typedef,** závisí na použitém modelu zřetězení, jak je znázorněno v následující tabulce:

| – definice typedef|Jedno závitování|Apartment threading|Volné závitování|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S `CComSingleThreadModel`= ; M=`CComMultiThreadModel`

Použití `CComObjectThreadModel` v rámci jedné třídy objektu. Použijte `CComGlobalsThreadModel` v objektu, který je buď globálně k dispozici pro váš program, nebo pokud chcete chránit prostředky modulu ve více vláknech.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="ccontainedwindow"></a><a name="ccontainedwindow"></a>CContainedWindow

Tato třída je specializací na `CContainedWindowT`.

```
typedef CContainedWindowT<CWindow> CContainedWindow;
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlwin.h

### <a name="remarks"></a>Poznámky

`CContainedWindow`je specializace [CContainedWindowT](../../atl/reference/ccontainedwindowt-class.md). Pokud chcete změnit základní třídu nebo `CContainedWindowT` vlastnosti, použijte přímo.

## <a name="cpath"></a><a name="cpath"></a>CPath

Specializace [CPathT](../../atl/reference/cpatht-class.md) pomocí `CString`.

```
typedef CPathT<CString> CPath;
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlpath.h

## <a name="cpatha"></a><a name="cpatha"></a>Cpatha

Specializace [CPathT](../../atl/reference/cpatht-class.md) pomocí `CStringA`.

```
typedef CPathT<CStringA> CPathA;
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlpath.h

## <a name="cpathw"></a><a name="cpathw"></a>CpathW

Specializace [CPathT](../../atl/reference/cpatht-class.md) pomocí `CStringW`.

```
typedef ATL::CPathT<CStringW> CPathW;
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlpath.h

## <a name="csimplevalarray"></a><a name="csimplevalarray"></a>CSimpleValArray

Představuje pole pro ukládání jednoduchých typů.

```
#define CSimpleValArray CSimpleArray
```

### <a name="remarks"></a>Poznámky

`CSimpleValArray`je k dispozici pro vytváření a správu polí obsahujících jednoduché datové typy. Jedná se o jednoduchý #define [CSimpleArray](../../atl/reference/csimplearray-class.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlsimpcoll.h

## <a name="lpcurl"></a><a name="lpcurl"></a>LPCURL

Ukazatel na konstantní [CUrl](../../atl/reference/curl-class.md) objektu.

```
typedef const CUrl* LPCURL;
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlutil.h

## <a name="defaultthreadtraits"></a><a name="defaultthreadtraits"></a>Výchozí threadtraits

Výchozí vlastnosti vlákna třídy.

### <a name="syntax"></a>Syntaxe

```
#if defined(_MT)
   typedef CRTThreadTraits DefaultThreadTraits;
#else
   typedef Win32ThreadTraits DefaultThreadTraits;
#endif
```

## <a name="remarks"></a>Poznámky

Pokud aktuální projekt používá vícevláknové CRT, DefaultThreadTraits je definován jako CRTThreadTraits. V opačném případě se používá Win32ThreadTraits.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="lpurl"></a><a name="lpurl"></a>LPURL

Ukazatel na [curl](../../atl/reference/curl-class.md) objekt.

```
typedef CUrl* LPURL;
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlutil.h

## <a name="see-also"></a>Viz také

[Desktopové komponenty ATL objektů COM](../../atl/atl-com-desktop-components.md)<br/>
[Functions](../../atl/reference/atl-functions.md)<br/>
[Globální proměnné](../../atl/reference/atl-global-variables.md)<br/>
[Třídy a struktury](../../atl/reference/atl-classes.md)<br/>
[Makra](../../atl/reference/atl-macros.md)
