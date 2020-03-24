---
title: Struktura InvokeModeOptions
ms.date: 03/22/2018
ms.topic: reference
f1_keywords:
- event/Microsoft::WRL::InvokeModeOptions
helpviewer_keywords:
- InvokeModeOptions structure
- InvokeMode enum
ms.openlocfilehash: 9bca49479d97ee371f6728f90a9aa96da0387f54
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213834"
---
# <a name="invokemodeoptions-structure"></a>Struktura InvokeModeOptions

Určuje, zda se mají aktivovat všechny události ve frontě delegátů nebo zastavit aktivaci po vyvolání chyby. Přípustné hodnoty jsou zadány ve výčtu `InvokeMode`.

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

**Záhlaví:** Event. h

**Obor názvů:** Microsoft:: WRL

## <a name="see-also"></a>Viz také

[Microsoft::WRL – obor názvů](microsoft-wrl-namespace.md)<br/>
[Microsoft:: WRL:: AgileEventSource – třída](agileeventsource-class.md)
