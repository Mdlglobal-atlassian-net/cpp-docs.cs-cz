---
title: CComAutoThreadModule – třída
ms.date: 11/04/2016
f1_keywords:
- CComAutoThreadModule
- ATLBASE/ATL::CComAutoThreadModule
- ATLBASE/ATL::CreateInstance
- ATLBASE/ATL::GetDefaultThreads
- ATLBASE/ATL::Init
- ATLBASE/ATL::Lock
- ATLBASE/ATL::Unlock
- ATLBASE/ATL::dwThreadID
- ATLBASE/ATL::m_Allocator
- ATLBASE/ATL::m_nThreads
- ATLBASE/ATL::m_pApartments
helpviewer_keywords:
- CComAutoThreadModule class
- apartment model modules
ms.assetid: 13063ea5-a57e-4aac-97d3-227137262811
ms.openlocfilehash: 9b0fa685bf9a7de94b158bd62b00161c1b58562d
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79417920"
---
# <a name="ccomautothreadmodule-class"></a>CComAutoThreadModule – třída

Od ATL 7,0 je `CComAutoThreadModule` zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

> [!IMPORTANT]
>  Tato třída a její členové nelze použít v aplikacích, které jsou spouštěny v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class ThreadAllocator = CComSimpleThreadAllocator>
class CComAutoThreadModule : public CComModule
```

#### <a name="parameters"></a>Parametry

*ThreadAllocator*<br/>
pro Třída, která spravuje výběr vlákna. Výchozí hodnota je [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Metoda](#createinstance)|Vybere vlákno a následně vytvoří objekt v přidruženém objektu apartment.|
|[GetDefaultThreads](#getdefaultthreads)|Tras Dynamicky vypočítá počet vláken pro modul na základě počtu procesorů.|
|[Init](#init)|Vytvoří vlákna modulu.|
|[Získáte](#lock)|Zvýší počet zámků v modulu a v aktuálním vlákně.|
|[Uzamknout](#unlock)|Sníží počet zámků v modulu a v aktuálním vlákně.|

### <a name="data-members"></a>Datové členy

### <a name="data-members"></a>Datové členy

|||
|-|-|
|[dwThreadID](#dwthreadid)|Obsahuje identifikátor aktuálního vlákna.|
|[m_Allocator](#m_allocator)|Spravuje výběr vlákna.|
|[m_nThreads](#m_nthreads)|Obsahuje počet vláken v modulu.|
|[m_pApartments](#m_papartments)|Spravuje objekty Apartment modulu.|

## <a name="remarks"></a>Poznámky

> [!NOTE]
>  Tato třída je zastaralá a byla nahrazena odvozenými třídami [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) a [CAtlModule](../../atl/reference/catlmodule-class.md) . Níže uvedené informace jsou pro použití se staršími verzemi knihovny ATL.

`CComAutoThreadModule` je odvozena od [CComModule](../../atl/reference/ccommodule-class.md) k implementaci serveru COM ve fondu vláken pro exe a služby systému Windows. `CComAutoThreadModule` používá [CComApartment](../../atl/reference/ccomapartment-class.md) ke správě izolovaného prostoru pro každé vlákno v modulu.

Odvodit modul z `CComAutoThreadModule`, pokud chcete vytvořit objekty ve více objektech Apartment. Musíte také zahrnout makro [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) do definice třídy vašeho objektu pro určení [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) jako objektu pro vytváření tříd.

Ve výchozím nastavení bude AppWizard ATL COM (Průvodce projekty ATL v aplikaci Visual Studio .NET) odvodit váš modul od `CComModule`. Chcete-li použít `CComAutoThreadModule`, upravte definici třídy. Příklad:

[!code-cpp[NVC_ATL_AxHost#2](../../atl/codesnippet/cpp/ccomautothreadmodule-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[CAtlModule](../../atl/reference/catlmodule-class.md)

`IAtlAutoThreadModule`

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)

[CComModule](../../atl/reference/ccommodule-class.md)

`CComAutoThreadModule`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

##  <a name="createinstance"></a>CComAutoThreadModule:: CreateInstance

Od ATL 7,0 je `CComAutoThreadModule` zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

```
HRESULT CreateInstance(
    void* pfnCreateInstance,
    REFIID riid,
    void** ppvObj);
```

### <a name="parameters"></a>Parametry

*pfnCreateInstance*<br/>
pro Ukazatel na funkci Creator.

*riid*<br/>
pro IID požadovaného rozhraní.

*ppvObj*<br/>
mimo Ukazatel na ukazatel rozhraní identifikovaný *riid*. Pokud objekt nepodporuje toto rozhraní, je *ppvObj* nastaveno na hodnotu null.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Vybere vlákno a následně vytvoří objekt v přidruženém objektu apartment.

##  <a name="dwthreadid"></a>CComAutoThreadModule::d wThreadID

Od ATL 7,0 je `CComAutoThreadModule` zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

```
DWORD dwThreadID;
```

### <a name="remarks"></a>Poznámky

Obsahuje identifikátor aktuálního vlákna.

##  <a name="getdefaultthreads"></a>CComAutoThreadModule::GetDefaultThreads

Od ATL 7,0 je `CComAutoThreadModule` zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

```
static int GetDefaultThreads();
```

### <a name="return-value"></a>Návratová hodnota

Počet vláken, která mají být vytvořena v modulu EXE.

### <a name="remarks"></a>Poznámky

Tato statická funkce dynamicky vypočítá maximální počet vláken pro modul EXE na základě počtu procesorů. Ve výchozím nastavení je tato návratová hodnota předána metodě [init](#init) pro vytvoření vlákna.

##  <a name="init"></a>CComAutoThreadModule:: init

Od ATL 7,0 je `CComAutoThreadModule` zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL,
    int nThreads = GetDefaultThreads());
```

### <a name="parameters"></a>Parametry

*trub*<br/>
pro Ukazatel na pole položek mapy objektů.

*y*<br/>
pro HINSTANCE předaný do `DLLMain` nebo `WinMain`.

*plibid*<br/>
pro Ukazatel na LIBID knihovny typů přidružené k projektu.

*nThreads*<br/>
pro Počet vláken, která mají být vytvořena. Ve výchozím nastavení je *nThreads* hodnotou vrácenou [GetDefaultThreads](#getdefaultthreads).

### <a name="remarks"></a>Poznámky

Inicializuje datové členy a vytvoří počet vláken určených parametrem *nThreads*.

##  <a name="lock"></a>CComAutoThreadModule:: Lock

Od ATL 7,0 je `CComAutoThreadModule` zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

```
LONG Lock();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečná pro diagnostiku nebo testování.

### <a name="remarks"></a>Poznámky

Provede atomické zvýšení počtu zámků pro modul a pro aktuální vlákno. `CComAutoThreadModule` používá počet zámků modulu k určení, jestli klienti přistupují k modulu. Počet zámků aktuálního vlákna se používá ke statistickým účelům.

##  <a name="m_allocator"></a>CComAutoThreadModule:: m_Allocator

Od ATL 7,0 je `CComAutoThreadModule` zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

```
ThreadAllocator  m_Allocator;
```

### <a name="remarks"></a>Poznámky

Objekt, který spravuje výběr vlákna. Ve výchozím nastavení je parametr šablony `ThreadAllocator` třídy [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

##  <a name="m_nthreads"></a>CComAutoThreadModule:: m_nThreads

Od ATL 7,0 je `CComAutoThreadModule` zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

```
int m_nThreads;
```

### <a name="remarks"></a>Poznámky

Obsahuje počet vláken v modulu EXE. Při volání metody [init](#init) je `m_nThreads` nastavena na hodnotu parametru *nThreads* . Objekt Apartment každého vlákna je spravován objektem [CComApartment](../../atl/reference/ccomapartment-class.md) .

##  <a name="m_papartments"></a>CComAutoThreadModule:: m_pApartments

Od ATL 7,0 je `CComAutoThreadModule` zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

```
CComApartment* m_pApartments;
```

### <a name="remarks"></a>Poznámky

Odkazuje na pole objektů [CComApartment](../../atl/reference/ccomapartment-class.md) , z nichž každá spravuje objekt Apartment v modulu. Počet elementů v poli je založen na členu [m_nThreads](#m_nthreads) .

##  <a name="unlock"></a>CComAutoThreadModule:: Unlock

Od ATL 7,0 je `CComAutoThreadModule` zastaralé: Další informace naleznete v tématu [třídy modulů ATL](../../atl/atl-module-classes.md) .

```
LONG Unlock();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečná pro diagnostiku nebo testování.

### <a name="remarks"></a>Poznámky

Provede atomické snížení počtu zámků pro modul a pro aktuální vlákno. `CComAutoThreadModule` používá počet zámků modulu k určení, jestli klienti přistupují k modulu. Počet zámků aktuálního vlákna se používá ke statistickým účelům.

Když počet zámků modulu dosáhne nuly, může být modul uvolněn.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Třídy modulů](../../atl/atl-module-classes.md)
