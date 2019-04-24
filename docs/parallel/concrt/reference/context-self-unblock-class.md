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
ms.openlocfilehash: 900dc68eac4441bd1db3818d3c1f30698b80a6e0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62296173"
---
# <a name="contextselfunblock-class"></a>context_self_unblock – třída

Tato třída popisuje výjimku vyvolána, když `Unblock` metodu `Context` objektu je volána z stejný kontext. Pokus o by jít odblokujete samotné podle daného kontextu.

## <a name="syntax"></a>Syntaxe

```
class context_self_unblock : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[context_self_unblock](#ctor)|Přetíženo. Vytvoří `context_self_unblock` objektu.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`context_self_unblock`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

**Namespace:** souběžnosti

##  <a name="ctor"></a> context_self_unblock

Vytvoří `context_self_unblock` objektu.

```
explicit _CRTIMP context_self_unblock(_In_z_ const char* _Message) throw();

context_self_unblock() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popisná zpráva chyby.

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)
