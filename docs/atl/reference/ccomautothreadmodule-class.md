---
title: Třída CComAutoThreadModule
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
ms.openlocfilehash: 391354c5672cf15c0286491619a13c6005493cfa
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321070"
---
# <a name="ccomautothreadmodule-class"></a>Třída CComAutoThreadModule

Od ATL 7.0, `CComAutoThreadModule` je zastaralý: viz [třídy modulu ATL](../../atl/atl-module-classes.md) pro další podrobnosti.

> [!IMPORTANT]
> Tuto třídu a její členy nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class ThreadAllocator = CComSimpleThreadAllocator>
class CComAutoThreadModule : public CComModule
```

#### <a name="parameters"></a>Parametry

*ThreadAllocator*<br/>
[v] Třída spravující výběr podprocesu. Výchozí hodnota je [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Createinstance](#createinstance)|Vybere vlákno a potom vytvoří objekt v přidruženém apartment.|
|[GetDefaultVlákna](#getdefaultthreads)|(Statické) Dynamicky vypočítá počet vláken pro modul na základě počtu procesorů.|
|[Init](#init)|Vytvoří vlákna modulu.|
|[Zámek](#lock)|Zvýšení počet zámků na modulu a na aktuální vlákno.|
|[Odemknout](#unlock)|Sníží počet zámků v modulu a v aktuálním vlákně.|

### <a name="data-members"></a>Členové dat

### <a name="data-members"></a>Členové dat

|||
|-|-|
|[dwThreadID](#dwthreadid)|Obsahuje identifikátor aktuálního vlákna.|
|[m_Allocator](#m_allocator)|Spravuje výběr vláken.|
|[m_nThreads](#m_nthreads)|Obsahuje počet podprocesů v modulu.|
|[m_pApartments](#m_papartments)|Spravuje byty modulu.|

## <a name="remarks"></a>Poznámky

> [!NOTE]
> Tato třída je zastaralá, protože byla nahrazena odvozenými třídami [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) a [CAtlModule.](../../atl/reference/catlmodule-class.md) Následující informace jsou určeny pro použití se staršími verzemi atl.

`CComAutoThreadModule`odvozuje z [CComModule](../../atl/reference/ccommodule-class.md) k implementaci serveru COM sdružený vlákny, apartment-model pro EXEs a služby systému Windows. `CComAutoThreadModule`používá [CComApartment](../../atl/reference/ccomapartment-class.md) pro správu bytu pro každé vlákno v modulu.

Odvodit `CComAutoThreadModule` modul z, když chcete vytvořit objekty ve více bytech. Musíte také zahrnout [makro DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) v definici třídy objektu k určení [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) jako factory třídy.

Ve výchozím nastavení bude průvodce atl COM AppWizard (Atl Project Wizard `CComModule`v sadě Visual Studio .NET) odvodit váš modul z . Chcete-li použít `CComAutoThreadModule`, upravte definici třídy. Příklad:

[!code-cpp[NVC_ATL_AxHost#2](../../atl/codesnippet/cpp/ccomautothreadmodule-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[Modul CAtl](../../atl/reference/catlmodule-class.md)

`IAtlAutoThreadModule`

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[CAtlAutoThreadModuleT](../../atl/reference/catlautothreadmodulet-class.md)

[Modul CCom](../../atl/reference/ccommodule-class.md)

`CComAutoThreadModule`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="ccomautothreadmodulecreateinstance"></a><a name="createinstance"></a>CComAutoThreadModule::CreateInstance

Od ATL 7.0, `CComAutoThreadModule` je zastaralý: viz [třídy modulu ATL](../../atl/atl-module-classes.md) pro další podrobnosti.

```
HRESULT CreateInstance(
    void* pfnCreateInstance,
    REFIID riid,
    void** ppvObj);
```

### <a name="parameters"></a>Parametry

*pfnCreateInstance*<br/>
[v] Ukazatel na funkci tvůrce.

*riid řekl:*<br/>
[v] IID požadovanérozhraní.

*ppvObj*<br/>
[out] Ukazatel rozhraní určený *riid*. Pokud objekt nepodporuje toto rozhraní, *je hodnota ppvObj* nastavena na hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Vybere vlákno a potom vytvoří objekt v přidruženém apartment.

## <a name="ccomautothreadmoduledwthreadid"></a><a name="dwthreadid"></a>CComAutoThreadModule::dwThreadID

Od ATL 7.0, `CComAutoThreadModule` je zastaralý: viz [třídy modulu ATL](../../atl/atl-module-classes.md) pro další podrobnosti.

```
DWORD dwThreadID;
```

### <a name="remarks"></a>Poznámky

Obsahuje identifikátor aktuálního vlákna.

## <a name="ccomautothreadmodulegetdefaultthreads"></a><a name="getdefaultthreads"></a>CComAutoThreadModule::GetDefaultThreads

Od ATL 7.0, `CComAutoThreadModule` je zastaralý: viz [třídy modulu ATL](../../atl/atl-module-classes.md) pro další podrobnosti.

```
static int GetDefaultThreads();
```

### <a name="return-value"></a>Návratová hodnota

Počet podprocesů, které mají být vytvořeny v modulu EXE.

### <a name="remarks"></a>Poznámky

Tato statická funkce dynamicky vypočítá maximální počet vláken pro modul EXE na základě počtu procesorů. Ve výchozím nastavení je tato vrácená hodnota předána metodě [Init](#init) k vytvoření vláken.

## <a name="ccomautothreadmoduleinit"></a><a name="init"></a>CComAutoThreadModule::Init

Od ATL 7.0, `CComAutoThreadModule` je zastaralý: viz [třídy modulu ATL](../../atl/atl-module-classes.md) pro další podrobnosti.

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL,
    int nThreads = GetDefaultThreads());
```

### <a name="parameters"></a>Parametry

*P*<br/>
[v] Ukazatel na pole položek mapy objektů.

*H*<br/>
[v] HINSTANCE předánnebo `DLLMain` `WinMain`.

*plibid*<br/>
[v] Ukazatel na LIBID knihovny typů přidružené k projektu.

*nVlákna*<br/>
[v] Počet podprocesů, které mají být vytvořeny. Ve výchozím nastavení *nThreads* je hodnota vrácená [GetDefaultThreads](#getdefaultthreads).

### <a name="remarks"></a>Poznámky

Inicializuje datové členy a vytvoří počet vláken určených *nThreads*.

## <a name="ccomautothreadmodulelock"></a><a name="lock"></a>CComAutoThreadModule::Zámek

Od ATL 7.0, `CComAutoThreadModule` je zastaralý: viz [třídy modulu ATL](../../atl/atl-module-classes.md) pro další podrobnosti.

```
LONG Lock();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečná pro diagnostiku nebo testování.

### <a name="remarks"></a>Poznámky

Provede atomický přírůstek na počet zámků pro modul a pro aktuální vlákno. `CComAutoThreadModule`používá počet zámek modulu k určení, zda jsou všichni klienti přístup k modulu. Počet zámků v aktuálním vlákně se používá pro statistické účely.

## <a name="ccomautothreadmodulem_allocator"></a><a name="m_allocator"></a>CComAutoThreadModule::m_Allocator

Od ATL 7.0, `CComAutoThreadModule` je zastaralý: viz [třídy modulu ATL](../../atl/atl-module-classes.md) pro další podrobnosti.

```
ThreadAllocator  m_Allocator;
```

### <a name="remarks"></a>Poznámky

Objekt spravující výběr vlákna. Ve výchozím `ThreadAllocator` nastavení je parametr šablony třídy [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).

## <a name="ccomautothreadmodulem_nthreads"></a><a name="m_nthreads"></a>CComAutoThreadModule::m_nThreads

Od ATL 7.0, `CComAutoThreadModule` je zastaralý: viz [třídy modulu ATL](../../atl/atl-module-classes.md) pro další podrobnosti.

```
int m_nThreads;
```

### <a name="remarks"></a>Poznámky

Obsahuje počet podprocesů v modulu EXE. Při [Init](#init) je `m_nThreads` volána, je nastavena na hodnotu parametru *nThreads.* Přidružený apartment každého vlákna je spravován objektem [CComApartment.](../../atl/reference/ccomapartment-class.md)

## <a name="ccomautothreadmodulem_papartments"></a><a name="m_papartments"></a>CComAutoThreadModule::m_pApartments

Od ATL 7.0, `CComAutoThreadModule` je zastaralý: viz [třídy modulu ATL](../../atl/atl-module-classes.md) pro další podrobnosti.

```
CComApartment* m_pApartments;
```

### <a name="remarks"></a>Poznámky

Odkazuje na pole [CComApartment](../../atl/reference/ccomapartment-class.md) objekty, z nichž každý spravuje apartment v modulu. Počet prvků v poli je založen na [členu m_nThreads.](#m_nthreads)

## <a name="ccomautothreadmoduleunlock"></a><a name="unlock"></a>CComAutoThreadModule::Odemknout

Od ATL 7.0, `CComAutoThreadModule` je zastaralý: viz [třídy modulu ATL](../../atl/atl-module-classes.md) pro další podrobnosti.

```
LONG Unlock();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečná pro diagnostiku nebo testování.

### <a name="remarks"></a>Poznámky

Provede atomické snížení počtu zámků pro modul a pro aktuální vlákno. `CComAutoThreadModule`používá počet zámek modulu k určení, zda jsou všichni klienti přístup k modulu. Počet zámků v aktuálním vlákně se používá pro statistické účely.

Když počet zámků modulu dosáhne nuly, modul může být uvolněn.

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)<br/>
[Třídy modulů](../../atl/atl-module-classes.md)
