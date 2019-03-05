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
ms.openlocfilehash: c10a7f302b63c33869425c4e5bddb36a15373ea8
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2019
ms.locfileid: "57326558"
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

*_Message*<br/>
Popisná zpráva chyby.

## <a name="see-also"></a>Viz také:

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[critical_section – třída](critical-section-class.md)<br/>
[reader_writer_lock – třída](reader-writer-lock-class.md)
