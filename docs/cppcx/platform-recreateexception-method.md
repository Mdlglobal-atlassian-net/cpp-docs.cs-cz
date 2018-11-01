---
title: Platform::RecreateException – metoda
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Exception
helpviewer_keywords:
- Platform::Exception Class
ms.assetid: fa73d1ab-86e4-4d26-a7d9-81938c1c7e77
ms.openlocfilehash: 8173377a3d7a75bc85088037c229bac19f341649
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50568867"
---
# <a name="platformrecreateexception-method"></a>Platform::ReCreateException – metoda

Tato metoda je jen pro interní použití a není určena pro uživatelský kód. Místo toho použijte metodu Exception::CreateException.

## <a name="syntax"></a>Syntaxe

```cpp
static Exception^ ReCreateException(int hr)
```

### <a name="parameters"></a>Parametry

*hr*

### <a name="property-valuereturn-value"></a>Hodnota vlastnosti / návratová hodnota

Vrátí nový Platform::Exception ^, podle zadaného HRESULT.
