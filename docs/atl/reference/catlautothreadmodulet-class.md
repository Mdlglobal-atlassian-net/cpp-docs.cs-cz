---
title: Catlautothreadmodulet – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: a54818b839f13ad9114274248cfdbfc74efa033a
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/06/2018
ms.locfileid: "37883070"
---
# <a name="catlautothreadmodulet-class"></a>Catlautothreadmodulet – třída
Tato třída poskytuje metody pro implementaci serveru ve fondu vláken, apartment model modelu COM.  
  
> [!IMPORTANT]
>  Tato třída a jejích členů nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.  
  
## <a name="syntax"></a>Syntaxe  
  
```
template <class T, 
         class ThreadAllocator = CComSimpleThreadAllocator,
         DWORD dwWait = INFINITE>  
class ATL_NO_VTABLE CAtlAutoThreadModuleT : public IAtlAutoThreadModule
```  
  
#### <a name="parameters"></a>Parametry  
 *T*  
 Třída, která implementuje serveru COM.  
  
 *ThreadAllocator*  
 Třídy správy výběr vlákna. Výchozí hodnota je [ccomsimplethreadallocator –](../../atl/reference/ccomsimplethreadallocator-class.md).  
  
 *dwWait*  
 Určuje interval časového limitu v milisekundách. Výchozí hodnota je NEKONEČNO, což znamená, že interval časového limitu metody nikdy vypaří.  
  
## <a name="members"></a>Členové  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CAtlAutoThreadModuleT::GetDefaultThreads](#getdefaultthreads)|Tato statická funkce dynamicky vypočítá a vrátí maximální počet vláken pro modul EXE, na základě počtu procesorů.|  
  
## <a name="remarks"></a>Poznámky  
 Třída [catlautothreadmodule –](../../atl/reference/catlautothreadmodule-class.md) je odvozena z `CAtlAutoThreadModuleT` kvůli implementaci ve fondu vláken, apartment model modelu COM serveru. Nahradí zastaralou třídu [CComAutoThreadModule](../../atl/reference/ccomautothreadmodule-class.md).  
  
> [!NOTE]
>  Tato třída by neměl v knihovně DLL použít jako výchozí *dwWait* hodnoty NEKONEČNÉ způsobí zablokování při uvolnění knihovny DLL.  
  
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
 Počet vláken v modulu souboru EXE.  
  
### <a name="remarks"></a>Poznámky  
 Potlačí tuto metodu, pokud chcete použít jinou metodu pro výpočet počtu vláken. Ve výchozím nastavení počet vláken vychází z počtu procesorů.  
  
## <a name="see-also"></a>Viz také  
 [Iatlautothreadmodule – třída](../../atl/reference/iatlautothreadmodule-class.md)   
 [Přehled tříd](../../atl/atl-class-overview.md)   
 [Iatlautothreadmodule – třída](../../atl/reference/iatlautothreadmodule-class.md)   
 [Třídy modulů](../../atl/atl-module-classes.md)
