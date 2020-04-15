---
title: Třída CComMultiThreadModelNoCS
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
ms.openlocfilehash: 4d41ffcfccbd7ef65ed86df79bffec1209a88cd3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81327654"
---
# <a name="ccommultithreadmodelnocs-class"></a>Třída CComMultiThreadModelNoCS

`CComMultiThreadModelNoCS`poskytuje metody bezpečné pro přístup z více vláken pro zvýšení a snížení hodnoty proměnné, bez kritického oddílu uzamčení nebo odemykání funkce.

## <a name="syntax"></a>Syntaxe

```
class CComMultiThreadModelNoCS
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

|Name (Název)|Popis|
|----------|-----------------|
|[CcomMultiThreadModelNoCS::Autokritický oddíl](#autocriticalsection)|Reference třídy [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).|
|[CcomMultiThreadModelNoCS::Kritickýoddíl](#criticalsection)|Třída Reference `CComFakeCriticalSection`.|
|[CcomMultiThreadModelNoCS::ThreadModelNoCS](#threadmodelnocs)|Třída Reference `CComMultiThreadModelNoCS`.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[CComMultiThreadModelNoCS::Decrement](#decrement)|(Statické) Sníží hodnotu zadané proměnné způsobem bezpečným pro přístup z více vláken.|
|[CComMultiThreadModelNoCS::Přírůstek](#increment)|(Statické) Zintáží hodnotu zadané proměnné způsobem bezpečným pro přístup z více vláken.|

## <a name="remarks"></a>Poznámky

`CComMultiThreadModelNoCS`je podobný [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) v tom, že poskytuje metody bezpečné pro přístup z více vláken pro zvýšení a snížení proměnné. Však při odkazování na `CComMultiThreadModelNoCS`třídu kritické `Lock` `Unlock` části prostřednictvím , metody, jako je například a nebude dělat nic.

Obvykle se používá `CComMultiThreadModelNoCS` prostřednictvím `ThreadModelNoCS` **typedef** název. Tento **typedef** je `CComMultiThreadModelNoCS` `CComMultiThreadModel`definován v , , a [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md).

> [!NOTE]
> Globální **typedef** názvy [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) a [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel) neodkazují `CComMultiThreadModelNoCS`.

Kromě `ThreadModelNoCS`, `CComMultiThreadModelNoCS` definuje `AutoCriticalSection` a `CriticalSection`. Tyto poslední dva **názvy typedef** odkaz [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md), který poskytuje prázdné metody spojené s získání a uvolnění kritické části.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="ccommultithreadmodelnocsautocriticalsection"></a><a name="autocriticalsection"></a>CcomMultiThreadModelNoCS::Autokritický oddíl

Při `CComMultiThreadModelNoCS`použití název **typedef** `AutoCriticalSection` odkazuje na třídu [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Poznámky

Protože `CComFakeCriticalSection` neposkytuje kritický oddíl, jeho metody nedělají nic.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) a [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) také `AutoCriticalSection`obsahují definice pro . V následující tabulce je uvedena relace mezi třídou modelu zřetězení a třídou kritického oddílu, na kterou odkazuje `AutoCriticalSection`:

|Třída definovaná v|Odkazovaná třída|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

Kromě `AutoCriticalSection`, můžete použít **název typedef** [CriticalSection](#criticalsection). Pokud chcete `AutoCriticalSection` odstranit spouštěcí kód CRT, neměli byste je určovat v globálních objektech nebo členech statické třídy.

### <a name="example"></a>Příklad

Viz [ccommultithreadmodel::autocriticalsection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="ccommultithreadmodelnocscriticalsection"></a><a name="criticalsection"></a>CcomMultiThreadModelNoCS::Kritickýoddíl

Při `CComMultiThreadModelNoCS`použití název **typedef** `CriticalSection` odkazuje na třídu [CComFakeCriticalSection](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>Poznámky

Protože `CComFakeCriticalSection` neposkytuje kritický oddíl, jeho metody nedělají nic.

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) a [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) také `CriticalSection`obsahují definice pro . V následující tabulce je uvedena relace mezi třídou modelu zřetězení a třídou kritického oddílu, na kterou odkazuje `CriticalSection`:

|Třída definovaná v|Odkazovaná třída|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

Kromě `CriticalSection`, můžete použít **název** `AutoCriticalSection`typedef . Pokud chcete `AutoCriticalSection` odstranit spouštěcí kód CRT, neměli byste je určovat v globálních objektech nebo členech statické třídy.

### <a name="example"></a>Příklad

Viz [ccommultithreadmodel::autocriticalsection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="ccommultithreadmodelnocsdecrement"></a><a name="decrement"></a>CComMultiThreadModelNoCS::Decrement

Tato statická funkce volá win32 funkce [InterlockedDecrement](/windows/win32/api/winnt/nf-winnt-interlockeddecrement), která snižuje hodnotu proměnné, na kterou se vztahuje *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
[v] Ukazatel na proměnnou, která má být snížena.

### <a name="return-value"></a>Návratová hodnota

Pokud je výsledek snížení 0, vrátí `Decrement` 0. Pokud je výsledek snížení nenulová, vrácená hodnota je také nenulová, ale nemusí se rovnat výsledku snížení.

### <a name="remarks"></a>Poznámky

**InterlockedDecrement** zabraňuje více než jedno vlákno současně pomocí této proměnné.

## <a name="ccommultithreadmodelnocsincrement"></a><a name="increment"></a>CComMultiThreadModelNoCS::Přírůstek

Tato statická funkce volá win32 funkce [InterlockedIncrement](/windows/win32/api/winnt/nf-winnt-interlockedincrement), která zintálí hodnotu proměnné, na kterou je odkazováno *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>Parametry

*P*<br/>
[v] Ukazatel na proměnnou, která má být zpřísněna.

### <a name="return-value"></a>Návratová hodnota

Pokud je výsledek přírůstku 0, vrátí **funkce Přírůstek** 0. Pokud je výsledek přírůstku nenulový, vrácená hodnota je také nenulová, ale nemusí se rovnat výsledku přírůstku.

### <a name="remarks"></a>Poznámky

**InterlockedIncrement** zabraňuje více než jeden podproces současně pomocí této proměnné.

## <a name="ccommultithreadmodelnocsthreadmodelnocs"></a><a name="threadmodelnocs"></a>CcomMultiThreadModelNoCS::ThreadModelNoCS

Při `CComMultiThreadModelNoCS`použití název **typedef** `ThreadModelNoCS` jednoduše `CComMultiThreadModelNoCS`odkazuje .

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>Poznámky

[CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) a [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) také `ThreadModelNoCS`obsahují definice pro . V následující tabulce je uvedena relace mezi třídou modelu `ThreadModelNoCS`zřetězení a třídou, na kterou odkazuje :

|Třída definovaná v|Odkazovaná třída|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|

Všimněte si, `ThreadModelNoCS` `CComMultiThreadModelNoCS` že definice `CComMultiThreadModel` in `CComSingleThreadModel`poskytuje symetrii s a . Předpokládejme například ukázkový `CComMultiThreadModel::AutoCriticalSection` kód v deklarované matné **funkce typedef**:

[!code-cpp[NVC_ATL_COM#37](../../atl/codesnippet/cpp/ccommultithreadmodelnocs-class_1.h)]

Bez ohledu na třídu zadanou pro `ThreadModel` (například `CComMultiThreadModelNoCS`), `_ThreadModel` řeší odpovídajícím způsobem.

### <a name="example"></a>Příklad

Viz [ccommultithreadmodel::autocriticalsection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="see-also"></a>Viz také

[Přehled třídy](../../atl/atl-class-overview.md)
