---
title: Ccommultithreadmodelnocs – třída
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
ms.openlocfilehash: ef2038a203b6cbfb2564bbe11d508ee43df0fd1b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62259219"
---
# <a name="ccommultithreadmodelnocs-class"></a>Ccommultithreadmodelnocs – třída

`CComMultiThreadModelNoCS` poskytuje metody bezpečným pro vlákno pro zvyšování a dekrementace hodnotu proměnné, bez kritický oddíl zamykání a odemykání funkce.

## <a name="syntax"></a>Syntaxe

```
class CComMultiThreadModelNoCS
```

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

|Název|Popis|
|----------|-----------------|
|[CComMultiThreadModelNoCS::AutoCriticalSection](#autocriticalsection)|Odkazuje na třídu [ccomfakecriticalsection –](../../atl/reference/ccomfakecriticalsection-class.md).|
|[CComMultiThreadModelNoCS::CriticalSection](#criticalsection)|Odkazuje na třídu `CComFakeCriticalSection`.|
|[CComMultiThreadModelNoCS::ThreadModelNoCS](#threadmodelnocs)|Odkazuje na třídu `CComMultiThreadModelNoCS`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[CComMultiThreadModelNoCS::Decrement](#decrement)|(Statické) Sníží hodnotu zadanou proměnnou způsobem bezpečným pro vlákno.|
|[CComMultiThreadModelNoCS::Increment](#increment)|(Statické) Zvýší hodnotu zadanou proměnnou způsobem bezpečným pro vlákno.|

## <a name="remarks"></a>Poznámky

`CComMultiThreadModelNoCS` je podobný [CComMultiThreadModel](../../atl/reference/ccommultithreadmodel-class.md) v tom, že poskytuje bezpečným pro vlákno metody pro zvyšování a dekrementace proměnné. Ale při odkazu na třídu kritický oddíl prostřednictvím `CComMultiThreadModelNoCS`, metody, jako `Lock` a `Unlock` Neprovádět žádnou akci.

Obvykle použijete `CComMultiThreadModelNoCS` prostřednictvím `ThreadModelNoCS` **typedef** název. To **typedef** je definována v `CComMultiThreadModelNoCS`, `CComMultiThreadModel`, a [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md).

> [!NOTE]
>  Globální **typedef** názvy [CComObjectThreadModel](atl-typedefs.md#ccomobjectthreadmodel) a [CComGlobalsThreadModel](atl-typedefs.md#ccomglobalsthreadmodel) Neodkazovat `CComMultiThreadModelNoCS`.

Kromě `ThreadModelNoCS`, `CComMultiThreadModelNoCS` definuje `AutoCriticalSection` a `CriticalSection`. Těchto dvou **– typedef** referenční názvy [ccomfakecriticalsection –](../../atl/reference/ccomfakecriticalsection-class.md), která poskytuje prázdný metody, které jsou přidružené k získání a uvolnění kritický oddíl.

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="autocriticalsection"></a>  CComMultiThreadModelNoCS::AutoCriticalSection

Při použití `CComMultiThreadModelNoCS`, **typedef** název `AutoCriticalSection` odkazuje na třídu [ccomfakecriticalsection –](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection AutoCriticalSection;
```

### <a name="remarks"></a>Poznámky

Protože `CComFakeCriticalSection` neposkytuje kritický oddíl, její metody Neprovádět žádnou akci.

[CComMultiThreadModel –](../../atl/reference/ccommultithreadmodel-class.md) a [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) také obsahovat definice pro `AutoCriticalSection`. Následující tabulka ukazuje vztah mezi vláken třídy modelu a kritický oddíl odkazuje `AutoCriticalSection`:

|Třída definovaná v|Třída odkazovaná|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComAutoCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

Kromě `AutoCriticalSection`, můžete použít **typedef** název [criticalsection –](#criticalsection). Neměli byste zadávat `AutoCriticalSection` v globálních objektů nebo statické členy třídy Pokud budete chtít vyloučit při spuštění kódu CRT.

### <a name="example"></a>Příklad

Zobrazit [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

##  <a name="criticalsection"></a>  CComMultiThreadModelNoCS::CriticalSection

Při použití `CComMultiThreadModelNoCS`, **typedef** název `CriticalSection` odkazuje na třídu [ccomfakecriticalsection –](../../atl/reference/ccomfakecriticalsection-class.md).

```
typedef CComFakeCriticalSection CriticalSection;
```

### <a name="remarks"></a>Poznámky

Protože `CComFakeCriticalSection` neposkytuje kritický oddíl, její metody Neprovádět žádnou akci.

[CComMultiThreadModel –](../../atl/reference/ccommultithreadmodel-class.md) a [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) také obsahovat definice pro `CriticalSection`. Následující tabulka ukazuje vztah mezi vláken třídy modelu a kritický oddíl odkazuje `CriticalSection`:

|Třída definovaná v|Třída odkazovaná|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComFakeCriticalSection`|
|`CComMultiThreadModel`|`CComCriticalSection`|
|`CComSingleThreadModel`|`CComFakeCriticalSection`|

Kromě `CriticalSection`, můžete použít **typedef** název `AutoCriticalSection`. Neměli byste zadávat `AutoCriticalSection` v globálních objektů nebo statické členy třídy Pokud budete chtít vyloučit při spuštění kódu CRT.

### <a name="example"></a>Příklad

Zobrazit [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

##  <a name="decrement"></a>  CComMultiThreadModelNoCS::Decrement

Tato statická funkce volá funkci Win32 [InterlockedDecrement](/windows/desktop/api/winnt/nf-winnt-interlockeddecrement), které sníží hodnotu proměnné, na které odkazuje *p*.

```
static ULONG WINAPI Decrement(LPLONG p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
[in] Ukazatel na proměnnou chcete snížit.

### <a name="return-value"></a>Návratová hodnota

Pokud výsledek snížení je 0, `Decrement` vrátí hodnotu 0. Pokud je výsledkem snížení nenulovou hodnotu, návratová hodnota je také nenulovou hodnotu, ale nemusí být roven výsledku snížení.

### <a name="remarks"></a>Poznámky

**InterlockedDecrement** zabrání současně pomocí této proměnné více než jedno vlákno.

##  <a name="increment"></a>  CComMultiThreadModelNoCS::Increment

Tato statická funkce volá funkci Win32 [InterlockedIncrement](/windows/desktop/api/winnt/nf-winnt-interlockedincrement), který zvýší hodnotu proměnné, na které odkazuje *p*.

```
static ULONG WINAPI Increment(LPLONG p) throw();
```

### <a name="parameters"></a>Parametry

*p*<br/>
[in] Ukazatel na proměnnou se zvýší.

### <a name="return-value"></a>Návratová hodnota

Pokud výsledek přírůstek je 0, **přírůstek** vrátí hodnotu 0. Pokud je výsledkem přírůstku nenulovou hodnotu, návratová hodnota je také nenulovou hodnotu, ale nesmí být roven výsledku přírůstku.

### <a name="remarks"></a>Poznámky

**InterlockedIncrement** zabrání současně pomocí této proměnné více než jedno vlákno.

##  <a name="threadmodelnocs"></a>  CComMultiThreadModelNoCS::ThreadModelNoCS

Při použití `CComMultiThreadModelNoCS`, **typedef** název `ThreadModelNoCS` jednoduše odkazuje `CComMultiThreadModelNoCS`.

```
typedef CComMultiThreadModelNoCS ThreadModelNoCS;
```

### <a name="remarks"></a>Poznámky

[CComMultiThreadModel –](../../atl/reference/ccommultithreadmodel-class.md) a [CComSingleThreadModel](../../atl/reference/ccomsinglethreadmodel-class.md) také obsahovat definice pro `ThreadModelNoCS`. Následující tabulka ukazuje vztah mezi vláken třídy modelu a odkazuje `ThreadModelNoCS`:

|Třída definovaná v|Třída odkazovaná|
|----------------------|----------------------|
|`CComMultiThreadModelNoCS`|`CComMultiThreadModelNoCS`|
|`CComMultiThreadModel`|`CComMultiThreadModelNoCS`|
|`CComSingleThreadModel`|`CComSingleThreadModel`|

Všimněte si, že definice `ThreadModelNoCS` v `CComMultiThreadModelNoCS` zajišťuje symetrii s `CComMultiThreadModel` a `CComSingleThreadModel`. Předpokládejme například, ukázkový kód v `CComMultiThreadModel::AutoCriticalSection` deklarovány následující **typedef**:

[!code-cpp[NVC_ATL_COM#37](../../atl/codesnippet/cpp/ccommultithreadmodelnocs-class_1.h)]

Bez ohledu na to třída zadaná pro `ThreadModel` (například `CComMultiThreadModelNoCS`), `_ThreadModel` řeší odpovídajícím způsobem.

### <a name="example"></a>Příklad

Zobrazit [CComMultiThreadModel::AutoCriticalSection](../../atl/reference/ccommultithreadmodel-class.md#autocriticalsection).

## <a name="see-also"></a>Viz také:

[Přehled tříd](../../atl/atl-class-overview.md)
