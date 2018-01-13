---
title: "Třída CAtlAutoThreadModuleT | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT
- ATLBASE/ATL::CAtlAutoThreadModuleT::GetDefaultThreads
dev_langs: C++
helpviewer_keywords: CAtlAutoThreadModuleT class
ms.assetid: ae1667c6-3fb8-47bc-b35d-9ea5e9896d7f
caps.latest.revision: "20"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 082214794b2caa66e8be1127c664e0ffec18a394
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
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
  
##  <a name="getdefaultthreads"></a>CAtlAutoThreadModuleT::GetDefaultThreads  
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
