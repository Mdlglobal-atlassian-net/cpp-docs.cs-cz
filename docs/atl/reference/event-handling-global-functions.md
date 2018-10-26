---
title: Globální funkce zpracování událostí | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlWaitWithMessageLoop
dev_langs:
- C++
helpviewer_keywords:
- event handling, global functions
- global functions, event handling
ms.assetid: fd674470-3def-47c3-be1c-894fa85f13e8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5ef89aec3a0eaf53c6c97b3480008b7e9fd586e3
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50054888"
---
# <a name="event-handling-global-functions"></a>Globální funkce zpracování událostí

Tato funkce poskytuje obslužné rutiny události.

> [!IMPORTANT]
>  Funkce uvedené v následující tabulce nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

|||
|-|-|
|[AtlWaitWithMessageLoop](#atlwaitwithmessageloop)|Počká na objekt, který má být signalizován, mezitím podle potřeby odbaví zprávy okna.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** atlbase.h

##  <a name="atlwaitwithmessageloop"></a>  AtlWaitWithMessageLoop

Počká na objekt, který má být signalizován, a mezitím podle potřeby odbaví zprávy okna.

> [!IMPORTANT]
>  Tuto funkci nelze použít v aplikacích, které jsou spouštěny v modulu Windows Runtime.

```
BOOL AtlWaitWithMessageLoop(HANDLE hEvent);
```

### <a name="parameters"></a>Parametry

*hEvent*<br/>
[in] Popisovač objektu čekání.

### <a name="return-value"></a>Návratová hodnota

Vrátí hodnotu PRAVDA, pokud byl signalizován objektu.

### <a name="remarks"></a>Poznámky

To je užitečné, pokud chcete čekat na událost objektu dojít, a oznámí to děje, ale povolit okna zpráv odeslaných během čekání.

## <a name="see-also"></a>Viz také

[Funkce](../../atl/reference/atl-functions.md)
