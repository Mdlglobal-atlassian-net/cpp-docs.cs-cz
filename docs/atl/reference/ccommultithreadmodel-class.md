---
title: Třída CComMultiThreadModel | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComMultiThreadModel
- ATLBASE/ATL::CComMultiThreadModel
- ATLBASE/ATL::CComMultiThreadModel::AutoCriticalSection
- ATLBASE/ATL::CComMultiThreadModel::CriticalSection
- ATLBASE/ATL::CComMultiThreadModel::ThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModel::Decrement
- ATLBASE/ATL::CComMultiThreadModel::Increment
dev_langs:
- C++
helpviewer_keywords:
- ATL, multithreading
- CComMultiThreadModel class
- threading [ATL]
ms.assetid: db8f1662-2f7a-44b3-b341-ffbfb6e422a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a89af8507150ee708ad381be2d47201c9266f763
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ccommultithreadmodel-class"></a>CComMultiThreadModel – třída
`CComMultiThreadModel` poskytuje metody vláken pro zvyšování a dekrementace hodnotu proměnné.  
  
## <a name="syntax"></a>Syntaxe  
  
```
class CComMultiThreadModel
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-typedefs"></a>Veřejné – definice TypeDef  
  
|Název|Popis|  
|----------|-----------------|  
|[CComMultiThreadModel::AutoCriticalSection](#autocriticalsection)|Odkazuje na třídu [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md).|  
|[CComMultiThreadModel::CriticalSection](#criticalsection)|Odkazuje na třídu [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).|  
|[CComMultiThreadModel::ThreadModelNoCS](#threadmodelnocs)|Odkazuje na třídu [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[CComMultiThreadModel::Decrement](#decrement)|(Statické) Sníží hodnotu zadanou proměnnou způsobem bezpečné pro přístup z více vláken.|  
|[CComMultiThreadModel::Increment](#increment)|(Statické) Zvýší hodnotu zadanou proměnnou způsobem bezpečné pro přístup z více vláken.|  
  
## <a name="remarks"></a>Poznámky  
 Obvykle použijete, `CComMultiThreadModel` prostřednictvím jednoho ze dvou `typedef` názvy, buď [CComObjectThreadModel] (atl – typedefs.md #ccomobjectthreadmodel nebo [CComGlobalsThreadModel] (atl – typedefs.md #ccomglobalsthreadmodel. Třída odkazuje každý `typedef` závisí na model vláken používaný, jak je znázorněno v následující tabulce:  
  
|– definice typedef|Jeden dělení na vlákna|Dělení objektu Apartment|Volné dělení na vlákna|  
|-------------|----------------------|-------------------------|--------------------|  
|`CComObjectThreadModel`|S|S|M|  
|`CComGlobalsThreadModel`|S|M|M|  
  
 S = `CComSingleThreadModel`; M = `CComMultiThreadModel`  
  
 `CComMultiThreadModel` samotný definuje tři `typedef` názvy. `AutoCriticalSection` a `CriticalSection` referenční třídy, které poskytují metody pro získání a uvolněním vlastnictví kritická sekce. `ThreadModelNoCS` odkazy na třídy [CComMultiThreadModelNoCS(ccommultithreadmodelnocs-class.md).  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** atlbase.h  
  
##  <a name="autocriticalsection"></a>  CComMultiThreadModel::AutoCriticalSection  
 Při použití `CComMultiThreadModel`, `typedef` název `AutoCriticalSection` odkazuje na třídu [CComAutoCriticalSection](ccomautocriticalsection-class.md), který poskytuje metody pro získání a uvolněním vlastnictví objektu kritická sekce.  
  
```
typedef CComAutoCriticalSection AutoCriticalSection;
```  
  
### <a name="remarks"></a>Poznámky  
 [CComSingleThreadModel](ccomsinglethreadmodel-class.md) a [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md) také obsahovat definice pro `AutoCriticalSection`. Následující tabulka znázorňuje vztah mezi vláken třídy modelu a kritická sekce odkazuje `AutoCriticalSection`:  
  
|Třídy definované v|Odkazovaný – třída|  
|----------------------|----------------------|  
|`CComMultiThreadModel`|`CComCriticalSection`|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
  
 Kromě `AutoCriticalSection`, můžete použít `typedef` název [CriticalSection](#criticalsection). Neměla by být zadána `AutoCriticalSection` v globální objekty nebo členy statických tříd, pokud chcete odstranit kód CRT spuštění.  
  
### <a name="example"></a>Příklad  
 Následující kód je Modelováno podle [CComObjectRootEx](ccomobjectrootex-class.md)a předvádí `AutoCriticalSection` použitá v prostředí s vláken.  
  

```cpp  
template<class ThreadModel>
class CMyAutoCritClass
{
public:
   typedef ThreadModel _ThreadModel;
   typedef typename _ThreadModel::AutoCriticalSection _CritSec;

   CMyAutoCritClass() : m_dwRef(0) {}

   ULONG InternalAddRef()
   {
      return _ThreadModel::Increment(&m_dwRef);
   }
   ULONG InternalRelease()
   {
      return _ThreadModel::Decrement(&m_dwRef);   
   }
   void Lock() { m_critsec.Lock( ); }
   void Unlock() { m_critsec.Unlock(); }

private:
   _CritSec m_critsec;
   LONG m_dwRef;
```  
  
 Následující tabulky popisují výsledky `InternalAddRef` a `Lock` metody, v závislosti na **ThreadModel** parametr šablony a aplikace používá model vláken:  
  
### <a name="threadmodel--ccomobjectthreadmodel"></a>ThreadModel = CComObjectThreadModel  
  
|Metoda|Jeden nebo dělení objektu Apartment|Volné dělení na vlákna|  
|------------|-----------------------------------|--------------------|  
|`InternalAddRef`|Přírůstek není bezpečné pro přístup z více vláken.|Přírůstek je bezpečné pro přístup z více vláken.|  
|`Lock`|Neprovede žádnou akci; neexistuje žádné kritická sekce modulu k uzamčení.|Kritická sekce je uzamčena.|  
  
### <a name="threadmodel--ccomobjectthreadmodelthreadmodelnocs"></a>ThreadModel = CComObjectThreadModel::ThreadModelNoCS  
  
|Metoda|Jeden nebo dělení objektu Apartment|Volné dělení na vlákna|  
|------------|-----------------------------------|--------------------|  
|`InternalAddRef`|Přírůstek není bezpečné pro přístup z více vláken.|Přírůstek je bezpečné pro přístup z více vláken.|  
|`Lock`|Neprovede žádnou akci; neexistuje žádné kritická sekce modulu k uzamčení.|Neprovede žádnou akci; neexistuje žádné kritická sekce modulu k uzamčení.|  
  
##  <a name="criticalsection"></a>  CComMultiThreadModel::CriticalSection  
 Při použití `CComMultiThreadModel`, `typedef` název `CriticalSection` odkazuje na třídu [CComCriticalSection](ccomcriticalsection-class.md), který poskytuje metody pro získání a uvolněním vlastnictví objektu kritická sekce.  
  
```
typedef CComCriticalSection CriticalSection;
```  
  
### <a name="remarks"></a>Poznámky  
 [CComSingleThreadModel](ccomsinglethreadmodel-class.md) a [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md) také obsahovat definice pro `CriticalSection`. Následující tabulka znázorňuje vztah mezi vláken třídy modelu a kritická sekce odkazuje `CriticalSection`:  
  
|Třídy definované v|Odkazovaný – třída|  
|----------------------|----------------------|  
|`CComMultiThreadModel`|`CComCriticalSection`|  
|`CComSingleThreadModel`|`CComFakeCriticalSection`|  
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|  
  
 Kromě `CriticalSection`, můžete použít `typedef` název [AutoCriticalSection](#autocriticalsection). Neměla by být zadána `AutoCriticalSection` v globální objekty nebo členy statických tříd, pokud chcete odstranit kód CRT spuštění.  
  
### <a name="example"></a>Příklad  
 V tématu [CComMultiThreadModel::AutoCriticalSection](#autocriticalsection).  
  
##  <a name="decrement"></a>  CComMultiThreadModel::Decrement  
 Tato statická funkce volá funkci Win32 [InterlockedDecrement](http://msdn.microsoft.com/library/windows/desktop/ms683580), které sníží hodnotu proměnné, na kterou odkazuje `p`.  
  
```
static ULONG WINAPI Decrement(LPLONG p) throw ();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 [v] Ukazatel na proměnnou se odečte.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud výsledkem snížení je 0, `Decrement` vrátí hodnotu 0. Pokud je výsledkem snížení nenulové, návratovou hodnotu jsou taky nenulové hodnoty, ale nemusí být roven výsledek snížení.  
  
### <a name="remarks"></a>Poznámky  
 **InterlockedDecrement** zabrání více než jedno vlákno současně pomocí této proměnné.  
  
##  <a name="increment"></a>  CComMultiThreadModel::Increment  
 Tato statická funkce volá funkci Win32 [InterlockedIncrement](http://msdn.microsoft.com/library/windows/desktop/ms683614), což zvýší hodnotu proměnné, na kterou odkazuje `p`.  
  
```
static ULONG WINAPI Increment(LPLONG p) throw ();
```  
  
### <a name="parameters"></a>Parametry  
 `p`  
 [v] Ukazatel na proměnnou se zvýší.  
  
### <a name="return-value"></a>Návratová hodnota  
 Pokud výsledek přírůstek je 0, **přírůstek** vrátí hodnotu 0. Pokud je výsledek přírůstku nenulové hodnoty, návratovou hodnotu je také nenulové hodnoty, ale nemusí být roven výsledek přírůstku.  
  
### <a name="remarks"></a>Poznámky  
 **InterlockedIncrement** zabrání více než jedno vlákno současně pomocí této proměnné.  
  
##  <a name="threadmodelnocs"></a>  CComMultiThreadModel::ThreadModelNoCS  
 Při použití `CComMultiThreadModel`, `typedef` název `ThreadModelNoCS` odkazuje na třídu [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md).  
  
```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```  
  
### <a name="remarks"></a>Poznámky  
 `CComMultiThreadModelNoCS` poskytuje metody vláken pro zvyšování a dekrementace proměnné. neposkytuje však kritická sekce.  
  
 [CComSingleThreadModel](ccomsinglethreadmodel-class.md) a `CComMultiThreadModelNoCS` také obsahovat definice pro `ThreadModelNoCS`. Následující tabulka znázorňuje vztah mezi vláken třídu modelu a třída odkazuje `ThreadModelNoCS`:  
  
|Třídy definované v|Odkazovaný – třída|  
|----------------------|----------------------|  
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|  
|`CComSingleThreadModel`|`CComSingleThreadModel`|  
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|  
  
### <a name="example"></a>Příklad  
 V tématu [CComMultiThreadModel::AutoCriticalSection](#autocriticalsection).  
  
## <a name="see-also"></a>Viz také  
 [CComSingleThreadModel – třída](ccomsinglethreadmodel-class.md)   
 [CComAutoCriticalSection – třída](ccomautocriticalsection-class.md)   
 [CComCriticalSection – třída](ccomcriticalsection-class.md)   
 [Přehled třídy](../atl-class-overview.md)
