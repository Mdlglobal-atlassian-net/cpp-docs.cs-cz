---
title: MakeAllocator – třída
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::MakeAllocator
- implements/Microsoft::WRL::Details::MakeAllocator::Allocate
- implements/Microsoft::WRL::Details::MakeAllocator::Detach
- implements/Microsoft::WRL::Details::MakeAllocator::MakeAllocator
- implements/Microsoft::WRL::Details::MakeAllocator::~MakeAllocator
helpviewer_keywords:
- Microsoft::WRL::Details::MakeAllocator class
- Microsoft::WRL::Details::MakeAllocator::Allocate method
- Microsoft::WRL::Details::MakeAllocator::Detach method
- Microsoft::WRL::Details::MakeAllocator::MakeAllocator, constructor
- Microsoft::WRL::Details::MakeAllocator::~MakeAllocator, destructor
ms.assetid: a1114615-abd7-4a56-9bc3-750c118f0fa1
ms.openlocfilehash: 805f0c09b0490d8cec1a0be96dcb1fc99a051371
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334685"
---
# <a name="makeallocator-class"></a>MakeAllocator – třída

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
template<
    typename T,
    bool hasWeakReferenceSupport =
          !__is_base_of(RuntimeClassFlags<InhibitWeakReference>,
                        T)
>
class MakeAllocator;

template<typename T>
class MakeAllocator<T, false>;

template<typename T>
class MakeAllocator<T, true>;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Název typu.

*hasWeakReferenceSupport*<br/>
**Hodnota TRUE** přidělení paměti pro objekt, který podporuje slabé odkazy; **false** přidělení paměti pro objekt, který nepodporuje slabé odkazy.

## <a name="remarks"></a>Poznámky

Přiděluje paměť pro aktivovatelné třídy s nebo bez něj slabou podporu odkazu.

Přepsat `MakeAllocator` třídu pro implementaci modelu přidělování paměti definované uživatelem.

`MakeAllocator` se obvykle používá pro zabránění nevracení paměti, pokud objekt vyvolá během konstrukce.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Název                                                  | Popis
----------------------------------------------------- | ----------------------------------------------------------------
[MakeAllocator::MakeAllocator](#makeallocator)        | Inicializuje novou instanci třídy `MakeAllocator` třídy.
[MakeAllocator::~MakeAllocator](#tilde-makeallocator) | Zruší inicializaci aktuální instance `MakeAllocator` třídy.

### <a name="public-methods"></a>Veřejné metody

Název                                 | Popis
------------------------------------ | -----------------------------------------------------------------------------------------------------------
[Makeallocator::allocate –](#allocate) | Přidělí paměť a přidruží ji k aktuální `MakeAllocator` objektu.
[MakeAllocator::Detach](#detach)     | Zruší přidružení paměť přidělenou [přidělení](#allocate) metodu z aktuální `MakeAllocator` objektu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`MakeAllocator`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="allocate"></a>Makeallocator::allocate –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
__forceinline void* Allocate();
```

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, ukazatel do přidělené paměti. v opačném případě `nullptr`.

### <a name="remarks"></a>Poznámky

Přidělí paměť a přidruží ji k aktuální `MakeAllocator` objektu.

Velikost přidělené paměti je velikost typu určeného aktuálním `MakeAllocator` parametr šablony.

Vývojář potřebuje pouze přepsat `Allocate()` metody k implementaci modelu přidělování různých paměti.

## <a name="detach"></a>MakeAllocator::Detach

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
__forceinline void Detach();
```

### <a name="remarks"></a>Poznámky

Zruší přidružení paměť přidělenou [přidělení](#allocate) metodu z aktuální `MakeAllocator` objektu.

Při volání `Detach()`, zodpovídáte za odstranění paměti poskytované `Allocate` metody.

## <a name="makeallocator"></a>Makeallocator::makeallocator –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
MakeAllocator();
```

### <a name="remarks"></a>Poznámky

Inicializuje novou instanci třídy `MakeAllocator` třídy.

## <a name="tilde-makeallocator"></a>MakeAllocator:: ~ makeallocator –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
~MakeAllocator();
```

### <a name="remarks"></a>Poznámky

Zruší inicializaci aktuální instance `MakeAllocator` třídy.

V případě potřeby se tento destruktor odstraní také základní přidělené paměti.