---
title: operation_timed_out – třída
ms.date: 11/04/2016
f1_keywords:
- operation_timed_out
- CONCRT/concurrency::operation_timed_out
- CONCRT/concurrency::operation_timed_out::operation_timed_out
helpviewer_keywords:
- operation_timed_out class
ms.assetid: 963efe1d-a6e0-477c-9a70-d93d8412c897
ms.openlocfilehash: 8b25a35ac359fe052f9ae3c1cb15363acfbe93e5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50561171"
---
# <a name="operationtimedout-class"></a>operation_timed_out – třída

Tato třída popisuje výjimku vyvolanou při vypršel časový limit operace.

## <a name="syntax"></a>Syntaxe

```
class operation_timed_out : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[operation_timed_out](#ctor)|Přetíženo. Vytvoří `operation_timed_out` objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`operation_timed_out`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

**Namespace:** souběžnosti

##  <a name="ctor"></a> operation_timed_out –

Vytvoří `operation_timed_out` objektu.

```
explicit _CRTIMP operation_timed_out(_In_z_ const char* _Message) throw();

operation_timed_out() throw();
```

### <a name="parameters"></a>Parametry

*_TEXT*<br/>
Popisná zpráva chyby.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
