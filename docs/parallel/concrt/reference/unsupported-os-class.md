---
title: unsupported_os – třída
ms.date: 11/04/2016
f1_keywords:
- unsupported_os
- CONCRT/concurrency::unsupported_os
- CONCRT/concurrency::unsupported_os::unsupported_os
helpviewer_keywords:
- unsupported_os class
ms.assetid: 6fa57636-341b-4b51-84cc-261d283ff736
ms.openlocfilehash: 253cd76182e1b6f85be3701663bd10c86c10e6ba
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142345"
---
# <a name="unsupported_os-class"></a>unsupported_os – třída

Tato třída popisuje výjimku vyvolanou při použití nepodporovaného operačního systému.

## <a name="syntax"></a>Syntaxe

```cpp
class unsupported_os : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[unsupported_os](#ctor)|Přetíženo. Vytvoří objekt `unsupported_os`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`unsupported_os`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h

**Obor názvů:** souběžnost

## <a name="ctor"></a>unsupported_os

Vytvoří objekt `unsupported_os`.

### <a name="syntax"></a>Syntaxe

```cpp
explicit _CRTIMP unsupported_os(_In_z_ const char* _Message) throw();

unsupported_os() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popisná zpráva o chybě

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
