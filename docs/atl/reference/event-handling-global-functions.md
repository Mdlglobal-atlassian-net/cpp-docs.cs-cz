---
title: Globální funkce zpracování událostí
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlWaitWithMessageLoop
helpviewer_keywords:
- event handling, global functions
- global functions, event handling
ms.assetid: fd674470-3def-47c3-be1c-894fa85f13e8
ms.openlocfilehash: f2f8269dcf0f59a5d0794d3f16d4c4f85d8841ac
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81330139"
---
# <a name="event-handling-global-functions"></a>Globální funkce zpracování událostí

Tato funkce poskytuje obslužnou rutinu události.

> [!IMPORTANT]
> Funkci uvedenou v následující tabulce nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

|||
|-|-|
|[AtlWaitWithMessageLoop](#atlwaitwithmessageloop)|Čeká na objekt, který má být signalizován, mezitím dispečink okno zprávy podle potřeby.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

## <a name="atlwaitwithmessageloop"></a><a name="atlwaitwithmessageloop"></a>AtlWaitWithMessageLoop

Počká na objekt, který má být signalizován, a mezitím podle potřeby odbaví zprávy okna.

> [!IMPORTANT]
> Tuto funkci nelze použít v aplikacích, které se spouštějí v prostředí Windows Runtime.

```
BOOL AtlWaitWithMessageLoop(HANDLE hEvent);
```

### <a name="parameters"></a>Parametry

*hUdálost*<br/>
[v] Popisovač objektu čekat.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud byl objekt signalizován.

### <a name="remarks"></a>Poznámky

To je užitečné, pokud chcete počkat na událost objektu a být upozorněni, že k ní dochází, ale povolit zprávy okna, které mají být odeslány během čekání.

## <a name="see-also"></a>Viz také

[Functions](../../atl/reference/atl-functions.md)
