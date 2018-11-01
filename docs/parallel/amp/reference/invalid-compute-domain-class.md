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
ms.openlocfilehash: 264b93d11b82eb00ac85e92413ca1a7071e06879
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50582244"
---
# <a name="invalidcomputedomain-class"></a>invalid_compute_domain – třída

Výjimka, která je vyvolána, když modul runtime nemůže spustit jádro za použití výpočetní domény určené na [parallel_for_each](concurrency-namespace-functions-amp.md#parallel_for_each) lokalitu volání.

## <a name="syntax"></a>Syntaxe

```
class invalid_compute_domain : public runtime_exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[invalid_compute_domain Constructor](#ctor)|Inicializuje novou instanci třídy `invalid_compute_domain` třídy.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`runtime_exception`

`invalid_compute_domain`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amprt.h

**Namespace:** souběžnosti

## <a name="ctor"></a> invalid_compute_domain –

Inicializuje novou instanci třídy.

## <a name="syntax"></a>Syntaxe

```
explicit invalid_compute_domain(
    const char * _Message ) throw();

invalid_compute_domain() throw();
```

### <a name="parameters"></a>Parametry

*_TEXT*<br/>
Popis chyby.

### <a name="return-value"></a>Návratová hodnota

Instance `invalid_compute_domain` třídy

## <a name="see-also"></a>Viz také

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
