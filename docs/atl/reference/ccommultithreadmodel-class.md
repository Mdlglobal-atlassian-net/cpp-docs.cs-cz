---
title: CComMultiThreadModel – třída | Dokumentace Microsoftu
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
ms.openlocfilehash: 33eac78dc871dd2a9869452bc829150c3356fd0a
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43754940"
---
# <a name="ccommultithreadmodel-class"></a>CComMultiThreadModel – třída

`CComMultiThreadModel` poskytuje metody bezpečným pro vlákno pro zvyšování a dekrementace hodnotu proměnné.

## <a name="syntax"></a>Syntaxe

```
class CComMultiThreadModel
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|[CComMultiThreadModel::AutoCriticalSection](#autocriticalsection)|Odkazuje na třídu [ccomautocriticalsection –](../../atl/reference/ccomautocriticalsection-class.md).|
|[CComMultiThreadModel::CriticalSection](#criticalsection)|Odkazuje na třídu [ccomautocriticalsection –](../../atl/reference/ccomcriticalsection-class.md).|
|[CComMultiThreadModel::ThreadModelNoCS](#threadmodelnocs)|Odkazuje na třídu [ccommultithreadmodelnocs –](../../atl/reference/ccommultithreadmodelnocs-class.md).|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComMultiThreadModel::Decrement](#decrement)|(Statické) Sníží hodnotu zadanou proměnnou způsobem bezpečným pro vlákno.|
|[CComMultiThreadModel::Increment](#increment)|(Statické) Zvýší hodnotu zadanou proměnnou způsobem bezpečným pro vlákno.|

## <a name="remarks"></a>Poznámky

Obvykle použijete `CComMultiThreadModel` prostřednictvím jednoho ze dvou **– typedef** názvy, buď [CComObjectThreadModel] (atl – typedefs.md #ccomobjectthreadmodel nebo [CComGlobalsThreadModel] (atl – typedefs.md #ccomglobalsthreadmodel. Třída odkazovaná každou **typedef** závisí na model vláken použít, jak je znázorněno v následující tabulce:

|– definice typedef|Jeden dělení na vlákna|Práce s vlákny typu Apartment|Bezplatné dělení na vlákna|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`; M = `CComMultiThreadModel`

`CComMultiThreadModel` samotný definuje tři **typedef** názvy. `AutoCriticalSection` a `CriticalSection` odkazovat na třídy, které poskytují metody pro získání a uvolnění vlastnictví kritický oddíl. `ThreadModelNoCS` odkazy na třídu [CComMultiThreadModelNoCS(ccommultithreadmodelnocs-class.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="autocriticalsection"></a>  CComMultiThreadModel::AutoCriticalSection

Při použití `CComMultiThreadModel`, **typedef** název `AutoCriticalSection` odkazuje na třídu [ccomautocriticalsection –](ccomautocriticalsection-class.md), který poskytuje metody pro získání a uvolnění vlastnictví kritický oddíl objekt.

```
typedef CComAutoCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Poznámky

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) a [ccommultithreadmodelnocs –](ccommultithreadmodelnocs-class.md) také obsahovat definice pro `AutoCriticalSection`. Následující tabulka ukazuje vztah mezi vláken třídy modelu a kritický oddíl odkazuje `AutoCriticalSection`:

|Třída definovaná v|Třída odkazovaná|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Kromě `AutoCriticalSection`, můžete použít **typedef** název [criticalsection –](#criticalsection). Neměli byste zadávat `AutoCriticalSection` v globálních objektů nebo statické členy třídy Pokud budete chtít vyloučit při spuštění kódu CRT.

### <a name="example"></a>Příklad

Následující kód je Modelováno podle [CComObjectRootEx](ccomobjectrootex-class.md)a ukazuje `AutoCriticalSection` používá v prostředí vláken.

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

Následující tabulky popisují výsledky `InternalAddRef` a `Lock` metody, v závislosti na `ThreadModel` parametr šablony a model vláken aplikace používá:

### <a name="threadmodel--ccomobjectthreadmodel"></a>ThreadModel = CComObjectThreadModel

|Metoda|Jeden nebo práce s vlákny typu Apartment|Bezplatné dělení na vlákna|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|Přírůstek není bezpečná pro vlákno.|Přírůstek je bezpečná pro vlákno.|
|`Lock`|Nemá žádný účinek; neexistuje žádné kritický oddíl uzamknout.|Kritický oddíl je uzamčen.|

### <a name="threadmodel--ccomobjectthreadmodelthreadmodelnocs"></a>ThreadModel = CComObjectThreadModel::ThreadModelNoCS

|Metoda|Jeden nebo práce s vlákny typu Apartment|Bezplatné dělení na vlákna|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|Přírůstek není bezpečná pro vlákno.|Přírůstek je bezpečná pro vlákno.|
|`Lock`|Nemá žádný účinek; neexistuje žádné kritický oddíl uzamknout.|Nemá žádný účinek; neexistuje žádné kritický oddíl uzamknout.|

##  <a name="criticalsection"></a>  CComMultiThreadModel::CriticalSection

Při použití `CComMultiThreadModel`, **typedef** název `CriticalSection` odkazuje na třídu [ccomautocriticalsection –](ccomcriticalsection-class.md), který poskytuje metody pro získání a uvolnění vlastnictví objektu kritický oddíl.

```
typedef CComCriticalSection CriticalSection;
```

### <a name="remarks"></a>Poznámky

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) a [ccommultithreadmodelnocs –](ccommultithreadmodelnocs-class.md) také obsahovat definice pro `CriticalSection`. Následující tabulka ukazuje vztah mezi vláken třídy modelu a kritický oddíl odkazuje `CriticalSection`:

|Třída definovaná v|Třída odkazovaná|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Kromě `CriticalSection`, můžete použít **typedef** název [AutoCriticalSection](#autocriticalsection). Neměli byste zadávat `AutoCriticalSection` v globálních objektů nebo statické členy třídy Pokud budete chtít vyloučit při spuštění kódu CRT.

### <a name="example"></a>Příklad

Zobrazit [CComMultiThreadModel::AutoCriticalSection](#autocriticalsection).

##  <a name="decrement"></a>  CComMultiThreadModel::Decrement

Tato statická funkce volá funkci Win32 [InterlockedDecrement](/windows/desktop/api/winbase/nf-winbase-interlockeddecrement), které sníží hodnotu proměnné, na které odkazuje *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw ();
```

### <a name="parameters"></a>Parametry

*p*  
[in] Ukazatel na proměnnou chcete snížit.

### <a name="return-value"></a>Návratová hodnota

Pokud výsledek snížení je 0, `Decrement` vrátí hodnotu 0. Pokud je výsledkem snížení nenulovou hodnotu, návratová hodnota je také nenulovou hodnotu, ale nemusí být roven výsledku snížení.

### <a name="remarks"></a>Poznámky

`InterlockedDecrement` zabrání současně pomocí této proměnné více než jedno vlákno.

##  <a name="increment"></a>  CComMultiThreadModel::Increment

Tato statická funkce volá funkci Win32 [InterlockedIncrement](/windows/desktop/api/winbase/nf-winbase-interlockedincrement), který zvýší hodnotu proměnné, na které odkazuje *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw ();
```

### <a name="parameters"></a>Parametry

*p*  
[in] Ukazatel na proměnnou se zvýší.

### <a name="return-value"></a>Návratová hodnota

Pokud výsledek přírůstek je 0, `Increment` vrátí hodnotu 0. Pokud je výsledkem přírůstku nenulovou hodnotu, návratová hodnota je také nenulovou hodnotu, ale nesmí být roven výsledku přírůstku.

### <a name="remarks"></a>Poznámky

`InterlockedIncrement` zabrání současně pomocí této proměnné více než jedno vlákno.

##  <a name="threadmodelnocs"></a>  CComMultiThreadModel::ThreadModelNoCS

Při použití `CComMultiThreadModel`, **typedef** název `ThreadModelNoCS` odkazuje na třídu [ccommultithreadmodelnocs –](ccommultithreadmodelnocs-class.md).

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>Poznámky

`CComMultiThreadModelNoCS` poskytuje metody bezpečným pro vlákno pro zvyšování a dekrementace proměnné. neposkytuje však kritický oddíl.

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) a `CComMultiThreadModelNoCS` také obsahovat definice pro `ThreadModelNoCS`. Následující tabulka ukazuje vztah mezi vláken třídy modelu a odkazuje `ThreadModelNoCS`:

|Třída definovaná v|Třída odkazovaná|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>Příklad

Zobrazit [CComMultiThreadModel::AutoCriticalSection](#autocriticalsection).

## <a name="see-also"></a>Viz také

[CComSingleThreadModel – třída](ccomsinglethreadmodel-class.md)   
[Ccomautocriticalsection – třída](ccomautocriticalsection-class.md)   
[Ccomautocriticalsection – třída](ccomcriticalsection-class.md)   
[Přehled tříd](../atl-class-overview.md)
