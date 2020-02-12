---
title: invalid_link_target – třída
ms.date: 11/04/2016
f1_keywords:
- invalid_link_target
- CONCRT/concurrency::invalid_link_target
- CONCRT/concurrency::invalid_link_target::invalid_link_target
helpviewer_keywords:
- invalid_link_target class
ms.assetid: 33b64885-34d8-4d4e-a893-02e9f19c958e
ms.openlocfilehash: bd3d82c06c174c69c60dec33592110f4de72ac99
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77141040"
---
# <a name="invalid_link_target-class"></a>invalid_link_target – třída

Tato třída popisuje výjimku vyvolanou při volání metody `link_target` bloku zasílání zpráv a blok zasílání zpráv se nemůže připojit k cíli. Může to být výsledek překročení počtu odkazů, které je povolený, nebo pokus o připojení konkrétního cíle dvakrát ke stejnému zdroji.

## <a name="syntax"></a>Syntaxe

```cpp
class invalid_link_target : public std::exception;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[invalid_link_target](#ctor)|Přetíženo. Vytvoří objekt `invalid_link_target`.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`exception`

`invalid_link_target`

## <a name="requirements"></a>Požadavky

**Záhlaví:** ConcRT. h

**Obor názvů:** souběžnost

## <a name="ctor"></a>invalid_link_target

Vytvoří objekt `invalid_link_target`.

```cpp
explicit _CRTIMP invalid_link_target(_In_z_ const char* _Message) throw();

invalid_link_target() throw();
```

### <a name="parameters"></a>Parametry

*_Message*<br/>
Popisná zpráva o chybě

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)<br/>
[Asynchronní bloky zpráv](../../../parallel/concrt/asynchronous-message-blocks.md)
