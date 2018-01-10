---
title: "Třída CComMultiThreadModelNoCS | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComMultiThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS::AutoCriticalSection
- ATLBASE/ATL::CComMultiThreadModelNoCS::CriticalSection
- ATLBASE/ATL::CComMultiThreadModelNoCS::ThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS::Decrement
- ATLBASE/ATL::CComMultiThreadModelNoCS::Increment
dev_langs: C++
helpviewer_keywords:
- ATL, multithreading
- CComMultiThreadModelNoCS class
- threading [ATL]
ms.assetid: 2b3f7a45-fd72-452c-aaf3-ccdaa621c821
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: cc32ab53469b1f125b56343806c7920461c64bf2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="ccommultithreadmodelnocs-class"></a>CComMultiThreadModelNoCS – třída
`CComMultiThreadModelNoCS`poskytuje metody vláken pro zvyšování a dekrementace hodnotu proměnné, bez kritická sekce zamykání a odemykání funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CComMultiThreadModelNoCS
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|[CComMultiThreadModelNoCS::AutoCriticalSection](#autocriticalsection)|Odkazuje na třídu [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).|  
|[CComMultiThreadModelNoCS::CriticalSection](#criticalsection)|Odkazuje na třídu `CComFakeCriticalSection`.|  
|[CComMultiThreadModelNoCS::ThreadModelNoCS](#threadmodelnocs)|Odkazuje na třídu `CComMultiThreadModelNoCS`.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComMultiThreadModelNoCS::Decrement](#decrement)|(Statické) Sníží hodnotu zadanou proměnnou způsobem bezpečné pro přístup z více vláken.|  
|[CComMultiThreadModelNoCS::Increment](#increment)|(Statické) Zvýší hodnotu zadanou proměnnou způsobem bezpečné pro přístup z více vláken.|  
  
## <a name="remarks"></a>Poznámky  
 `CComMultiThreadModelNoCS`je podobná [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) v tom, že poskytuje metody vláken pro zvyšování a dekrementace proměnné. Ale při odkazu na třídu kritická sekce prostřednictvím `CComMultiThreadModelNoCS`, metody, jako `Lock` a `Unlock` se nic nestane.  
  
 Obvykle použijete, `CComMultiThreadModelNoCS` prostřednictvím `ThreadModelNoCS` `typedef` název. To `typedef` je definována v `CComMultiThreadModelNoCS`, `CComMultiThreadModel`, a [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md).  
  
> [!NOTE]
>  Na globální `typedef` názvy [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) a [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel) neodkazují na `CComMultiThreadModelNoCS`.  
  
 Kromě `ThreadModelNoCS`, `CComMultiThreadModelNoCS` definuje `AutoCriticalSection` a `CriticalSection`. Těchto dvou `typedef` názvy odkaz [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), který poskytuje prázdný metody, které jsou přidružené k získání a uvolněním kritická sekce.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
##  <a name="autocriticalsection"></a>CComMultiThreadModelNoCS::AutoCriticalSection  
 Při použití `CComMultiThreadModelNoCS`, `typedef` název `AutoCriticalSection` odkazuje na třídu [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).  
  
```
typedef CComFakeCriticalSection AutoCriticalSection;
```  
  
### <a name="remarks"></a>Poznámky  
 Protože `CComFakeCriticalSection` neposkytuje kritická sekce její metody Neprovádět žádnou akci.  
  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) a [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) také obsahovat definice pro `AutoCriticalSection`. Následující tabulka znázorňuje vztah mezi vláken třídy modelu a kritická sekce odkazuje `AutoCriticalSection`:  
  
|Třídy definované v|Odkazovaný – třída|  
|----------------------|----------------------|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
|`CComMultiThreadModel`|`CComAutoCriticalSection`|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
  
 Kromě `AutoCriticalSection`, můžete použít `typedef` název [CriticalSection](#criticalsection). Neměla by být zadána `AutoCriticalSection` v globální objekty nebo členy statických tříd, pokud chcete odstranit kód CRT spuštění.  
  
### <a name="example"></a>Příklad  
 V tématu [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).  
  
##  <a name="criticalsection"></a>CComMultiThreadModelNoCS::CriticalSection  
 Při použití `CComMultiThreadModelNoCS`, `typedef` název `CriticalSection` odkazuje na třídu [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).  
  
```
typedef CComFakeCriticalSection CriticalSection;
```  
  
### <a name="remarks"></a>Poznámky  
 Protože `CComFakeCriticalSection` neposkytuje kritická sekce její metody Neprovádět žádnou akci.  
  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) a [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) také obsahovat definice pro `CriticalSection`. Následující tabulka znázorňuje vztah mezi vláken třídy modelu a kritická sekce odkazuje `CriticalSection`:  
  
|Třídy definované v|Odkazovaný – třída|  
|----------------------|----------------------|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
|`CComMultiThreadModel`|`CComCriticalSection`|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
  
 Kromě `CriticalSection`, můžete použít `typedef` název `AutoCriticalSection`. Neměla by být zadána `AutoCriticalSection` v globální objekty nebo členy statických tříd, pokud chcete odstranit kód CRT spuštění.  
  
### <a name="example"></a>Příklad  
 V tématu [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).  
  
##  <a name="decrement"></a>CComMultiThreadModelNoCS::Decrement  
 Tato statická funkce volá funkci Win32 [InterlockedDecrement](http://msdn.microsoft.com/library/windows/desktop/ms683580), které sníží hodnotu proměnné, na kterou odkazuje `p`.  
  
```
static ULONG WINAPI Decrement(LPLONG p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 [v] Ukazatel na proměnnou se odečte.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud výsledkem snížení je 0, `Decrement` vrátí hodnotu 0. Pokud je výsledkem snížení nenulové, návratovou hodnotu jsou taky nenulové hodnoty, ale nemusí být roven výsledek snížení.  
  
### <a name="remarks"></a>Poznámky  
 **InterlockedDecrement** zabrání více než jedno vlákno současně pomocí této proměnné.  
  
##  <a name="increment"></a>CComMultiThreadModelNoCS::Increment  
 Tato statická funkce volá funkci Win32 [InterlockedIncrement](http://msdn.microsoft.com/library/windows/desktop/ms683614), což zvýší hodnotu proměnné, na kterou odkazuje `p`.  
  
```
static ULONG WINAPI Increment(LPLONG p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 [v] Ukazatel na proměnnou se zvýší.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud výsledek přírůstek je 0, **přírůstek** vrátí hodnotu 0. Pokud je výsledek přírůstku nenulové hodnoty, návratovou hodnotu je také nenulové hodnoty, ale nemusí být roven výsledek přírůstku.  
  
### <a name="remarks"></a>Poznámky  
 **InterlockedIncrement** zabrání více než jedno vlákno současně pomocí této proměnné.  
  
##  <a name="threadmodelnocs"></a>CComMultiThreadModelNoCS::ThreadModelNoCS  
 Při použití `CComMultiThreadModelNoCS`, `typedef` název `ThreadModelNoCS` jednoduše odkazuje `CComMultiThreadModelNoCS`.  
  
```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```  
  
### <a name="remarks"></a>Poznámky  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) a [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) také obsahovat definice pro `ThreadModelNoCS`. Následující tabulka znázorňuje vztah mezi vláken třídu modelu a třída odkazuje `ThreadModelNoCS`:  
  
|Třídy definované v|Odkazovaný – třída|  
|----------------------|----------------------|  
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|  
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|  
|`CComSingleThreadModel`|`CComSingleThreadModel`|  
  
 Všimněte si, že definice `ThreadModelNoCS` v `CComMultiThreadModelNoCS` poskytuje symetrie s `CComMultiThreadModel` a `CComSingleThreadModel`. Předpokládejme například, že ukázkový kód v `CComMultiThreadModel::AutoCriticalSection` deklarovaný následující `typedef`:  
  
 [!code-cpp[NVC_ATL_COM#37](../../atl/codesnippet/cpp/ccommultithreadmodelnocs-class_1.h)]  
  
 Bez ohledu na to Zadaná třída pro `ThreadModel` (například `CComMultiThreadModelNoCS`), `_ThreadModel` přeloží odpovídajícím způsobem.  
  
### <a name="example"></a>Příklad  
 V tématu [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)