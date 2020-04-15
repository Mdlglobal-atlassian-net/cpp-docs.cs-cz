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
ms.openlocfilehash: dc0d83f2550646572a4eff2bec7850037c6dbf6a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81371326"
---
# <a name="makeallocator-class"></a>MakeAllocator – třída

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

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
**true** přidělit paměť pro objekt, který podporuje slabé odkazy; **false** přidělit paměť pro objekt, který nepodporuje slabé odkazy.

## <a name="remarks"></a>Poznámky

Přiděluje paměť pro aktivovatelnou třídu, se slabou referenční podporou nebo bez ní.

Přepište `MakeAllocator` třídu a implementujte uživatelem definovaný model přidělení paměti.

`MakeAllocator`se obvykle používá k zabránění nevracení paměti, pokud objekt vyvolá během výstavby.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Name (Název)                                                  | Popis
----------------------------------------------------- | ----------------------------------------------------------------
[MakeAllocator::MakeAllocator](#makeallocator)        | Inicializuje novou instanci třídy. `MakeAllocator`
[MakeAllocator::~MakeAllocator](#tilde-makeallocator) | Deinitializes aktuální instance `MakeAllocator` třídy.

### <a name="public-methods"></a>Veřejné metody

Name (Název)                                 | Popis
------------------------------------ | -----------------------------------------------------------------------------------------------------------
[MakeAllocator::Přidělit](#allocate) | Přidělí paměť a přidruží ji k aktuálnímu `MakeAllocator` objektu.
[MakeAllocator::Detach](#detach)     | Zruší přidružení paměti přidělené metodou [Allocate](#allocate) od `MakeAllocator` aktuálního objektu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`MakeAllocator`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Obor názvů:** Microsoft::WRL::Details

## <a name="makeallocatorallocate"></a><a name="allocate"></a>MakeAllocator::Přidělit

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
__forceinline void* Allocate();
```

### <a name="return-value"></a>Návratová hodnota

Pokud je úspěšná, ukazatel na přidělenou paměť; v `nullptr`opačném případě .

### <a name="remarks"></a>Poznámky

Přidělí paměť a přidruží ji k aktuálnímu `MakeAllocator` objektu.

Velikost přidělené paměti je velikost typu určeného aktuálním `MakeAllocator` parametrem šablony.

Vývojář musí přepsat pouze `Allocate()` metodu k implementaci jiného modelu přidělení paměti.

## <a name="makeallocatordetach"></a><a name="detach"></a>MakeAllocator::Detach

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
__forceinline void Detach();
```

### <a name="remarks"></a>Poznámky

Zruší přidružení paměti přidělené metodou [Allocate](#allocate) od `MakeAllocator` aktuálního objektu.

Pokud zavoláte `Detach()`, jste zodpovědní za odstranění paměti `Allocate` poskytované metodou.

## <a name="makeallocatormakeallocator"></a><a name="makeallocator"></a>MakeAllocator::MakeAllocator

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
MakeAllocator();
```

### <a name="remarks"></a>Poznámky

Inicializuje novou instanci třídy. `MakeAllocator`

## <a name="makeallocatormakeallocator"></a><a name="tilde-makeallocator"></a>MakeAllocator::~MakeAllocator

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
~MakeAllocator();
```

### <a name="remarks"></a>Poznámky

Deinitializes aktuální instance `MakeAllocator` třídy.

Tento destruktor také v případě potřeby odstraní podkladovou přidělenou paměť.
