---
title: tile_barrier – třída
ms.date: 03/27/2019
f1_keywords:
- tile_barrier
- AMP/tile_barrier
- AMP/Concurrency::tile_barrier::tile_barrier::tile_barrier
- AMP/Concurrency::tile_barrier::tile_barrier::wait
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_all_memory_fence
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_global_memory_fence
- AMP/Concurrency::tile_barrier::tile_barrier::wait_with_tile_static_memory_fence
helpviewer_keywords:
- tile_barrier class
ms.assetid: b4ccdccb-0032-4e11-b7bd-dc9d43445dee
ms.openlocfilehash: c00f1e41e70e723be185959eeff176390def7647
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374728"
---
# <a name="tile_barrier-class"></a>tile_barrier – třída

Synchronizuje provádění podprocesů, které jsou spuštěny ve skupině `wait` vláken (dlaždice) pomocí metod. Pouze runtime můžete vytvořit instanci této třídy.

## <a name="syntax"></a>Syntaxe

```cpp
class tile_barrier;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[konstruktor tile_barrier](#ctor)|Inicializuje novou instanci třídy. `tile_barrier`|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[Počkej](#wait)|Instruuje všechna vlákna ve skupině vláken (dlaždice) zastavit provádění, dokud všechna vlákna v dlaždici dokončili čekání.|
|[wait_with_all_memory_fence](#wait_with_all_memory_fence)|Blokuje provádění všech podprocesů v dlaždici, dokud všechny přístupy do paměti byly dokončeny a všechna vlákna v dlaždici dosáhly tohoto volání.|
|[wait_with_global_memory_fence](#wait_with_global_memory_fence)|Blokuje provádění všech podprocesů v dlaždici, dokud všechny přístupy globální paměti byly dokončeny a všechna vlákna v dlaždici dosáhly tohoto volání.|
|[wait_with_tile_static_memory_fence](#wait_with_tile_static_memory_fence)|Blokuje provádění všech podprocesů v `tile_static` dlaždici, dokud všechny přístupy do paměti byly dokončeny a všechna vlákna v dlaždici dosáhly tohoto volání.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`tile_barrier`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp.h

**Obor názvů:** Souběžnost

## <a name="tile_barrier-constructor"></a><a name="ctor"></a>konstruktor tile_barrier

Inicializuje novou instanci třídy zkopírováním existující instance.

### <a name="syntax"></a>Syntaxe

```cpp
tile_barrier(
    const tile_barrier& _Other ) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Objekt, `tile_barrier` který chcete zkopírovat.

## <a name="wait"></a>Počkej

Instruuje všechna vlákna ve skupině vláken (dlaždice) zastavit provádění, dokud všechna vlákna v dlaždici dokončili čekání.

### <a name="syntax"></a>Syntaxe

```cpp
void wait() const restrict(amp);
```

## <a name="wait_with_all_memory_fence"></a><a name="wait_with_all_memory_fence"></a>wait_with_all_memory_fence

Blokuje provádění všech podprocesů v dlaždici, dokud všechna vlákna v dlaždici nedosáhly tohoto volání. Tím je zajištěno, že všechny přístupy k paměti jsou viditelné pro ostatní vlákna v dlaždici vlákna a byly provedeny v pořadí programu.

### <a name="syntax"></a>Syntaxe

```cpp
void wait_with_all_memory_fence() const restrict(amp);
```

## <a name="a-namewait_with_global_memory_fence-wait_with_global_memory_fence"></a><a name="wait_with_global_memory_fence">wait_with_global_memory_fence

Blokuje provádění všech podprocesů v dlaždici, dokud všechna vlákna v dlaždici nedosáhly tohoto volání. Tím je zajištěno, že všechny přístupy globální paměti jsou viditelné pro ostatní vlákna v dlaždici vlákna a byly provedeny v pořadí programu.

### <a name="syntax"></a>Syntaxe

```cpp
void wait_with_global_memory_fence() const  restrict(amp);
```

## <a name="a-namewait_with_tile_static_memory_fence-wait_with_tile_static_memory_fence"></a><a name="wait_with_tile_static_memory_fence">wait_with_tile_static_memory_fence

Blokuje provádění všech podprocesů v dlaždici, dokud všechna vlákna v dlaždici nedosáhly tohoto volání. Tím je `tile_static` zajištěno, že přístupy k paměti jsou viditelné pro ostatní vlákna v dlaždici vlákna a byly provedeny v pořadí programu.

### <a name="syntax"></a>Syntaxe

```cpp
void wait_with_tile_static_memory_fence() const restrict(amp);
```

## <a name="see-also"></a>Viz také

[Obor názvů souběžnosti (C++ AMP)](concurrency-namespace-cpp-amp.md)
