---
title: invalid_oversubscribe_operation – třída
ms.date: 11/04/2016
f1_keywords:
- invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation
- CONCRT/concurrency::invalid_oversubscribe_operation::invalid_oversubscribe_operation
helpviewer_keywords:
- invalid_oversubscribe_operation class
ms.assetid: 0a9c5f08-d5e6-4ad0-90a9-517472b3ac28
ms.openlocfilehash: 7a879fc2da2f963cd4b5ea5fcd7e9506f86ce051
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77140837"
---
# <a name="invalid_oversubscribe_operation-class"></a>invalid_oversubscribe_operation – třída

Tato třída popisuje výjimku vyvolanou při volání metody `Context::Oversubscribe` s parametrem `_BeginOversubscription` nastaveným na **hodnotu false** bez předchozího volání metody `Context::Oversubscribe` s parametrem `_BeginOversubscription` nastaveným na **hodnotu true**.

## <a name="syntax"></a>Syntaxe

```cpp
class invalid_oversubscribe_operation : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[invalid_oversubscribe_operation](#ctor)|Přetíženo. Vytvoří objekt `invalid_oversubscribe_operation`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`invalid_oversubscribe_operation`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h

**Obor názvů:** souběžnost

## <a name="ctor"></a>invalid_oversubscribe_operation

Vytvoří objekt `invalid_oversubscribe_operation`.

```cpp
explicit _CRTIMP invalid_oversubscribe_operation(_In_z_ const char* _Message) throw();

invalid_oversubscribe_operation() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popisná zpráva o chybě

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
