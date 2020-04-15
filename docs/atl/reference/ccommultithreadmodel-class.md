---
title: Třída CComMultiThreadModel
ms.date: 11/04/2016
f1_keywords:
- CComMultiThreadModel
- ATLBASE/ATL::CComMultiThreadModel
- ATLBASE/ATL::CComMultiThreadModel::AutoCriticalSection
- ATLBASE/ATL::CComMultiThreadModel::CriticalSection
- ATLBASE/ATL::CComMultiThreadModel::ThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModel::Decrement
- ATLBASE/ATL::CComMultiThreadModel::Increment
helpviewer_keywords:
- ATL, multithreading
- CComMultiThreadModel class
- threading [ATL]
ms.assetid: db8f1662-2f7a-44b3-b341-ffbfb6e422a3
ms.openlocfilehash: 7ef803439d2d683633e8f9c00810542dd787541e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327672"
---
# <a name="ccommultithreadmodel-class"></a>Třída CComMultiThreadModel

`CComMultiThreadModel`poskytuje metody bezpečné pro přístup z více vláken pro zvýšení a snížení hodnoty proměnné.

## <a name="syntax"></a>Syntaxe

```
class CComMultiThreadModel
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Name (Název)|Popis|
|----------|-----------------|
|[CcomMultiThreadModel::Autokritickýoddíl](#autocriticalsection)|Odkazuje na třídu [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md).|
|[CcomMultiThreadModel::Kritickýoddíl](#criticalsection)|Reference třídy [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).|
|[CcomMultiThreadModel::ThreadModelNoCS](#threadmodelnocs)|Odkazuje na třídu [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CComMultiThreadModel::Decrement](#decrement)|(Statické) Sníží hodnotu zadané proměnné způsobem bezpečným pro přístup z více vláken.|
|[CComMultiThreadModel::Přírůstek](#increment)|(Statické) Zintáží hodnotu zadané proměnné způsobem bezpečným pro přístup z více vláken.|

## <a name="remarks"></a>Poznámky

Obvykle používáte `CComMultiThreadModel` prostřednictvím jednoho ze dvou názvů **typedef,** buď [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel nebo [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel. Třída, na kterou odkazuje každý **typedef,** závisí na použitém modelu zřetězení, jak je znázorněno v následující tabulce:

| – definice typedef|Jedno závitování|Apartment threading|Volné závitování|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S `CComSingleThreadModel`= ; M=`CComMultiThreadModel`

`CComMultiThreadModel`sama definuje tři **názvy typedef.** `AutoCriticalSection`a `CriticalSection` referenční třídy, které poskytují metody pro získání a uvolnění vlastnictví kritické části. `ThreadModelNoCS`odkazuje na třídu [CComMultiThreadModelNoCS(ccommultithreadmodelnocs-class.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="ccommultithreadmodelautocriticalsection"></a><a name="autocriticalsection"></a>CcomMultiThreadModel::Autokritickýoddíl

Při `CComMultiThreadModel`použití název **typedef** `AutoCriticalSection` odkazuje na třídu [CComAutoCriticalSection](ccomautocriticalsection-class.md), která poskytuje metody pro získání a uvolnění vlastnictví objektu kritické části.

```
typedef CComAutoCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Poznámky

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) a [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md) také `AutoCriticalSection`obsahují definice pro . V následující tabulce je uvedena relace mezi třídou modelu zřetězení a třídou kritického oddílu, na kterou odkazuje `AutoCriticalSection`:

|Třída definovaná v|Odkazovaná třída|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Kromě `AutoCriticalSection`, můžete použít **název typedef** [CriticalSection](#criticalsection). Pokud chcete `AutoCriticalSection` odstranit spouštěcí kód CRT, neměli byste je určovat v globálních objektech nebo členech statické třídy.

### <a name="example"></a>Příklad

Následující kód je modelován podle [CComObjectRootEx](ccomobjectrootex-class.md)a `AutoCriticalSection` ukazuje, že se používá v prostředí vláken.

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

V následujících tabulkách `Lock` jsou uvedeny `ThreadModel` výsledky metod `InternalAddRef` a v závislosti na parametru šablony a modelu zřetězení používaném aplikací:

### <a name="threadmodel--ccomobjectthreadmodel"></a>ThreadModel = CComObjectThreadModel

|Metoda|Jednolůžkové nebo bytové závitování|Volné zřetězení|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|Přírůstek není bezpečný pro přístup z více vláken.|Přírůstek je bezpečný pro přístup z více vláken.|
|`Lock`|Nedělá nic; neexistuje žádný kritický řez, který by bylo možné zamknout.|Kritická část je uzamčena.|

### <a name="threadmodel--ccomobjectthreadmodelthreadmodelnocs"></a>ThreadModel = CComObjectThreadModel::ThreadModelNoCS

|Metoda|Jednolůžkové nebo bytové závitování|Volné zřetězení|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|Přírůstek není bezpečný pro přístup z více vláken.|Přírůstek je bezpečný pro přístup z více vláken.|
|`Lock`|Nedělá nic; neexistuje žádný kritický řez, který by bylo možné zamknout.|Nedělá nic; neexistuje žádný kritický řez, který by bylo možné zamknout.|

## <a name="ccommultithreadmodelcriticalsection"></a><a name="criticalsection"></a>CcomMultiThreadModel::Kritickýoddíl

Při `CComMultiThreadModel`použití název **typedef** `CriticalSection` odkazuje na třídu [CComCriticalSection](ccomcriticalsection-class.md), která poskytuje metody pro získání a uvolnění vlastnictví objektu kritické části.

```
typedef CComCriticalSection CriticalSection;
```

### <a name="remarks"></a>Poznámky

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) a [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md) také `CriticalSection`obsahují definice pro . V následující tabulce je uvedena relace mezi třídou modelu zřetězení a třídou kritického oddílu, na kterou odkazuje `CriticalSection`:

|Třída definovaná v|Odkazovaná třída|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Kromě `CriticalSection`aplikace můžete použít název **typedef** [AutoCriticalSection](#autocriticalsection). Pokud chcete `AutoCriticalSection` odstranit spouštěcí kód CRT, neměli byste je určovat v globálních objektech nebo členech statické třídy.

### <a name="example"></a>Příklad

Viz [ccommultithreadmodel::autocriticalsection](#autocriticalsection).

## <a name="ccommultithreadmodeldecrement"></a><a name="decrement"></a>CComMultiThreadModel::Decrement

Tato statická funkce volá win32 funkce [InterlockedDecrement](/windows/win32/api/winnt/nf-winnt-interlockeddecrement), která snižuje hodnotu proměnné, na kterou se vztahuje *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw ();
```

### <a name="parameters"></a>Parametry

*P*<br/>
[v] Ukazatel na proměnnou, která má být snížena.

### <a name="return-value"></a>Návratová hodnota

Pokud je výsledek snížení 0, vrátí `Decrement` 0. Pokud je výsledek snížení nenulová, vrácená hodnota je také nenulová, ale nemusí se rovnat výsledku snížení.

### <a name="remarks"></a>Poznámky

`InterlockedDecrement`zabraňuje současnému použití této proměnné více než jednomu vláknu.

## <a name="ccommultithreadmodelincrement"></a><a name="increment"></a>CComMultiThreadModel::Přírůstek

Tato statická funkce volá win32 funkce [InterlockedIncrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement), která zintálí hodnotu proměnné, na kterou je odkazováno *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw ();
```

### <a name="parameters"></a>Parametry

*P*<br/>
[v] Ukazatel na proměnnou, která má být zpřísněna.

### <a name="return-value"></a>Návratová hodnota

Pokud je výsledek přírůstku 0, `Increment` vrátí 0. Pokud je výsledek přírůstku nenulový, vrácená hodnota je také nenulová, ale nemusí se rovnat výsledku přírůstku.

### <a name="remarks"></a>Poznámky

`InterlockedIncrement`zabraňuje současnému použití této proměnné více než jednomu vláknu.

## <a name="ccommultithreadmodelthreadmodelnocs"></a><a name="threadmodelnocs"></a>CcomMultiThreadModel::ThreadModelNoCS

Při `CComMultiThreadModel`použití název **typedef** `ThreadModelNoCS` odkazuje na třídu [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md).

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>Poznámky

`CComMultiThreadModelNoCS`poskytuje metody bezpečné pro přístup z více vláken pro zvýšení a snížení proměnné; však neposkytuje kritický oddíl.

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) `CComMultiThreadModelNoCS` a také obsahují `ThreadModelNoCS`definice pro . V následující tabulce je uvedena relace mezi třídou modelu `ThreadModelNoCS`zřetězení a třídou, na kterou odkazuje :

|Třída definovaná v|Odkazovaná třída|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>Příklad

Viz [ccommultithreadmodel::autocriticalsection](#autocriticalsection).

## <a name="see-also"></a>Viz také

[Třída CComsingleThreadModel](ccomsinglethreadmodel-class.md)<br/>
[Třída CComautocriticalsection](ccomautocriticalsection-class.md)<br/>
[Třída CComCriticalSection](ccomcriticalsection-class.md)<br/>
[Přehled třídy](../atl-class-overview.md)
