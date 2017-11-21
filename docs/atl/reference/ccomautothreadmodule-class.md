---
title: "Třída CComAutoThreadModule | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
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
dev_langs: C++
helpviewer_keywords:
- CComAutoThreadModule class
- apartment model modules
ms.assetid: 13063ea5-a57e-4aac-97d3-227137262811
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d07a29ff12edcd590379f9bb30cdc122806a83c6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ccomautothreadmodule-class"></a>CComAutoThreadModule – třída
Od verze ATL 7.0 `CComAutoThreadModule` je zastaralá: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class ThreadAllocator = CComSimpleThreadAllocator>  
class CComAutoThreadModule : public CComModule
```  
  
#### <a name="parameters"></a>Parametry  
 `ThreadAllocator`  
 [v] Třída správy výběr přístup z více vláken. Výchozí hodnota je [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).  
  
## <a name="members"></a>Členové  
  
### <a name="methods"></a>Metody  
  
|||  
|-|-|  
|[CreateInstance –](#createinstance)|Vybere vlákna a potom vytvoří objekt přidružený typu apartment.|  
|[GetDefaultThreads](#getdefaultthreads)|(Statické) Dynamicky vypočítá počet vláken pro modul na základě počtu procesorů.|  
|[Init –](#init)|Vytvoří modulu vláken.|  
|[Zámek](#lock)|Zvětší počet zámku na modul a na aktuální vlákno.|  
|[Odemknutí](#unlock)|Snižuje počet zámek na modul a na aktuální vlákno.|  
  
### <a name="data-members"></a>Datové členy  
  
### <a name="data-members"></a>Datové členy  
  
|||  
|-|-|  
|[dwThreadID](#dwthreadid)|Obsahuje identifikátor aktuálního vlákna.|  
|[m_Allocator](#m_allocator)|Spravuje výběr přístup z více vláken.|  
|[m_nThreads](#m_nthreads)|Obsahuje počet vláken v modulu.|  
|[m_pApartments](#m_papartments)|Spravuje Apartment modulu.|  
  
## <a name="remarks"></a>Poznámky  
  
> [!NOTE]
>  Tato třída je zastaralá, s nahrazena [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) a [CAtlModule](../../atl/reference/catlmodule-class.md) odvozených třídách. Informace, které následuje je pro použití se staršími verzemi ATL.  
  
 `CComAutoThreadModule`odvozená z [CComModule](../../atl/reference/ccommodule-class.md) implementovat ve fondu vláken, apartment model server COM služeb souborů exe a systému Windows. `CComAutoThreadModule`používá [CComApartment](../../atl/reference/ccomapartment-class.md) ke správě izolovaný prostor pro každé vlákno v modulu.  
  
 Odvození modul z `CComAutoThreadModule` když chcete vytvořit objekty v několika Apartment. Musíte taky zahrnout [DECLARE_CLASSFACTORY_AUTO_THREAD](aggregation-and-class-factory-macros.md#declare_classfactory_auto_thread) makra v definici třídy objektu k určení [CComClassFactoryAutoThread](../../atl/reference/ccomclassfactoryautothread-class.md) jako objekt pro vytváření tříd.  
  
 Ve výchozím nastavení, odvodí objekty AppWizard ATL COM (Průvodce projektem knihovny ATL v sadě Visual Studio .NET) modul z `CComModule`. Chcete-li použít `CComAutoThreadModule`, upravte definici třídy. Příklad:  
  
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
 **Záhlaví:** atlbase.h  
  
##  <a name="createinstance"></a>CComAutoThreadModule::CreateInstance  
 Od verze ATL 7.0 `CComAutoThreadModule` je zastaralá: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
HRESULT CreateInstance(
    void* pfnCreateInstance,
    REFIID riid,
    void** ppvObj);
```  
  
### <a name="parameters"></a>Parametry  
 *pfnCreateInstance*  
 [v] Ukazatel na funkci creator.  
  
 `riid`  
 [v] Identifikátory IID požadované rozhraní.  
  
 `ppvObj`  
 [out] Ukazatel na ukazatel rozhraní identifikovaný `riid`. Pokud objekt nepodporuje toto rozhraní `ppvObj` je nastaven na hodnotu NULL.  
  
### <a name="return-value"></a>Návratová hodnota  
 Standardní hodnota HRESULT.  
  
### <a name="remarks"></a>Poznámky  
 Vybere vlákna a potom vytvoří objekt přidružený typu apartment.  
  
##  <a name="dwthreadid"></a>CComAutoThreadModule::dwThreadID  
 Od verze ATL 7.0 `CComAutoThreadModule` je zastaralá: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
DWORD dwThreadID;
```  
  
### <a name="remarks"></a>Poznámky  
 Obsahuje identifikátor aktuálního vlákna.  
  
##  <a name="getdefaultthreads"></a>CComAutoThreadModule::GetDefaultThreads  
 Od verze ATL 7.0 `CComAutoThreadModule` je zastaralá: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
static int GetDefaultThreads();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet podprocesů, které lze vytvořit v modulu EXE.  
  
### <a name="remarks"></a>Poznámky  
 Tato statická funkce dynamicky vypočítá maximální počet vláken pro modul EXE, na základě počtu procesorů. Ve výchozím nastavení, je předán tuto hodnotu [Init](#init) metodu pro vytvoření vláken.  
  
##  <a name="init"></a>CComAutoThreadModule::Init  
 Od verze ATL 7.0 `CComAutoThreadModule` je zastaralá: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
HRESULT Init(
    _ATL_OBJMAP_ENTRY* p,
    HINSTANCE h,
    const GUID* plibid = NULL,
    int nThreads = GetDefaultThreads());
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 [v] Ukazatel na pole položek mapování objektu.  
  
 `h`  
 [v] `HINSTANCE` Předaný **DLLMain** nebo `WinMain`.  
  
 `plibid`  
 [v] Ukazatel na ID KNIHOVNY knihovny typů, který je přidružený k projektu.  
  
 `nThreads`  
 [v] Počet vláken, který se má vytvořit. Ve výchozím nastavení `nThreads` je hodnoty vrácené [GetDefaultThreads](#getdefaultthreads).  
  
### <a name="remarks"></a>Poznámky  
 Datové členy inicializuje a vytvoří počet vláken určeného `nThreads`.  
  
##  <a name="lock"></a>CComAutoThreadModule::Lock  
 Od verze ATL 7.0 `CComAutoThreadModule` je zastaralá: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
LONG Lock();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota, která může být užitečné pro diagnostiku nebo testování.  
  
### <a name="remarks"></a>Poznámky  
 Provede atomic přírůstek počtu uzamčení pro modul a pro aktuální vlákno. `CComAutoThreadModule`Počet modulů zámku se používá k určení, zda všichni klienti přistupují k modulu. Počet zámku na aktuální vlákno se používá pro účely statistiky.  
  
##  <a name="m_allocator"></a>CComAutoThreadModule::m_Allocator  
 Od verze ATL 7.0 `CComAutoThreadModule` je zastaralá: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
ThreadAllocator  m_Allocator;
```     
  
### <a name="remarks"></a>Poznámky  
 Objekt správy výběr přístup z více vláken. Ve výchozím nastavení `ThreadAllocator` parametr šablony třídy je [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).  
  
##  <a name="m_nthreads"></a>CComAutoThreadModule::m_nThreads  
 Od verze ATL 7.0 `CComAutoThreadModule` je zastaralá: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
int m_nThreads;
```  
  
### <a name="remarks"></a>Poznámky  
 Obsahuje počet vláken v modulu EXE. Když [Init](#init) je volána, `m_nThreads` je nastaven na `nThreads` hodnotu parametru. Každé vlákno přidružené apartment spravuje [CComApartment](../../atl/reference/ccomapartment-class.md) objektu.  
  
##  <a name="m_papartments"></a>CComAutoThreadModule::m_pApartments  
 Od verze ATL 7.0 `CComAutoThreadModule` je zastaralá: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
CComApartment* m_pApartments;
```  
  
### <a name="remarks"></a>Poznámky  
 Odkazuje na pole [CComApartment](../../atl/reference/ccomapartment-class.md) objekty, z nichž každý spravuje typu apartment v modulu. Počet prvků v poli je založen na [m_nThreads](#m_nthreads) člen.  
  
##  <a name="unlock"></a>CComAutoThreadModule::Unlock  
 Od verze ATL 7.0 `CComAutoThreadModule` je zastaralá: najdete v části [ATL – třídy modulů](../../atl/atl-module-classes.md) další podrobnosti.  
  
```
LONG Unlock();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Hodnota, která může být užitečné pro diagnostiku nebo testování.  
  
### <a name="remarks"></a>Poznámky  
 Provede atomic snížení počtu uzamčení pro modul a pro aktuální vlákno. `CComAutoThreadModule`Počet modulů zámku se používá k určení, zda všichni klienti přistupují k modulu. Počet zámku na aktuální vlákno se používá pro účely statistiky.  
  
 Pokud počet modulů zámku hodnota nula, může být modul odpojen.  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [Třídy modulů](../../atl/atl-module-classes.md)
