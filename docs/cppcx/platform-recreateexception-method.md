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
ms.sourcegitcommit: b032daf81cb5fdb1f5a988277ee30201441c4945
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/15/2018
ms.locfileid: "51693266"
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
