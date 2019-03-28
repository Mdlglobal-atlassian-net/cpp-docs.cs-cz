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
ms.openlocfilehash: f0e742a0cc1a0809fc08b3862cadb7e3deb36fa8
ms.sourcegitcommit: 309dc532f13242854b47759cef846de59bb807f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/28/2019
ms.locfileid: "58564980"
---
# <a name="tilebarrier-class"></a>tile_barrier – třída

Synchronizuje provádění vláken spuštěných ve skupině vláken (bloku) pomocí `wait` metody. Pouze modul runtime lze vytvořit instanci této třídy.

### <a name="syntax"></a>Syntaxe

```
class tile_barrier;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[tile_barrier – konstruktor](#ctor)|Inicializuje novou instanci třídy `tile_barrier` třídy.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[Počkej](#wait)|Nařídí všem vláknům ve skupině vláken (bloku) pozastavit spuštění, dokud všechna vlákna v bloku nedokončila čekání.|
|[wait_with_all_memory_fence](#wait_with_all_memory_fence)|Pozastaví spuštění všech vláken v dlaždici, dokud nejsou dokončeny všechny přístupy do paměti a dokud všechna vlákna v dlaždici nedosáhnou tohoto volání.|
|[wait_with_global_memory_fence](#wait_with_global_memory_fence)|Pozastaví spuštění všech vláken v dlaždici, dokud nejsou dokončeny všechny přístupy do globální paměti a všechna vlákna v dlaždici nedosáhnou tohoto volání.|
|[wait_with_tile_static_memory_fence](#wait_with_tile_static_memory_fence)|Pozastaví spuštění všech vláken v dlaždici, dokud všichni `tile_static` nejsou dokončeny přístupy do paměti a všechna vlákna v dlaždici nedosáhnou tohoto volání.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`tile_barrier`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amp.h

**Namespace:** Souběžnost

## <a name="ctor"></a>  tile_barrier – konstruktor

Inicializuje novou instanci třídy zkopírováním existující.

### <a name="syntax"></a>Syntaxe

```
tile_barrier(
    const tile_barrier& _Other ) restrict(amp,cpu);
```

### <a name="parameters"></a>Parametry

*Ji_né*<br/>
`tile_barrier` Objektu, který chcete zkopírovat.

## <a name="wait"></a>Počkej

Nařídí všem vláknům ve skupině vláken (bloku) pro zastavení provádění, dokud všechna vlákna v bloku nedokončila čekání.

### <a name="syntax"></a>Syntaxe

```
void wait() const restrict(amp);
```

## <a name="waitwithallmemoryfence"></a>wait_with_all_memory_fence

Pozastaví spuštění všech vláken v dlaždici, dokud všechna vlákna v dlaždici nedosáhnou tohoto volání. Tím se zajistí, že všechny přístupy do paměti viditelné pro ostatní vlákna v dlaždici vlákna a že byly provedeny v pořadí programu.

### <a name="syntax"></a>Syntaxe

```
void wait_with_all_memory_fence() const restrict(amp);
```

## <a name="waitwithglobalmemoryfence"></a>wait_with_global_memory_fence –

Pozastaví spuštění všech vláken v dlaždici, dokud všechna vlákna v dlaždici nedosáhnou tohoto volání. Tím se zajistí, že všechny přístupy do globální paměti viditelné pro ostatní vlákna v dlaždici vlákna a že byly provedeny v pořadí programu.

### <a name="syntax"></a>Syntaxe

```
void wait_with_global_memory_fence() const  restrict(amp);
```

## <a name="waitwithtilestaticmemoryfence"></a>wait_with_tile_static_memory_fence

Pozastaví spuštění všech vláken v dlaždici, dokud všechna vlákna v dlaždici nedosáhnou tohoto volání. To zajistí, že `tile_static` paměti přístupy jsou viditelné pro ostatní vlákna v dlaždici vlákna a že byly provedeny v pořadí programu.

### <a name="syntax"></a>Syntaxe

```
void wait_with_tile_static_memory_fence() const restrict(amp);
```

## <a name="see-also"></a>Viz také:

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
