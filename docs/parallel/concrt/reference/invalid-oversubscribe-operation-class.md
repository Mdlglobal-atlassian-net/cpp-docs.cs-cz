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
ms.openlocfilehash: 9e25095f70266e772d69f9b644f7def968157912
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50572143"
---
# <a name="invalidoversubscribeoperation-class"></a>invalid_oversubscribe_operation – třída

Tato třída popisuje výjimku vyvolána, když `Context::Oversubscribe` metoda je volána `_BeginOversubscription` parametr nastaven na **false** bez předchozího volání `Context::Oversubscribe` metodu s `_BeginOversubscription` parametr nastaven na **true**.

## <a name="syntax"></a>Syntaxe

```
class invalid_oversubscribe_operation : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[invalid_oversubscribe_operation](#ctor)|Přetíženo. Vytvoří `invalid_oversubscribe_operation` objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`invalid_oversubscribe_operation`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

**Namespace:** souběžnosti

##  <a name="ctor"></a> invalid_oversubscribe_operation –

Vytvoří `invalid_oversubscribe_operation` objektu.

```
explicit _CRTIMP invalid_oversubscribe_operation(_In_z_ const char* _Message) throw();

invalid_oversubscribe_operation() throw();
```

### <a name="parameters"></a>Parametry

*_TEXT*<br/>
Popisná zpráva chyby.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
