---
title: CComSingleThreadModel – třída
ms.date: 2/29/2020
f1_keywords:
- CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel::AutoCriticalSection
- ATLBASE/ATL::CComSingleThreadModel::CriticalSection
- ATLBASE/ATL::CComSingleThreadModel::ThreadModelNoCS
- ATLBASE/ATL::CComSingleThreadModel::Decrement
- ATLBASE/ATL::CComSingleThreadModel::Increment
helpviewer_keywords:
- single-threaded applications
- CComSingleThreadModel class
- single-threaded applications, ATL
ms.assetid: e5dc30c7-405a-4ba4-8ae9-51937243fce8
ms.openlocfilehash: 9b111e06ba475a5077ba36b2235e8bd530302189
ms.sourcegitcommit: ab8d7b47b63b62892a1256a09b1324a9a136eccf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/02/2020
ms.locfileid: "78215451"
---
# <a name="ccomsinglethreadmodel-class"></a>CComSingleThreadModel – třída

Tato třída poskytuje metody pro zvýšení a snížení hodnoty proměnné.

## <a name="syntax"></a>Syntaxe

```
class CComSingleThreadModel
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

|Název|Popis|
|----------|-----------------|
|[CComSingleThreadModel::AutoCriticalSection](#autocriticalsection)|Odkazuje na třídu [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).|
|[CComSingleThreadModel:: CriticalSection](#criticalsection)|Odkazuje na třídu `CComFakeCriticalSection`.|
|[CComSingleThreadModel::ThreadModelNoCS](#threadmodelnocs)|Odkazuje na `CComSingleThreadModel`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComSingleThreadModel::D ecrement](#decrement)|Sníží hodnotu zadané proměnné. Tato implementace není bezpečná pro přístup z více vláken.|
|[CComSingleThreadModel:: Increment](#increment)|Zvýší hodnotu zadané proměnné. Tato implementace není bezpečná pro přístup z více vláken.|

## <a name="remarks"></a>Poznámky

`CComSingleThreadModel` poskytuje metody pro zvýšení a snížení hodnoty proměnné. Na rozdíl od [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) a [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md)tyto metody nejsou bezpečné pro přístup z více vláken.

Obvykle používáte `CComSingleThreadModel` prostřednictvím jednoho ze dvou názvů **typedef** , buď [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) nebo [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel). Třída, na kterou odkazuje každý typ **typedef** , závisí na použitém modelu vláken, jak je znázorněno v následující tabulce:

|– definice typedef|Model s jedním vláknem|Model vláken typu Apartment|Model bezplatných vláken|
|-------------|----------------------------|-------------------------------|--------------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`; M = `CComMultiThreadModel`

`CComSingleThreadModel` sám definuje tři názvy **typedef** . `ThreadModelNoCS` odkazuje na `CComSingleThreadModel`. `AutoCriticalSection` a `CriticalSection` referenční třídy [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), která poskytuje prázdné metody přidružené k získání a uvolnění vlastnictví kritické části.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase. h

##  <a name="autocriticalsection"></a>CComSingleThreadModel::AutoCriticalSection

Při použití `CComSingleThreadModel`název **typedef** `AutoCriticalSection` odkazuje na třídu [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Poznámky

Vzhledem k tomu, že `CComFakeCriticalSection` neposkytuje kritickou část, její metody nedělají nic.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) a [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) obsahují definice pro `AutoCriticalSection`. Následující tabulka ukazuje vztah mezi třídou modelu vláken a kritickou oddílovou třídou, na kterou odkazuje `AutoCriticalSection`:

|Třída definovaná v|Odkazovaná třída|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Kromě `AutoCriticalSection`můžete použít název **typedef** [CriticalSection](#criticalsection). Pokud chcete odstranit spouštěcí kód CRT, neměli byste určovat `AutoCriticalSection` v globálních objektech nebo členech statické třídy.

### <a name="example"></a>Příklad

Viz [CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

##  <a name="criticalsection"></a>CComSingleThreadModel:: CriticalSection

Při použití `CComSingleThreadModel`název **typedef** `CriticalSection` odkazuje na třídu [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>Poznámky

Vzhledem k tomu, že `CComFakeCriticalSection` neposkytuje kritickou část, její metody nedělají nic.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) a [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) obsahují definice pro `CriticalSection`. Následující tabulka ukazuje vztah mezi třídou modelu vláken a kritickou oddílovou třídou, na kterou odkazuje `CriticalSection`:

|Třída definovaná v|Odkazovaná třída|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Kromě `CriticalSection`můžete použít název **typedef** [AutoCriticalSection](#autocriticalsection). Pokud chcete odstranit spouštěcí kód CRT, neměli byste určovat `AutoCriticalSection` v globálních objektech nebo členech statické třídy.

### <a name="example"></a>Příklad

Viz [CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

##  <a name="decrement"></a>CComSingleThreadModel::D ecrement

Tato statická funkce snižuje hodnotu proměnné, na kterou odkazuje *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>Parametry

*trub*<br/>
pro Ukazatel na proměnnou, která má být snížena.

### <a name="return-value"></a>Návratová hodnota

Výsledek snížení.

##  <a name="increment"></a>CComSingleThreadModel:: Increment

Tato statická funkce zvyšuje hodnotu proměnné, na kterou odkazuje *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>Parametry

*trub*<br/>
pro Ukazatel na proměnnou, která se má zvýšit.

### <a name="return-value"></a>Návratová hodnota

Výsledek zvýšení

##  <a name="threadmodelnocs"></a>CComSingleThreadModel::ThreadModelNoCS

Při použití `CComSingleThreadModel`název **typedef** `ThreadModelNoCS` jednoduše odkazuje na `CComSingleThreadModel`.

```
typedef CComSingleThreadModel ThreadModelNoCS;
```

### <a name="remarks"></a>Poznámky

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) a [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) obsahují definice pro `ThreadModelNoCS`. Následující tabulka ukazuje vztah mezi třídou modelu vláken a třídou, na kterou odkazuje `ThreadModelNoCS`:

|Třída definovaná v|Odkazovaná třída|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>Příklad

Viz [CComMultiThreadModel:: AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="see-also"></a>Viz také:

[Přehled třídy](../../atl/atl-class-overview.md)
