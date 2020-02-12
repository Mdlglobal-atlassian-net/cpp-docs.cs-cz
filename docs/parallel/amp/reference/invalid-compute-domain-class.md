---
title: invalid_compute_domain – třída
ms.date: 11/04/2016
f1_keywords:
- invalid_compute_domain
- AMPRT/invalid_compute_domain
- AMPRT/Concurrency::invalid_compute_domain::invalid_compute_domain
helpviewer_keywords:
- invalid_compute_domain class
ms.assetid: ac7a7166-8bdb-4db1-8caf-ea129ab5117e
ms.openlocfilehash: 3b8179e8e92665fa6482bd092504af71aa0106f0
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77126458"
---
# <a name="invalid_compute_domain-class"></a>invalid_compute_domain – třída

Výjimka, která je vyvolána, když modul runtime nemůže spustit jádro pomocí výpočetní domény zadané na webu [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each) volání.

## <a name="syntax"></a>Syntaxe

```cpp
class invalid_compute_domain : public runtime_exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[invalid_compute_domain – konstruktor](#ctor)|Inicializuje novou instanci třídy `invalid_compute_domain`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`runtime_exception`

`invalid_compute_domain`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amprt. h

**Obor názvů:** Concurrency

## <a name="ctor"></a>invalid_compute_domain

Inicializuje novou instanci třídy.

## <a name="syntax"></a>Syntaxe

```cpp
explicit invalid_compute_domain(
    const char * _Message ) throw();

invalid_compute_domain() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popis chyby

### <a name="return-value"></a>Návratová hodnota

Instance třídy `invalid_compute_domain`

## <a name="see-also"></a>Viz také

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
