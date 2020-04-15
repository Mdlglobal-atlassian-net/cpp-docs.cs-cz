---
title: out_of_memory – třída
ms.date: 11/04/2016
f1_keywords:
- out_of_memory
- AMPRT/out_of_memory
- AMPRT/Concurrency::out_of_memory::out_of_memory
helpviewer_keywords:
- out_of_memory class
ms.assetid: 3aa7e682-8f13-4ae6-9188-31fb423956e4
ms.openlocfilehash: e716d4952bdb9634cc0d195285d3a65c5c06b0a1
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336808"
---
# <a name="out_of_memory-class"></a>out_of_memory – třída

Výjimka, která je vyvolána při selhání metody z důvodu nedostatku systémové nebo paměti zařízení.

## <a name="syntax"></a>Syntaxe

```cpp
class out_of_memory : public runtime_exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[konstruktor out_of_memory](#ctor)|Inicializuje novou instanci třídy. `out_of_memory`|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`runtime_exception`

`out_of_memory`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amprt.h

**Obor názvů:** Souběžnost

## <a name="out_of_memory"></a><a name="ctor"></a>out_of_memory

Inicializuje novou instanci třídy.

### <a name="syntax"></a>Syntaxe

```cpp
explicit out_of_memory(
    const char * _Message ) throw();

out_of_memory () throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popis chyby.

### <a name="return-value"></a>Návratová hodnota

Nová instance třídy. `out_of_memory`

## <a name="see-also"></a>Viz také

[Obor názvů souběžnosti (C++ AMP)](concurrency-namespace-cpp-amp.md)
