---
title: uninitialized_object – třída
ms.date: 03/27/2019
f1_keywords:
- uninitialized_object
- AMPRT/uninitialized_object
- AMPRT/Concurrency::uninitialized_object
helpviewer_keywords:
- uninitialized_object class
ms.assetid: 6ae3c4e8-64a6-4511-a158-03be197b63af
ms.openlocfilehash: ef7ded0bf925d3430b70064c4979b75e08f9cf45
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127696"
---
# <a name="uninitialized_object-class"></a>uninitialized_object – třída

Výjimka, která je vyvolána při použití neinicializovaného objektu.

## <a name="syntax"></a>Syntaxe

```cpp
class uninitialized_object : public runtime_exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[uninitialized_object – konstruktor](#uninitialized_object)|Inicializuje novou instanci třídy `uninitialized_object`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`runtime_exception`

`uninitialized_object`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amprt. h

**Obor názvů:** Concurrency

## <a name="uninitialized_object"></a>uninitialized_object

Sestaví novou instanci výjimky `uninitialized_object`.

### <a name="syntax"></a>Syntaxe

```cpp
explicit uninitialized_object(
    const char * _Message ) throw();

uninitialized_object() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popis chyby

### <a name="return-value"></a>Návratová hodnota

Objekt výjimky `uninitialized_object`.

## <a name="see-also"></a>Viz také

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
