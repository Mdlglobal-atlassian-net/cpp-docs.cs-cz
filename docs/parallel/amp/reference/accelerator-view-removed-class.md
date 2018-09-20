---
title: accelerator_view_removed – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-amp
ms.topic: reference
f1_keywords:
- accelerator_view_removed
- AMPRT/accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed:accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed:get_view_removed_reason
dev_langs:
- C++
helpviewer_keywords:
- AMPRT/Concurrency::accelerator_view_removed:accelerator_view_removed Class
ms.assetid: 262446de-311c-454e-a5ed-e2aaced0d88a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e937c2f5afedf1c78a46e864ea0b081ddf18e99d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46373298"
---
# <a name="acceleratorviewremoved-class"></a>accelerator_view_removed – třída

Výjimka, která je vyvolána, když podkladové volání rozhraní DirectX selže z důvodu vypršení časového limitu Windows mechanismus detekce a obnovení.

## <a name="syntax"></a>Syntaxe

```
class accelerator_view_removed : public runtime_exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[accelerator_view_removed – konstruktor](#ctor)|Inicializuje novou instanci třídy `accelerator_view_removed` třídy.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[get_view_removed_reason](#get_view_removed_reason)|Vrátí kód chyby HRESULT označující příčinu `accelerator_view` odebírání příslušného objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`runtime_exception`

`out_of_memory`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amprt.h

**Namespace:** souběžnosti

## <a name="ctor"></a> accelerator_view_removed –

Inicializuje novou instanci třídy [accelerator_view_removed –](accelerator-view-removed-class.md) třídy.

### <a name="syntax"></a>Syntaxe

```
explicit accelerator_view_removed(
    const char * _Message,
    HRESULT _View_removed_reason ) throw();

explicit accelerator_view_removed(
    HRESULT _View_removed_reason ) throw();
```

### <a name="parameters"></a>Parametry

*_TEXT*<br/>
Popis chyby.

*_View_removed_reason*<br/>
Kód chyby HRESULT označující důvod odebrání `accelerator_view` objektu.

### <a name="return-value"></a>Návratová hodnota

Vytvoření nové instance třídy accelerator_view_removed –.

## <a name="get_view_removed_reason_method"></a> get_view_removed_reason

Vrátí kód chyby HRESULT označující příčinu `accelerator_view` odebírání příslušného objektu.

### <a name="syntax"></a>Syntaxe

```
HRESULT get_view_removed_reason() const throw();
```

## <a name="see-also"></a>Viz také

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
