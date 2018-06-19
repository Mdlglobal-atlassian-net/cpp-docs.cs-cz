---
title: Třída CAtlAutoThreadModuleT | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT::GetDefaultThreads
dev_langs:
- C++
helpviewer_keywords:
- CAtlAutoThreadModuleT class
ms.assetid: ae1667c6-3fb8-47bc-b35d-9ea5e9896d7f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a012494365745d40d98c0f65ee9eff6b5e9502da
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32361415"
---
# <a name="catlautothreadmodulet-class"></a>CAtlAutoThreadModuleT – třída
Tato třída poskytuje metody pro implementaci serveru COM ve fondu vláken, apartment model.  
  
> [!IMPORTANT]
>  Tato třída a její členy nelze použít v aplikacích, které jsou spuštěny v prostředí Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T, 
         class ThreadAllocator = CComSimpleThreadAllocator,
         DWORD dwWait = INFINITE>  
class ATL_NO_VTABLE CAtlAutoThreadModuleT : public IAtlAutoThreadModule
```  
  
#### <a name="parameters"></a>Parametry  
 `T`  
 Třída, která bude implementovat COM server.  
  
 `ThreadAllocator`  
 Třída správy výběr přístup z více vláken. Výchozí hodnota je [CComSimpleThreadAllocator](../../atl/reference/ccomsimplethreadallocator-class.md).  
  
 `dwWait`  
 Určuje interval časového limitu v milisekundách. Výchozí hodnota je NEKONEČNO, to znamená interval časového limitu metoda nikdy po uplynutí předem.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlAutoThreadModuleT::GetDefaultThreads](#getdefaultthreads)|Tato statická funkce dynamicky vypočítá a vrátí maximální počet vláken pro modul EXE, na základě počtu procesorů.|  
  
## <a name="remarks"></a>Poznámky  
 Třída [CAtlAutoThreadModule](../../atl/reference/catlautothreadmodule-class.md) je odvozena z `CAtlAutoThreadModuleT` kvůli implementaci serveru COM ve fondu vláken, apartment model. Nahradí zastaralé třídy [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).  
  
> [!NOTE]
>  Tato třída by neměl být používány knihovny DLL, jako výchozí `dwWait` hodnotu NEKONEČNÉ způsobí zablokování, když knihovnu DLL je odpojen.  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `IAtlAutoThreadModule`  
  
 `CAtlAutoThreadModuleT`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
##  <a name="getdefaultthreads"></a>  CAtlAutoThreadModuleT::GetDefaultThreads  
 Tato statická funkce dynamicky vypočítá a vrátí maximální počet vláken pro modul EXE, na základě počtu procesorů.  
  
```
static int GetDefaultThreads();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Počet podprocesů, které lze vytvořit v modulu EXE.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu, pokud chcete použít jinou metodu pro výpočet počet vláken. Ve výchozím nastavení je počet vláken, podle počtu procesorů.  
  
## <a name="see-also"></a>Viz také  
 [IAtlAutoThreadModule – třída](../../atl/reference/iatlautothreadmodule-class.md)   
 [Přehled třídy](../../atl/atl-class-overview.md)   
 [IAtlAutoThreadModule – třída](../../atl/reference/iatlautothreadmodule-class.md)   
 [Třídy modulů](../../atl/atl-module-classes.md)
