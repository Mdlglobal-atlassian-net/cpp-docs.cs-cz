---
title: context_self_unblock – třída
ms.date: 11/04/2016
f1_keywords:
- context_self_unblock
- CONCRT/concurrency::context_self_unblock
- CONCRT/concurrency::context_self_unblock::context_self_unblock
helpviewer_keywords:
- context_self_unblock class
ms.assetid: 9601cd28-4f40-4c2e-89ab-747068956331
ms.openlocfilehash: 883d5630251a6ea13afba1164f221a0da1773c17
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77143115"
---
# <a name="context_self_unblock-class"></a>context_self_unblock – třída

Tato třída popisuje výjimku vyvolanou při volání metody `Unblock` objektu `Context` ze stejného kontextu. To by znamenalo, že pokus o odblokování samotného daného kontextu.

## <a name="syntax"></a>Syntaxe

```cpp
class context_self_unblock : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[context_self_unblock](#ctor)|Přetíženo. Vytvoří objekt `context_self_unblock`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`context_self_unblock`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h

**Obor názvů:** souběžnost

## <a name="ctor"></a>context_self_unblock

Vytvoří objekt `context_self_unblock`.

```cpp
explicit _CRTIMP context_self_unblock(_In_z_ const char* _Message) throw();

context_self_unblock() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popisná zpráva o chybě

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
