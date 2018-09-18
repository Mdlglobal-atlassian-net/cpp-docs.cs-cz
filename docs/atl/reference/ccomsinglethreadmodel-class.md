---
title: CComSingleThreadModel – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel
- ATLBASE/ATL::CComSingleThreadModel::AutoCriticalSection
- ATLBASE/ATL::CComSingleThreadModel::CriticalSection
- ATLBASE/ATL::CComSingleThreadModel::ThreadModelNoCS
- ATLBASE/ATL::CComSingleThreadModel::Decrement
- ATLBASE/ATL::CComSingleThreadModel::Increment
dev_langs:
- C++
helpviewer_keywords:
- single-threaded applications
- CComSingleThreadModel class
- single-threaded applications, ATL
ms.assetid: e5dc30c7-405a-4ba4-8ae9-51937243fce8
author: mikeblome
ms.author: mblome
ms.openlocfilehash: b257628747dca488292cfdfff0ef783303bd1b88
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094426"
---
# <a name="ccomsinglethreadmodel-class"></a>CComSingleThreadModel – třída

Tato třída poskytuje metody pro zvyšování a dekrementace hodnotu proměnné.

## <a name="syntax"></a>Syntaxe

```
class CComSingleThreadModel
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|[CComSingleThreadModel::AutoCriticalSection](#autocriticalsection)|Odkazuje na třídu [ccomfakecriticalsection –](../../atl/reference/ccomfakecriticalsection-class.md).|
|[CComSingleThreadModel::CriticalSection](#criticalsection)|Odkazuje na třídu `CComFakeCriticalSection`.|
|[CComSingleThreadModel::ThreadModelNoCS](#threadmodelnocs)|Odkazy na `CComSingleThreadModel`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComSingleThreadModel::Decrement](#decrement)|Sníží hodnotu zadanou proměnnou. Tato implementace není bezpečná pro vlákno.|
|[CComSingleThreadModel::Increment](#increment)|Zvýší hodnotu zadanou proměnnou. Tato implementace není bezpečná pro vlákno.|

## <a name="remarks"></a>Poznámky

`CComSingleThreadModel` poskytuje metody pro zvyšování a dekrementace hodnotu proměnné. Na rozdíl od [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) a [ccommultithreadmodelnocs –](../../atl/reference/ccommultithreadmodelnocs-class.md), tyto metody nejsou bezpečné pro vlákna.  

Obvykle použijete `CComSingleThreadModel` prostřednictvím jednoho ze dvou **typedef** názvy buď [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) nebo [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel). Třída odkazovaná každou **typedef** závisí na model vláken použít, jak je znázorněno v následující tabulce:  

|– definice typedef|Jeden model vláken|Podprocesový model Apartment|Model vláken zdarma|
|-------------|----------------------------|-------------------------------|--------------------------|
|`CComObjectThreadModel`|S|S|M|
|`CComGlobalsThreadModel`|S|M|M|

S = `CComSingleThreadModel`; M = `CComMultiThreadModel`

`CComSingleThreadModel` samotný definuje tři **typedef** názvy. `ThreadModelNoCS` odkazy na `CComSingleThreadModel`. `AutoCriticalSection` a `CriticalSection` referenční třídu [ccomfakecriticalsection –](../../atl/reference/ccomfakecriticalsection-class.md), která poskytuje prázdný metody, které jsou přidružené k získání a uvolnění vlastnictví kritický oddíl.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="autocriticalsection"></a>  CComSingleThreadModel::AutoCriticalSection

Při použití `CComSingleThreadModel`, **typedef** název `AutoCriticalSection` odkazuje na třídu [ccomfakecriticalsection –](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Poznámky

Protože `CComFakeCriticalSection` neposkytuje kritický oddíl, její metody Neprovádět žádnou akci.

[CComMultiThreadModel –](../../atl/reference/ccommultithreadmodel-class.md) a [ccommultithreadmodelnocs –](../../atl/reference/ccommultithreadmodelnocs-class.md) obsahovat definice pro `AutoCriticalSection`. Následující tabulka ukazuje vztah mezi vláken třídy modelu a kritický oddíl odkazuje `AutoCriticalSection`:

|Třída definovaná v|Třída odkazovaná|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Kromě `AutoCriticalSection`, můžete použít **typedef** název [criticalsection –](#criticalsection). Neměli byste zadávat `AutoCriticalSection` v globálních objektů nebo statické členy třídy Pokud budete chtít vyloučit při spuštění kódu CRT.

### <a name="example"></a>Příklad

Zobrazit [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

##  <a name="criticalsection"></a>  CComSingleThreadModel::CriticalSection

Při použití `CComSingleThreadModel`, **typedef** název `CriticalSection` odkazuje na třídu [ccomfakecriticalsection –](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>Poznámky

Protože `CComFakeCriticalSection` neposkytuje kritický oddíl, její metody Neprovádět žádnou akci.

[CComMultiThreadModel –](../../atl/reference/ccommultithreadmodel-class.md) a [ccommultithreadmodelnocs –](../../atl/reference/ccommultithreadmodelnocs-class.md) obsahovat definice pro `CriticalSection`. Následující tabulka ukazuje vztah mezi vláken třídy modelu a kritický oddíl odkazuje `CriticalSection`:

|Třída definovaná v|Třída odkazovaná|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|

Kromě `CriticalSection`, můžete použít **typedef** název [AutoCriticalSection](#autocriticalsection). Neměli byste zadávat `AutoCriticalSection` v globálních objektů nebo statické členy třídy Pokud budete chtít vyloučit při spuštění kódu CRT.

### <a name="example"></a>Příklad

Zobrazit [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

##  <a name="decrement"></a>  CComSingleThreadModel::Decrement

Tato statická funkce sníží hodnotu proměnné, na které odkazuje *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
[in] Ukazatel na proměnnou chcete snížit.

### <a name="return-value"></a>Návratová hodnota

Výsledkem snížení.

##  <a name="increment"></a>  CComSingleThreadModel::Increment

Tato statická funkce sníží hodnotu proměnné, na které odkazuje *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
[in] Ukazatel na proměnnou se zvýší.

### <a name="return-value"></a>Návratová hodnota

Výsledek přírůstku.

##  <a name="threadmodelnocs"></a>  CComSingleThreadModel::ThreadModelNoCS

Při použití `CComSingleThreadModel`, **typedef** název `ThreadModelNoCS` jednoduše odkazuje `CComSingleThreadModel`.

```
typedef CComSingleThreadModel ThreadModelNoCS;
```

### <a name="remarks"></a>Poznámky

[CComMultiThreadModel –](../../atl/reference/ccommultithreadmodel-class.md) a [ccommultithreadmodelnocs –](../../atl/reference/ccommultithreadmodelnocs-class.md) obsahovat definice pro `ThreadModelNoCS`. Následující tabulka ukazuje vztah mezi vláken třídy modelu a odkazuje `ThreadModelNoCS`:

|Třída definovaná v|Třída odkazovaná|
|----------------------|----------------------|
|`CComSingleThreadModel`|`CComSingleThreadModel`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|

### <a name="example"></a>Příklad

Zobrazit [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="see-also"></a>Viz také

[Přehled tříd](../../atl/atl-class-overview.md)
