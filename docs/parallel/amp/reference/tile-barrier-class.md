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
ms.openlocfilehash: 757309a10da3e6d1c9c053430cce2cf603380b1f
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422281"
---
# <a name="tile_barrier-class"></a>tile_barrier – třída

Synchronizuje spuštění vláken, která běží ve skupině vláken (dlaždice) pomocí metod `wait`. Pouze modul runtime může vytvořit instanci této třídy.

## <a name="syntax"></a>Syntaxe

```cpp
class tile_barrier;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[tile_barrier – konstruktor](#ctor)|Inicializuje novou instanci třídy `tile_barrier`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[Počkej](#wait)|Instruuje všechna vlákna ve skupině vláken (dlaždice), aby ukončila provádění, dokud všechna vlákna v dlaždici nedokončí čekání.|
|[wait_with_all_memory_fence](#wait_with_all_memory_fence)|Blokuje spuštění všech vláken v dlaždici, dokud nejsou dokončeny všechny přístupy do paměti a všechna vlákna v dlaždici dosáhla tohoto volání.|
|[wait_with_global_memory_fence](#wait_with_global_memory_fence)|Blokuje spuštění všech vláken v dlaždici, dokud nejsou dokončeny všechny přístupy do globální paměti, a všechna vlákna v dlaždici dosáhla tohoto volání.|
|[wait_with_tile_static_memory_fence](#wait_with_tile_static_memory_fence)|Blokuje spuštění všech vláken v dlaždici, dokud nejsou dokončeny všechny přístupy do `tile_static` paměti, a všechna vlákna v dlaždici dosáhla tohoto volání.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`tile_barrier`

## <a name="requirements"></a>Požadavky

**Hlavička:** amp. h

**Obor názvů:** Concurrency

## <a name="ctor"></a>tile_barrier – konstruktor

Inicializuje novou instanci třídy zkopírováním existujícího objektu.

### <a name="syntax"></a>Syntaxe

```cpp
tile_barrier(
    const tile_barrier& _Other ) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*_Other*<br/>
Objekt `tile_barrier` ke zkopírování.

## <a name="wait"></a>Počkej

Instruuje všechna vlákna ve skupině vláken (dlaždice), aby ukončila provádění, dokud všechna vlákna v dlaždici nedokončí čekání.

### <a name="syntax"></a>Syntaxe

```cpp
void wait() const restrict(amp);
```

## <a name="wait_with_all_memory_fence"></a>wait_with_all_memory_fence

Blokuje spuštění všech vláken v dlaždici, dokud všechna vlákna v dlaždici nedosáhnou tohoto volání. Tím zajistíte, že všechny přístupy do paměti jsou viditelné pro ostatní vlákna v dlaždici vlákna a že byly provedeny v pořadí programu.

### <a name="syntax"></a>Syntaxe

```cpp
void wait_with_all_memory_fence() const restrict(amp);
```

## <a name="a-namewait_with_global_memory_fence-wait_with_global_memory_fence"></a><a name="wait_with_global_memory_fence"> wait_with_global_memory_fence

Blokuje spuštění všech vláken v dlaždici, dokud všechna vlákna v dlaždici nedosáhnou tohoto volání. Tím se zajistí, že všechny přístupy do globální paměti jsou viditelné pro ostatní vlákna v dlaždici vlákna a že byly provedeny v pořadí programu.

### <a name="syntax"></a>Syntaxe

```cpp
void wait_with_global_memory_fence() const  restrict(amp);
```

## <a name="a-namewait_with_tile_static_memory_fence-wait_with_tile_static_memory_fence"></a><a name="wait_with_tile_static_memory_fence"> wait_with_tile_static_memory_fence

Blokuje spuštění všech vláken v dlaždici, dokud všechna vlákna v dlaždici nedosáhnou tohoto volání. Tím se zajistí, že přístup k `tile_static` paměti je viditelný pro ostatní vlákna v dlaždici vlákna a že byly provedeny v pořadí programu.

### <a name="syntax"></a>Syntaxe

```cpp
void wait_with_tile_static_memory_fence() const restrict(amp);
```

## <a name="see-also"></a>Viz také

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
