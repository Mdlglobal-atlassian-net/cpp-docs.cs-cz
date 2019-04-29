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
ms.openlocfilehash: 09f534a90f3191025c3ce99d07a462908387c676
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405648"
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
|[accelerator_view_removed Constructor](#ctor)|Inicializuje novou instanci třídy `accelerator_view_removed` třídy.|

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

**Namespace:** Souběžnost

## <a name="ctor"></a> accelerator_view_removed –

Inicializuje novou instanci třídy [accelerator_view_removed –](accelerator-view-removed-class.md) třídy.

### <a name="syntax"></a>Syntaxe

```
explicit accelerator_view_removed(
    const char * message,
    HRESULT view_removed_reason ) throw();

explicit accelerator_view_removed(
    HRESULT view_removed_reason ) throw();
```

### <a name="parameters"></a>Parametry

*message*<br/>
Popis chyby.

*view_removed_reason*<br/>
Kód chyby HRESULT označující důvod odebrání `accelerator_view` objektu.

### <a name="return-value"></a>Návratová hodnota

Novou instanci třídy `accelerator_view_removed` třídy.

## <a name="getviewremovedreason"></a>get_view_removed_reason

Vrátí kód chyby HRESULT označující příčinu `accelerator_view` odebírání příslušného objektu.

### <a name="syntax"></a>Syntaxe

```
HRESULT get_view_removed_reason() const throw();
```

## <a name="see-also"></a>Viz také:

[Obor názvů Concurrency (C++ AMP)](concurrency-namespace-cpp-amp.md)
