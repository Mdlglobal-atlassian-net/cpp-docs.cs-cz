---
title: improper_lock – třída
ms.date: 11/04/2016
f1_keywords:
- improper_lock
- CONCRT/concurrency::improper_lock
- CONCRT/concurrency::improper_lock::improper_lock
helpviewer_keywords:
- improper_lock class
ms.assetid: 8f494942-7748-4a2a-8de2-23414bfe6346
ms.openlocfilehash: de7393c9186a1572040acd18854b5b3046b239f2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50552786"
---
# <a name="improperlock-class"></a>improper_lock – třída

Tato třída popisuje výjimku vyvolanou při nesprávně získán zámek.

## <a name="syntax"></a>Syntaxe

```
class improper_lock : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[improper_lock](#ctor)|Přetíženo. Vytvoří `improper_lock exception`.|

## <a name="remarks"></a>Poznámky

Obvykle tato výjimka je vyvolána při pokusu o získání zámku mimo reentrant rekurzivně na stejném kontextu.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`improper_lock`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

**Namespace:** souběžnosti

##  <a name="ctor"></a> improper_lock –

Vytvoří `improper_lock exception`.

```
explicit _CRTIMP improper_lock(_In_z_ const char* _Message) throw();

improper_lock() throw();
```

### <a name="parameters"></a>Parametry

*_TEXT*<br/>
Popisná zpráva chyby.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[critical_section – třída](critical-section-class.md)<br/>
[reader_writer_lock – třída](reader-writer-lock-class.md)
