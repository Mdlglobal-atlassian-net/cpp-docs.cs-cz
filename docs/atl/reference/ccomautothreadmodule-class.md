---
title: Třídy CComAutoThreadModule | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CComAutoThreadModule class
- apartment model modules
ms.assetid: 13063ea5-a57e-4aac-97d3-227137262811
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 9e747386c37e760793ceaa0396f217304cbe621d
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022679"
---
# <a name="ccomautothreadmodule-class"></a>Ccomautothreadmodule – třída

Od verze ATL 7.0 `CComAutoThreadModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.

> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

## <a name="syntax"></a>Syntaxe

```
template <class ThreadAllocator = CComSimpleThreadAllocator>
class CComAutoThreadModule : public CComModule
```

#### <a name="parameters"></a>Parametry

*ThreadAllocator*<br/>
[in] Třídy správy výběr vlákna. Výchozí hodnota je [ccomsimplethreadallocator –](../../atl/reference/ccomsimplethreadallocator-class.md).

## <a name="members"></a>Členové

### <a name="methods"></a>Metody

|||
|-|-|
|[Funkci CreateInstance](#createinstance)|Vybere vlákna a poté vytvoří objekt v přidružené objektu apartment.|
|[GetDefaultThreads](#getdefaultthreads)|(Statické) Dynamicky vypočítá počet vláken pro modul na základě počtu procesorů.|
|[Init](#init)|Vytvoří vlákna modulu.|
|[Zámek](#lock)|Pak inkrementuje počet na modul a u aktuálního vlákna.|
|[Odemknutí](#unlock)|Dekrementuje počet zámků v modulu a u aktuálního vlákna.|

### <a name="data-members"></a>Datové členy

### <a name="data-members"></a>Datové členy

|||
|-|-|
|[dwThreadID](#dwthreadid)|Obsahuje identifikátor aktuálního vlákna.|
|[m_Allocator](#m_allocator)|Spravuje výběr vlákna.|
|[m_nThreads](#m_nthreads)|Obsahuje počet vláken v modulu.|
|[m_pApartments](#m_papartments)|Spravuje objekty apartment modulu.|

## <a name="remarks"></a>Poznámky

> [!NOTE]
>  Tato třída je zastaralá, s nahrazena [catlautothreadmodule –](../../atl/reference/catlautothreadmodule-class.md) a [catlmodule –](../../atl/reference/catlmodule-class.md) odvozené třídy. Informace, které následuje je pro použití se staršími verzemi sady ATL.

`CComAutoThreadModule` je odvozen od [ccommodule –](../../atl/reference/ccommodule-class.md) implementovat ve fondu vláken, apartment model modelu COM serveru služby souborů exe a Windows. `CComAutoThreadModule` používá [ccomapartment –](../../atl/reference/ccomapartment-class.md) ke správě typu apartment pro každé vlákno v modulu.

Odvození z modulu `CComAutoThreadModule` kdy budete chtít vytvořit objekty ve více objekty apartment. Je také nutné uvést [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) makra v definici třídy objektu k určení [ccomclassfactoryautothread –](../../atl/reference/ccomclassfactoryautothread-class.md) jako objekt pro vytváření tříd.

Standardně průvodcem AppWizard knihovny ATL modelu COM (Průvodce projektu knihovny ATL v sadě Visual Studio .NET) odvodí z modulu `CComModule`. Chcete-li použít `CComAutoThreadModule`, upravte definici třídy. Příklad:

[!code-cpp[NVC_ATL_AxHost#2](../../atl/codesnippet/cpp/ccomautothreadmodule-class_1.cpp)]

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[_ATL_MODULE](atl-typedefs.md#_atl_module)

[Catlmodule –](../../atl/reference/catlmodule-class.md)

`IAtlAutoThreadModule`

[CAtlModuleT](../../atl/reference/catlmodulet-class.md)

[Catlautothreadmodulet –](../../atl/reference/catlautothreadmodulet-class.md)

[Ccommodule –](../../atl/reference/ccommodule-class.md)

`CComAutoThreadModule`

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="createinstance"></a>  CComAutoThreadModule::CreateInstance

Od verze ATL 7.0 `CComAutoThreadModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.

```
HRESULT CreateInstance(
    void* pfnCreateInstance,
    REFIID riid,
    void** ppvObj);
```

### <a name="parameters"></a>Parametry

*pfnCreateInstance*<br/>
[in] Ukazatel na funkci Tvůrce.

*riid*<br/>
[in] Identifikátor IID požadované rozhraní.

*ppvObj*<br/>
[out] Ukazatel na ukazatel rozhraní, který je identifikován *riid*. Pokud objekt nepodporuje toto rozhraní *ppvObj* nastaven na hodnotu NULL.

### <a name="return-value"></a>Návratová hodnota

Standardní hodnoty HRESULT.

### <a name="remarks"></a>Poznámky

Vybere vlákna a poté vytvoří objekt v přidružené objektu apartment.

##  <a name="dwthreadid"></a>  CComAutoThreadModule::dwThreadID

Od verze ATL 7.0 `CComAutoThreadModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.

```
DWORD dwThreadID;
```

### <a name="remarks"></a>Poznámky

Obsahuje identifikátor aktuálního vlákna.

##  <a name="getdefaultthreads"></a>  CComAutoThreadModule::GetDefaultThreads

Od verze ATL 7.0 `CComAutoThreadModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.

```
static int GetDefaultThreads();
```

### <a name="return-value"></a>Návratová hodnota

Počet vláken v modulu souboru EXE.

### <a name="remarks"></a>Poznámky

Tato statická funkce dynamicky vypočítá maximální počet vláken pro modul EXE, na základě počtu procesorů. Ve výchozím nastavení, je předat tuto hodnotu [Init](#init) metodu pro vytvoření vlákna.

##  <a name="init"></a>  CComAutoThreadModule::Init

Od verze ATL 7.0 `CComAutoThreadModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.

```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL,
    int nThreads = GetDefaultThreads());
```

### <a name="parameters"></a>Parametry

*p*<br/>
[in] Ukazatel na pole položek mapování objektu.

*h*<br/>
[in] Předány HINSTANCE `DLLMain` nebo `WinMain`.

*plibid*<br/>
[in] Ukazatel na LIBID knihovnu typů, který je přidružený k projektu.

*nThreads*<br/>
[in] Počet vláken, který se má vytvořit. Ve výchozím nastavení *nThreads* je hodnoty vrácené [GetDefaultThreads](#getdefaultthreads).

### <a name="remarks"></a>Poznámky

Inicializuje datové členy a vytvoří počet vláken určené *nThreads*.

##  <a name="lock"></a>  CComAutoThreadModule::Lock

Od verze ATL 7.0 `CComAutoThreadModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.

```
LONG Lock();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečné pro diagnostiku a testování.

### <a name="remarks"></a>Poznámky

Provádí atomické přírůstek na počet zámků pro modul a pro aktuální vlákno. `CComAutoThreadModule` Počet zámků modulů se používá k určení, zda všichni klienti přistupují k modulu. Počet zámků pro aktuální vlákno je použít pro statistické účely.

##  <a name="m_allocator"></a>  CComAutoThreadModule::m_Allocator

Od verze ATL 7.0 `CComAutoThreadModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.

```
ThreadAllocator  m_Allocator;
```

### <a name="remarks"></a>Poznámky

Objekt správy výběr vlákna. Ve výchozím nastavení `ThreadAllocator` je parametr šablony třídy [ccomsimplethreadallocator –](../../atl/reference/ccomsimplethreadallocator-class.md).

##  <a name="m_nthreads"></a>  CComAutoThreadModule::m_nThreads

Od verze ATL 7.0 `CComAutoThreadModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.

```
int m_nThreads;
```

### <a name="remarks"></a>Poznámky

Obsahuje počet vláken v modulu souboru EXE. Když [Init](#init) se nazývá `m_nThreads` je nastavena na *nThreads* hodnotu parametru. Každé vlákno přidružené apartment spravuje [ccomapartment –](../../atl/reference/ccomapartment-class.md) objektu.

##  <a name="m_papartments"></a>  CComAutoThreadModule::m_pApartments

Od verze ATL 7.0 `CComAutoThreadModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.

```
CComApartment* m_pApartments;
```

### <a name="remarks"></a>Poznámky

Odkazuje na pole [ccomapartment –](../../atl/reference/ccomapartment-class.md) objektů, z nichž každý spravuje komplexu v modulu. Počet prvků v poli je založen na [m_nThreads](#m_nthreads) člena.

##  <a name="unlock"></a>  CComAutoThreadModule::Unlock

Od verze ATL 7.0 `CComAutoThreadModule` je zastaralý: naleznete v tématu [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.

```
LONG Unlock();
```

### <a name="return-value"></a>Návratová hodnota

Hodnota, která může být užitečné pro diagnostiku a testování.

### <a name="remarks"></a>Poznámky

Provádí atomické snížení počet zámků pro modul a pro aktuální vlákno. `CComAutoThreadModule` Počet zámků modulů se používá k určení, zda všichni klienti přistupují k modulu. Počet zámků pro aktuální vlákno je použít pro statistické účely.

Když počet zámků modulů dosáhne nuly, může být uvolněna modulu.

## <a name="see-also"></a>Viz také

[Přehled tříd](../../atl/atl-class-overview.md)<br/>
[Třídy modulů](../../atl/atl-module-classes.md)
