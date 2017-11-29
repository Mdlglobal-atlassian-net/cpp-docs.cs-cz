---
title: "Třída CComSingleThreadModel | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel::AutoCriticalSection
- ATLBASE/ATL::CComSingleThreadModel::CriticalSection
- ATLBASE/ATL::CComSingleThreadModel::ThreadModelNoCS
- ATLBASE/ATL::CComSingleThreadModel::Decrement
- ATLBASE/ATL::CComSingleThreadModel::Increment
dev_langs: C++
helpviewer_keywords:
- single-threaded applications
- CComSingleThreadModel class
- single-threaded applications, ATL
ms.assetid: e5dc30c7-405a-4ba4-8ae9-51937243fce8
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 65af9492f3721fd642def72a3049552cdff75ce6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ccomsinglethreadmodel-class"></a>CComSingleThreadModel – třída
Tato třída poskytuje metody pro zvyšování a dekrementace hodnotu proměnné.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CComSingleThreadModel
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|[CComSingleThreadModel::AutoCriticalSection](#autocriticalsection)|Odkazuje na třídu [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).|  
|[CComSingleThreadModel::CriticalSection](#criticalsection)|Odkazuje na třídu `CComFakeCriticalSection`.|  
|[CComSingleThreadModel::ThreadModelNoCS](#threadmodelnocs)|Odkazy na `CComSingleThreadModel`.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComSingleThreadModel::Decrement](#decrement)|Sníží hodnotu zadanou proměnnou. Tato implementace není bezpečné pro přístup z více vláken.|  
|[CComSingleThreadModel::Increment](#increment)|Zvýší hodnotu zadanou proměnnou. Tato implementace není bezpečné pro přístup z více vláken.|  
  
## <a name="remarks"></a>Poznámky  
 `CComSingleThreadModel`poskytuje metody pro zvyšování a dekrementace hodnotu proměnné. Na rozdíl od [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) a [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md), tyto metody nejsou bezpečné pro přístup z více vláken.  

 Obvykle použijete, `CComSingleThreadModel` prostřednictvím jednoho ze dvou `typedef` názvy buď [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) nebo [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel). Třída odkazuje každý `typedef` závisí na model vláken používaný, jak je znázorněno v následující tabulce:  

  
|– definice typedef|Jeden model vláken|Model vláken typu Apartment|Bezplatná model vláken|  
|-------------|----------------------------|-------------------------------|--------------------------|  
|`CComObjectThreadModel`|S|S|M|  
|`CComGlobalsThreadModel`|S|M|M|  
  
 S = `CComSingleThreadModel`; M =`CComMultiThreadModel`  
  
 `CComSingleThreadModel`samotný definuje tři `typedef` názvy. `ThreadModelNoCS`odkazy na `CComSingleThreadModel`. `AutoCriticalSection`a `CriticalSection` referenční třídy [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), který poskytuje prázdný metody, které jsou přidružené k získání a uvolněním vlastnictví kritická sekce.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
##  <a name="autocriticalsection"></a>CComSingleThreadModel::AutoCriticalSection  
 Při použití `CComSingleThreadModel`, `typedef` název `AutoCriticalSection` odkazuje na třídu [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).  
  
```
typedef CComFakeCriticalSection AutoCriticalSection;
```  
  
### <a name="remarks"></a>Poznámky  
 Protože `CComFakeCriticalSection` neposkytuje kritická sekce její metody Neprovádět žádnou akci.  
  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) a [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) obsahovat definice pro `AutoCriticalSection`. Následující tabulka znázorňuje vztah mezi vláken třídy modelu a kritická sekce odkazuje `AutoCriticalSection`:  
  
|Třídy definované v|Odkazovaný – třída|  
|----------------------|----------------------|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
|`CComMultiThreadModel`|`CComAutoCriticalSection`|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
  
 Kromě `AutoCriticalSection`, můžete použít `typedef` název [CriticalSection](#criticalsection). Neměla by být zadána `AutoCriticalSection` v globální objekty nebo členy statických tříd, pokud chcete odstranit kód CRT spuštění.  
  
### <a name="example"></a>Příklad  
 V tématu [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).  
  
##  <a name="criticalsection"></a>CComSingleThreadModel::CriticalSection  
 Při použití `CComSingleThreadModel`, `typedef` název `CriticalSection` odkazuje na třídu [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).  
  
```
typedef CComFakeCriticalSection CriticalSection;
```  
  
### <a name="remarks"></a>Poznámky  
 Protože `CComFakeCriticalSection` neposkytuje kritická sekce její metody Neprovádět žádnou akci.  
  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) a [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) obsahovat definice pro `CriticalSection`. Následující tabulka znázorňuje vztah mezi vláken třídy modelu a kritická sekce odkazuje `CriticalSection`:  
  
|Třídy definované v|Odkazovaný – třída|  
|----------------------|----------------------|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
|`CComMultiThreadModel`|`CComCriticalSection`|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
  
 Kromě `CriticalSection`, můžete použít `typedef` název [AutoCriticalSection](#autocriticalsection). Neměla by být zadána `AutoCriticalSection` v globální objekty nebo členy statických tříd, pokud chcete odstranit kód CRT spuštění.  
  
### <a name="example"></a>Příklad  
 V tématu [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).  
  
##  <a name="decrement"></a>CComSingleThreadModel::Decrement  
 Tato statická funkce sníží hodnotu proměnné, na kterou odkazuje `p`.  
  
```
static ULONG WINAPI Decrement(LPLONG p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 [v] Ukazatel na proměnnou se odečte.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výsledek snížení.  
  
##  <a name="increment"></a>CComSingleThreadModel::Increment  
 Tato statická funkce sníží hodnotu proměnné, na kterou odkazuje `p`.  
  
```
static ULONG WINAPI Increment(LPLONG p) throw();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 [v] Ukazatel na proměnnou se zvýší.  
  
### <a name="return-value"></a>Návratová hodnota  
 Výsledek přírůstku.  
  
##  <a name="threadmodelnocs"></a>CComSingleThreadModel::ThreadModelNoCS  
 Při použití `CComSingleThreadModel`, `typedef` název `ThreadModelNoCS` jednoduše odkazuje `CComSingleThreadModel`.  
  
```
typedef CComSingleThreadModel ThreadModelNoCS;
```  
  
### <a name="remarks"></a>Poznámky  
 [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) a [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) obsahovat definice pro `ThreadModelNoCS`. Následující tabulka znázorňuje vztah mezi vláken třídu modelu a třída odkazuje `ThreadModelNoCS`:  
  
|Třídy definované v|Odkazovaný – třída|  
|----------------------|----------------------|  
|`CComSingleThreadModel`|`CComSingleThreadModel`|  
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|  
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|  
  
### <a name="example"></a>Příklad  
 V tématu [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).  
  
## <a name="see-also"></a>Viz také  
 [Přehled třídy](../../atl/atl-class-overview.md)