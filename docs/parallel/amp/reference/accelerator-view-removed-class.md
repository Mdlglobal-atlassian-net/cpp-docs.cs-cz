---
title: accelerator_view_removed – třída
ms.date: 03/27/2019
f1_keywords:
- accelerator_view_removed
- AMPRT/accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed::accelerator_view_removed
- AMPRT/Concurrency::accelerator_view_removed::get_view_removed_reason
helpviewer_keywords:
- AMPRT/Concurrency::accelerator_view_removed::accelerator_view_removed Class
ms.assetid: 262446de-311c-454e-a5ed-e2aaced0d88a
ms.openlocfilehash: 9a3f6f349fc3103893639fe209dcf23a07ffec56
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77127121"
---
# <a name="accelerator_view_removed-class"></a>accelerator_view_removed – třída

Výjimka, která je vyvolána, když se podkladové volání rozhraní DirectX nepovede z důvodu detekce a obnovení časového limitu systému Windows.

## <a name="syntax"></a>Syntaxe

```cpp
class accelerator_view_removed : public runtime_exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[accelerator_view_removed – konstruktor](#ctor)|Inicializuje novou instanci třídy `accelerator_view_removed`.|

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[get_view_removed_reason](#get_view_removed_reason)|Vrátí kód chyby HRESULT označující příčinu odebrání objektu `accelerator_view`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`runtime_exception`

`out_of_memory`

## <a name="requirements"></a>Požadavky

**Záhlaví:** amprt. h

**Obor názvů:** Concurrency

## <a name="ctor"></a>accelerator_view_removed

Inicializuje novou instanci třídy [accelerator_view_removed](accelerator-view-removed-class.md) .

### <a name="syntax"></a>Syntaxe

```cpp
explicit accelerator_view_removed(
    const char * message,
    HRESULT view_removed_reason ) throw();

explicit accelerator_view_removed(
    HRESULT view_removed_reason ) throw();
```

### <a name="parameters"></a>Parametry

*message*<br/>
Popis chyby

*view_removed_reason*<br/>
Kód chyby HRESULT označující příčinu odebrání objektu `accelerator_view`.

### <a name="return-value"></a>Návratová hodnota

Nová instance třídy `accelerator_view_removed`.

## <a name="get_view_removed_reason"></a>get_view_removed_reason

Vrátí kód chyby HRESULT označující příčinu odebrání objektu `accelerator_view`.

### <a name="syntax"></a>Syntaxe

```cpp
HRESULT get_view_removed_reason() const throw();
```

## <a name="see-also"></a>Viz také

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
