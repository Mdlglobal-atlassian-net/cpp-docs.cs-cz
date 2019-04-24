---
title: Platform::RecreateException – metoda
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Exception
helpviewer_keywords:
- Platform::Exception Class
ms.assetid: fa73d1ab-86e4-4d26-a7d9-81938c1c7e77
ms.openlocfilehash: 9e167efc54352d125e849956a2da8d8e8cad4ed6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62330320"
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
