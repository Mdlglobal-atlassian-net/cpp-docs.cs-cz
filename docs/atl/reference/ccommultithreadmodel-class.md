---
title: CComMultiThreadModel – třída
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
ms.openlocfilehash: 74fb68eead498685ef252968124368863e27be75
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497093"
---
# <a name="ccommultithreadmodel-class"></a>CComMultiThreadModel – třída

`CComMultiThreadModel`poskytuje metody bezpečné pro přístup z více vláken pro zvýšení a snížení hodnoty proměnné.

## <a name="syntax"></a>Syntaxe

```
class CComMultiThreadModel
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Name|Popis|
|----------|-----------------|
|[CComMultiThreadModel::AutoCriticalSection](#autocriticalsection)|Odkazuje na třídu [CComAutoCriticalSection](../../atl/reference/ccomautocriticalsection-class.md).|
|[CComMultiThreadModel::CriticalSection](#criticalsection)|Odkazuje na třídu [CComCriticalSection](../../atl/reference/ccomcriticalsection-class.md).|
|[CComMultiThreadModel::ThreadModelNoCS](#threadmodelnocs)|Odkazuje na třídu [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md).|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CComMultiThreadModel::D ecrement](#decrement)|Tras Sníží hodnotu zadané proměnné způsobem zabezpečeným pro přístup z více vláken.|
|[CComMultiThreadModel:: Increment](#increment)|Tras Zvýší hodnotu zadané proměnné způsobem bezpečným pro přístup z více vláken.|

## <a name="remarks"></a>Poznámky

Obvykle použijete `CComMultiThreadModel` prostřednictvím jednoho ze dvou názvů **typedef** , buď [CComObjectThreadModel] (ATL-definice typedef. MD # CComObjectThreadModel nebo [CComGlobalsThreadModel] (ATL-definice typedef. MD # CComGlobalsThreadModel. Třída, na kterou odkazuje každý typ **typedef** , závisí na použitém modelu vláken, jak je znázorněno v následující tabulce:

|– definice typedef|Jednoduché dělení na vlákna|Dělení na vlákna|Bezplatné dělení na vlákna|
|-------------|----------------------|-------------------------|--------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S= `CComSingleThreadModel`; M= `CComMultiThreadModel`

`CComMultiThreadModel`sám sebe definuje tři názvy **typedef** . `AutoCriticalSection`a `CriticalSection` referenční třídy, které poskytují metody pro získání a uvolnění vlastnictví kritické části. `ThreadModelNoCS`odkazuje na třídu [CComMultiThreadModelNoCS (CComMultiThreadModelNoCS-class.md).

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

##  <a name="autocriticalsection"></a>CComMultiThreadModel::AutoCriticalSection

Při použití `CComMultiThreadModel`, `AutoCriticalSection` název **typedef** odkazuje na třídu [CComAutoCriticalSection](ccomautocriticalsection-class.md), která poskytuje metody pro získání a uvolnění vlastnictví objektu kritického oddílu.

```
typedef CComAutoCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Poznámky

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) a [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md) také obsahují definice pro `AutoCriticalSection`. Následující tabulka ukazuje vztah mezi třídou modelu vláken a kritickou sekcí oddílu, na kterou odkazuje `AutoCriticalSection`:

|Třída definovaná v|Odkazovaná třída|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Kromě `AutoCriticalSection`toho můžete použít název **typedef** [CriticalSection](#criticalsection). Pokud chcete odstranit spouštěcí `AutoCriticalSection` kód CRT, neměli byste určovat globální objekty ani statické členy třídy.

### <a name="example"></a>Příklad

Následující kód je modelován po [CComObjectRootEx](ccomobjectrootex-class.md)a ukazuje `AutoCriticalSection` použití v prostředí vláken.

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

V následujících tabulkách jsou uvedeny výsledky `InternalAddRef` metod a `Lock` `ThreadModel` , v závislosti na parametru šablony a modelu vláken používaném aplikací:

### <a name="threadmodel--ccomobjectthreadmodel"></a>ThreadModel = CComObjectThreadModel

|Metoda|Jednoduché nebo vícevláknové dělení na vlákna|Bezplatné dělení na vlákna|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|Přírůstek není bezpečný pro přístup z více vláken.|Přírůstek je bezpečný pro přístup z více vláken.|
|`Lock`|Neprovede žádnou akci. neexistuje žádný důležitý oddíl, který by bylo možné uzamknout.|Oddíl Critical je zamčený.|

### <a name="threadmodel--ccomobjectthreadmodelthreadmodelnocs"></a>ThreadModel = CComObjectThreadModel::ThreadModelNoCS

|Metoda|Jednoduché nebo vícevláknové dělení na vlákna|Bezplatné dělení na vlákna|
|------------|-----------------------------------|--------------------|
|`InternalAddRef`|Přírůstek není bezpečný pro přístup z více vláken.|Přírůstek je bezpečný pro přístup z více vláken.|
|`Lock`|Neprovede žádnou akci. neexistuje žádný důležitý oddíl, který by bylo možné uzamknout.|Neprovede žádnou akci. neexistuje žádný důležitý oddíl, který by bylo možné uzamknout.|

##  <a name="criticalsection"></a>CComMultiThreadModel:: CriticalSection

Při použití `CComMultiThreadModel`, `CriticalSection` název **typedef** odkazuje na třídu [CComCriticalSection](ccomcriticalsection-class.md), která poskytuje metody pro získání a uvolnění vlastnictví objektu kritického oddílu.

```
typedef CComCriticalSection CriticalSection;
```

### <a name="remarks"></a>Poznámky

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) a [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md) také obsahují definice pro `CriticalSection`. Následující tabulka ukazuje vztah mezi třídou modelu vláken a kritickou sekcí oddílu, na kterou odkazuje `CriticalSection`:

|Třída definovaná v|Odkazovaná třída|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Kromě `CriticalSection`toho můžete použít název **typedef** [AutoCriticalSection](#autocriticalsection). Pokud chcete odstranit spouštěcí `AutoCriticalSection` kód CRT, neměli byste určovat globální objekty ani statické členy třídy.

### <a name="example"></a>Příklad

Viz [CComMultiThreadModel:: AutoCriticalSection](#autocriticalsection).

##  <a name="decrement"></a>CComMultiThreadModel::D ecrement

Tato statická funkce volá funkci Win32 [InterlockedDecrement](/windows/win32/api/winnt/nf-winnt-interlockeddecrement), která snižuje hodnotu proměnné, na kterou odkazuje hodnota *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw ();
```

### <a name="parameters"></a>Parametry

*p*<br/>
pro Ukazatel na proměnnou, která má být snížena.

### <a name="return-value"></a>Návratová hodnota

Pokud je výsledek snížení 0, `Decrement` vrátí hodnotu 0. Pokud je výsledek snížení nenulový, vrácená hodnota je také nenulová, ale nemusí být rovna výsledku snížení.

### <a name="remarks"></a>Poznámky

`InterlockedDecrement`zabrání více než jednomu vláknu současně pomocí této proměnné.

##  <a name="increment"></a>CComMultiThreadModel:: Increment

Tato statická funkce volá funkci Win32 [InterlockedIncrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement), která zvyšuje hodnotu proměnné, na kterou odkazuje hodnota *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw ();
```

### <a name="parameters"></a>Parametry

*p*<br/>
pro Ukazatel na proměnnou, která se má zvýšit.

### <a name="return-value"></a>Návratová hodnota

Pokud je výsledek přírůstku 0, `Increment` vrátí hodnotu 0. Pokud je výsledek přírůstku nenulový, vrácená hodnota je také nenulová, ale nemusí být rovna výsledku zvýšení.

### <a name="remarks"></a>Poznámky

`InterlockedIncrement`zabrání více než jednomu vláknu současně pomocí této proměnné.

##  <a name="threadmodelnocs"></a>CComMultiThreadModel::ThreadModelNoCS

Při použití `CComMultiThreadModel`se `ThreadModelNoCS` název **typedef** odkazuje na třídu [CComMultiThreadModelNoCS](ccommultithreadmodelnocs-class.md).

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>Poznámky

`CComMultiThreadModelNoCS`poskytuje metody bezpečné pro přístup z více vláken pro zvýšení a snížení proměnné; neposkytuje ale kritickou část.

[CComSingleThreadModel](ccomsinglethreadmodel-class.md) a `CComMultiThreadModelNoCS` také obsahuje definice pro `ThreadModelNoCS`. Následující tabulka ukazuje vztah mezi třídou modelu vláken a třídou, na kterou odkazuje `ThreadModelNoCS`:

|Třída definovaná v|Odkazovaná třída|
|----------------------|----------------------|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>Příklad

Viz [CComMultiThreadModel:: AutoCriticalSection](#autocriticalsection).

## <a name="see-also"></a>Viz také:

[CComSingleThreadModel – třída](ccomsinglethreadmodel-class.md)<br/>
[CComAutoCriticalSection – třída](ccomautocriticalsection-class.md)<br/>
[CComAutoCriticalSection – třída](ccomcriticalsection-class.md)<br/>
[Přehled třídy](../atl-class-overview.md)
