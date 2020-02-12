---
title: unsupported_feature – třída
ms.date: 03/27/2019
f1_keywords:
- unsupported_feature
- AMPRT/unsupported_feature
- AMPRT/Concurrency::unsupported_feature
helpviewer_keywords:
- unsupported_feature class
ms.assetid: 6b1ab917-df13-48c7-9648-7cb2465a0ff5
ms.openlocfilehash: 561f0a258943f6d7e1c0f1b5cae716592c931fbc
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127709"
---
# <a name="unsupported_feature-class"></a>unsupported_feature – třída

Výjimka, která je vyvolána při použití nepodporované funkce.

## <a name="syntax"></a>Syntaxe

```cpp
class unsupported_feature : public runtime_exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[unsupported_feature – konstruktor](#unsupported_feature)|Sestaví novou instanci výjimky `unsupported_feature`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`runtime_exception`

`unsupported_feature`

## <a name="unsupported_feature"></a>unsupported_feature

  Sestaví novou instanci výjimky `unsupported_feature`.

### <a name="syntax"></a>Syntaxe

```cpp
explicit unsupported_feature(
    const char * _Message ) throw();

unsupported_feature() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popis chyby

### <a name="return-value"></a>Návratová hodnota

Objekt `unsupported_feature`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amprt. h

**Obor názvů:** Concurrency

## <a name="see-also"></a>Viz také

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
