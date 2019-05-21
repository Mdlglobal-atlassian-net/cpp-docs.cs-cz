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
ms.openlocfilehash: a977957fcb28a7f4c6c849c954026e2bda4e728c
ms.sourcegitcommit: a61d17cffdd50f1c3c6e082a01bbcbc85b6cc5a7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2019
ms.locfileid: "65975161"
---
# <a name="uninitializedobject-class"></a>uninitialized_object – třída

Výjimka, která je vyvolána při použití neinicializovaného objektu.

## <a name="syntax"></a>Syntaxe

```
class uninitialized_object : public runtime_exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[uninitialized_object Constructor](#uninitialized_object)|Inicializuje novou instanci třídy `uninitialized_object` třídy.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`runtime_exception`

`uninitialized_object`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amprt.h

**Namespace:** Souběžnost

## <a name="uninitialized_object"></a> uninitialized_object –

Vytvoří novou instanci třídy `uninitialized_object` výjimky.

### <a name="syntax"></a>Syntaxe

```
explicit uninitialized_object(
    const char * _Message ) throw();

uninitialized_object() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popis chyby.

### <a name="return-value"></a>Návratová hodnota

`uninitialized_object` Objekt výjimky.

## <a name="see-also"></a>Viz také:

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
