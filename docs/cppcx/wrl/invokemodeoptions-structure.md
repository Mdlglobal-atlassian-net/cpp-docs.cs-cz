---
title: Invokemodeoptions – struktura
ms.date: 03/22/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::InvokeModeOptions
helpviewer_keywords:
- InvokeModeOptions structure
- InvokeMode enum
ms.openlocfilehash: 0e5b45042c9959b87ad5db97ab755e49de469149
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/05/2019
ms.locfileid: "59035277"
---
# <a name="invokemodeoptions-structure"></a>Invokemodeoptions – struktura

Určuje, jestli chcete-li vyvolat všech událostí ve frontě delegáta nebo zastavit ohlásí, jakmile dojde k chybě. Přípustné hodnoty jsou uvedeny v `InvokeMode` výčtu.

## <a name="syntax"></a>Syntaxe

```cpp
enum InvokeMode
{
   StopOnFirstError = 1,
   FireAll = 2,
};

struct InvokeModeOptions
{
   static const InvokeMode invokeMode = invokeModeValue;
};
```

## <a name="requirements"></a>Požadavky

**Záhlaví:** event.h

**Namespace:** Microsoft::WRL

## <a name="see-also"></a>Viz také:

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)<br/>
[Třída Microsoft::WRL::AgileEventSource](agileeventsource-class.md)