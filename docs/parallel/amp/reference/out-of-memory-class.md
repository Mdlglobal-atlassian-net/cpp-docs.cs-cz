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
ms.openlocfilehash: 4edc1db3c1a70a41f9a0493bd3dc484e27f99b44
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126445"
---
# <a name="out_of_memory-class"></a>out_of_memory – třída

Výjimka, která je vyvolána, když je metoda neúspěšná z důvodu nedostatku paměti systému nebo zařízení.

## <a name="syntax"></a>Syntaxe

```cpp
class out_of_memory : public runtime_exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[out_of_memory – konstruktor](#ctor)|Inicializuje novou instanci třídy `out_of_memory`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`runtime_exception`

`out_of_memory`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amprt. h

**Obor názvů:** Concurrency
## <a name="ctor"></a>out_of_memory

Inicializuje novou instanci třídy.

### <a name="syntax"></a>Syntaxe

```cpp
explicit out_of_memory(
    const char * _Message ) throw();

out_of_memory () throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popis chyby

### <a name="return-value"></a>Návratová hodnota

Nová instance třídy `out_of_memory`.

## <a name="see-also"></a>Viz také

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
