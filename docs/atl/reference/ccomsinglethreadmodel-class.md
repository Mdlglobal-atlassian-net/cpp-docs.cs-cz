---
title: Třída CComsingleThreadModel
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
ms.openlocfilehash: 3d8169c999ba96049bc711033f7ba2ef53989663
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327335"
---
# <a name="ccomsinglethreadmodel-class"></a>Třída CComsingleThreadModel

Tato třída poskytuje metody pro zvýšení a snížení hodnoty proměnné.

## <a name="syntax"></a>Syntaxe

```
class CComSingleThreadModel
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Name (Název)|Popis|
|----------|-----------------|
|[CcomsingleThreadModel::autokritický oddíl](#autocriticalsection)|Reference třídy [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).|
|[CcomsingleThreadModel::Kritickýoddíl](#criticalsection)|Třída Reference `CComFakeCriticalSection`.|
|[CcomsingleThreadModel::ThreadModelNoCS](#threadmodelnocs)|Odkazy `CComSingleThreadModel`.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CComSingleThreadModel::Decrement](#decrement)|Sníží hodnotu zadané proměnné. Tato implementace není bezpečná pro přístup z více vláken.|
|[CComSingleThreadModel::Přírůstek](#increment)|Zintáží hodnotu zadané proměnné. Tato implementace není bezpečná pro přístup z více vláken.|

## <a name="remarks"></a>Poznámky

`CComSingleThreadModel`poskytuje metody pro zvýšení a snížení hodnoty proměnné. Na rozdíl od [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) a [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md), tyto metody nejsou bezpečné pro přístup z více vláken.

Obvykle se používá `CComSingleThreadModel` prostřednictvím jednoho ze dvou **typedef** názvy, [cComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) nebo [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel). Třída, na kterou odkazuje každý **typedef,** závisí na použitém modelu zřetězení, jak je znázorněno v následující tabulce:

| – definice typedef|Model jednoho závitu|Model apartment threadingu|Model volného závitování|
|-------------|----------------------------|-------------------------------|--------------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S `CComSingleThreadModel`= ; M=`CComMultiThreadModel`

`CComSingleThreadModel`sama definuje tři **názvy typedef.** `ThreadModelNoCS`odkazy `CComSingleThreadModel`. `AutoCriticalSection`a `CriticalSection` referenční třída [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), která poskytuje prázdné metody spojené s získáním a uvolněním vlastnictví kritické části.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="ccomsinglethreadmodelautocriticalsection"></a><a name="autocriticalsection"></a>CcomsingleThreadModel::autokritický oddíl

Při `CComSingleThreadModel`použití název **typedef** `AutoCriticalSection` odkazuje na třídu [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Poznámky

Protože `CComFakeCriticalSection` neposkytuje kritický oddíl, jeho metody nedělají nic.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) a [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) obsahují `AutoCriticalSection`definice pro . V následující tabulce je uvedena relace mezi třídou modelu zřetězení a třídou kritického oddílu, na kterou odkazuje `AutoCriticalSection`:

|Třída definovaná v|Odkazovaná třída|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Kromě `AutoCriticalSection`, můžete použít **název typedef** [CriticalSection](#criticalsection). Pokud chcete `AutoCriticalSection` odstranit spouštěcí kód CRT, neměli byste je určovat v globálních objektech nebo členech statické třídy.

### <a name="example"></a>Příklad

Viz [ccommultithreadmodel::autocriticalsection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="ccomsinglethreadmodelcriticalsection"></a><a name="criticalsection"></a>CcomsingleThreadModel::Kritickýoddíl

Při `CComSingleThreadModel`použití název **typedef** `CriticalSection` odkazuje na třídu [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>Poznámky

Protože `CComFakeCriticalSection` neposkytuje kritický oddíl, jeho metody nedělají nic.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) a [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) obsahují `CriticalSection`definice pro . V následující tabulce je uvedena relace mezi třídou modelu zřetězení a třídou kritického oddílu, na kterou odkazuje `CriticalSection`:

|Třída definovaná v|Odkazovaná třída|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Kromě `CriticalSection`aplikace můžete použít název **typedef** [AutoCriticalSection](#autocriticalsection). Pokud chcete `AutoCriticalSection` odstranit spouštěcí kód CRT, neměli byste je určovat v globálních objektech nebo členech statické třídy.

### <a name="example"></a>Příklad

Viz [ccommultithreadmodel::autocriticalsection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="ccomsinglethreadmodeldecrement"></a><a name="decrement"></a>CComSingleThreadModel::Decrement

Tato statická funkce snižuje hodnotu proměnné, na kterou je odkazováno *písmenem p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
[v] Ukazatel na proměnnou, která má být snížena.

### <a name="return-value"></a>Návratová hodnota

Výsledek snížení.

## <a name="ccomsinglethreadmodelincrement"></a><a name="increment"></a>CComSingleThreadModel::Přírůstek

Tato statická funkce zintálí hodnotu proměnné, na kterou je odkazováno *písmenem p*.

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
[v] Ukazatel na proměnnou, která má být zpřísněna.

### <a name="return-value"></a>Návratová hodnota

Výsledek přírůstku.

## <a name="ccomsinglethreadmodelthreadmodelnocs"></a><a name="threadmodelnocs"></a>CcomsingleThreadModel::ThreadModelNoCS

Při `CComSingleThreadModel`použití název **typedef** `ThreadModelNoCS` jednoduše `CComSingleThreadModel`odkazuje .

```
typedef CComSingleThreadModel ThreadModelNoCS;
```

### <a name="remarks"></a>Poznámky

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) a [CComMultiThreadModelNoCS](../../atl/reference/ccommultithreadmodelnocs-class.md) obsahují `ThreadModelNoCS`definice pro . V následující tabulce je uvedena relace mezi třídou modelu `ThreadModelNoCS`zřetězení a třídou, na kterou odkazuje :

|Třída definovaná v|Odkazovaná třída|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>Příklad

Viz [ccommultithreadmodel::autocriticalsection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
