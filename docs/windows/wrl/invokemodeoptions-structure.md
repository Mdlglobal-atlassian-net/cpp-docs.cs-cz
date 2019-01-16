---
title: Invokemodeoptions – struktura
ms.date: 03/22/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::InvokeModeOptions
helpviewer_keywords:
- InvokeModeOptions structure
- InvokeMode enum
ms.openlocfilehash: ff16c6c5a2ce09313283198fe0b86e95d572e46c
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334743"
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

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)<br/>
[Třída Microsoft::WRL::AgileEventSource](agileeventsource-class.md)