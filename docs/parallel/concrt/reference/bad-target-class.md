---
title: bad_target – třída
ms.date: 11/04/2016
f1_keywords:
- bad_target
- CONCRT/concurrency::bad_target
- CONCRT/concurrency::bad_target::bad_target
helpviewer_keywords:
- bad_target class
ms.assetid: e6dcddbf-9217-4fac-ac7f-7b8b4781d2f5
ms.openlocfilehash: 0440955718bee3b426f5e4625b5eb3fc559a5d28
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434480"
---
# <a name="badtarget-class"></a>bad_target – třída

Tato třída popisuje výjimku vyvolanou při blok zpráv je dán ukazatel cíl, který není platný pro právě prováděnou operaci.

## <a name="syntax"></a>Syntaxe

```
class bad_target : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[bad_target](#ctor)|Přetíženo. Vytvoří `bad_target` objektu.|

## <a name="remarks"></a>Poznámky

Toto se obvykle výjimka z důvodů, jako je například cíl pokusu o zpracování zprávy, která je vyhrazena pro jiný cíl nebo uvolnění rezervace, který nemá.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`bad_target`

## <a name="requirements"></a>Požadavky

**Záhlaví:** concrt.h

**Namespace:** souběžnosti

##  <a name="ctor"></a> bad_target –

Vytvoří `bad_target` objektu.

```
explicit _CRTIMP bad_target(_In_z_ const char* _Message) throw();

bad_target() throw();
```

### <a name="parameters"></a>Parametry

*_TEXT*<br/>
Popisná zpráva chyby.

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[Asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md)

