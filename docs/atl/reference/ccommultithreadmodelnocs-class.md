---
title: CComMultiThreadModelNoCS – třída
ms.date: 11/04/2016
f1_keywords:
- CComMultiThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS::AutoCriticalSection
- ATLBASE/ATL::CComMultiThreadModelNoCS::CriticalSection
- ATLBASE/ATL::CComMultiThreadModelNoCS::ThreadModelNoCS
- ATLBASE/ATL::CComMultiThreadModelNoCS::Decrement
- ATLBASE/ATL::CComMultiThreadModelNoCS::Increment
helpviewer_keywords:
- ATL, multithreading
- CComMultiThreadModelNoCS class
- threading [ATL]
ms.assetid: 2b3f7a45-fd72-452c-aaf3-ccdaa621c821
ms.openlocfilehash: 01c7f953b6b8916394ee4c2b5b27cf84af52b920
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497085"
---
# <a name="ccommultithreadmodelnocs-class"></a>CComMultiThreadModelNoCS – třída

`CComMultiThreadModelNoCS`poskytuje metody bezpečné pro přístup z více vláken pro zvýšení a snížení hodnoty proměnné bez důležitého zamykání oddílů nebo odemknutí funkčnosti.

## <a name="syntax"></a>Syntaxe

```
class CComMultiThreadModelNoCS
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Name|Popis|
|----------|-----------------|
|[CComMultiThreadModelNoCS::AutoCriticalSection](#autocriticalsection)|Odkazuje na třídu [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).|
|[CComMultiThreadModelNoCS::CriticalSection](#criticalsection)|Odkazuje na `CComFakeCriticalSection`třídu.|
|[CComMultiThreadModelNoCS::ThreadModelNoCS](#threadmodelnocs)|Odkazuje na `CComMultiThreadModelNoCS`třídu.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[CComMultiThreadModelNoCS::Decrement](#decrement)|Tras Sníží hodnotu zadané proměnné způsobem zabezpečeným pro přístup z více vláken.|
|[CComMultiThreadModelNoCS::Increment](#increment)|Tras Zvýší hodnotu zadané proměnné způsobem bezpečným pro přístup z více vláken.|

## <a name="remarks"></a>Poznámky

`CComMultiThreadModelNoCS`je podobný jako [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) v tom, že poskytuje metody bezpečné pro přístup z více vláken pro zvýšení a snížení proměnné. Nicméně při odkazování na třídu kritického oddílu pomocí `CComMultiThreadModelNoCS`metody `Lock` , jako například a `Unlock` , neprovede nic.

Obvykle se používá `CComMultiThreadModelNoCS` `ThreadModelNoCS` pomocí názvu **typedef** . Tato **definice typedef** je definována `CComMultiThreadModelNoCS`v `CComMultiThreadModel`, a [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md).

> [!NOTE]
>  Globální názvy **typedef** [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) a [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel) neodkazují `CComMultiThreadModelNoCS`.

Kromě `ThreadModelNoCS`, `CComMultiThreadModelNoCS` definují a`AutoCriticalSection` . `CriticalSection` Tyto dva názvy **typedef** odkazují na [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), které poskytují prázdné metody přidružené k získání a uvolnění kritické části.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

##  <a name="autocriticalsection"></a>  CComMultiThreadModelNoCS::AutoCriticalSection

Při použití `CComMultiThreadModelNoCS`se `AutoCriticalSection` název **typedef** odkazuje na třídu [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Poznámky

Protože `CComFakeCriticalSection` neposkytuje kritickou část, její metody nedělají nic.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) a [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) také obsahují definice pro `AutoCriticalSection`. Následující tabulka ukazuje vztah mezi třídou modelu vláken a kritickou sekcí oddílu, na kterou odkazuje `AutoCriticalSection`:

|Třída definovaná v|Odkazovaná třída|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

Kromě `AutoCriticalSection`toho můžete použít název **typedef** [CriticalSection](#criticalsection). Pokud chcete odstranit spouštěcí `AutoCriticalSection` kód CRT, neměli byste určovat globální objekty ani statické členy třídy.

### <a name="example"></a>Příklad

Viz [CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

##  <a name="criticalsection"></a>CComMultiThreadModelNoCS:: CriticalSection

Při použití `CComMultiThreadModelNoCS`se `CriticalSection` název **typedef** odkazuje na třídu [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>Poznámky

Protože `CComFakeCriticalSection` neposkytuje kritickou část, její metody nedělají nic.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) a [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) také obsahují definice pro `CriticalSection`. Následující tabulka ukazuje vztah mezi třídou modelu vláken a kritickou sekcí oddílu, na kterou odkazuje `CriticalSection`:

|Třída definovaná v|Odkazovaná třída|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

Kromě `CriticalSection`toho můžete použít název `AutoCriticalSection` **typedef** . Pokud chcete odstranit spouštěcí `AutoCriticalSection` kód CRT, neměli byste určovat globální objekty ani statické členy třídy.

### <a name="example"></a>Příklad

Viz [CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

##  <a name="decrement"></a>CComMultiThreadModelNoCS::D ecrement

Tato statická funkce volá funkci Win32 [InterlockedDecrement](/windows/win32/api/winnt/nf-winnt-interlockeddecrement), která snižuje hodnotu proměnné, na kterou odkazuje hodnota *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
pro Ukazatel na proměnnou, která má být snížena.

### <a name="return-value"></a>Návratová hodnota

Pokud je výsledek snížení 0, `Decrement` vrátí hodnotu 0. Pokud je výsledek snížení nenulový, vrácená hodnota je také nenulová, ale nemusí být rovna výsledku snížení.

### <a name="remarks"></a>Poznámky

**InterlockedDecrement** zabraňuje současnému více než jednomu vláknu pomocí této proměnné.

##  <a name="increment"></a>CComMultiThreadModelNoCS:: Increment

Tato statická funkce volá funkci Win32 [InterlockedIncrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement), která zvyšuje hodnotu proměnné, na kterou odkazuje hodnota *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
pro Ukazatel na proměnnou, která se má zvýšit.

### <a name="return-value"></a>Návratová hodnota

Pokud je výsledek přírůstku 0, pak **přírůstek** vrátí hodnotu 0. Pokud je výsledek přírůstku nenulový, vrácená hodnota je také nenulová, ale nemusí být rovna výsledku zvýšení.

### <a name="remarks"></a>Poznámky

**InterlockedIncrement** zabraňuje současnému více než jednomu vláknu pomocí této proměnné.

##  <a name="threadmodelnocs"></a>CComMultiThreadModelNoCS::ThreadModelNoCS

Při použití `CComMultiThreadModelNoCS`se v názvu `ThreadModelNoCS` typedef jednoduše odkazují `CComMultiThreadModelNoCS`.

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>Poznámky

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) a [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) také obsahují definice pro `ThreadModelNoCS`. Následující tabulka ukazuje vztah mezi třídou modelu vláken a třídou, na kterou odkazuje `ThreadModelNoCS`:

|Třída definovaná v|Odkazovaná třída|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|

Všimněte si, že definice `ThreadModelNoCS` v `CComMultiThreadModelNoCS` nástroji poskytuje symetrie `CComSingleThreadModel`s `CComMultiThreadModel` a. Předpokládejme například, že vzorový kód v `CComMultiThreadModel::AutoCriticalSection` deklaraci následující **typedef**:

[!code-cpp[NVC_ATL_COM#37](../../atl/codesnippet/cpp/ccommultithreadmodelnocs-class_1.h)]

Bez ohledu na třídu zadanou pro `ThreadModel` ( `CComMultiThreadModelNoCS`například) se `_ThreadModel` odpovídajícím způsobem vyřeší.

### <a name="example"></a>Příklad

Viz [CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="see-also"></a>Viz také:

[Přehled třídy](../../atl/atl-class-overview.md)
