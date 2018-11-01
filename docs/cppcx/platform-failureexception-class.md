---
title: Platform::failureexception – třída
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::FailureException::FailureException
- VCCORLIB/Platform::FailureException
helpviewer_keywords:
- Platform::FailureException
ms.assetid: 1729cd07-bfc2-448e-9db5-185d5cbf5b81
ms.openlocfilehash: b1890fb0649dee779b3851ed9f1fc46a67b2916d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472615"
---
# <a name="platformfailureexception-class"></a>Platform::failureexception – třída

Vyvolána, když operace se nezdařila. Jedná se o ekvivalent E_FAIL HRESULT.

## <a name="syntax"></a>Syntaxe

```cpp
public ref class FailureException : COMException,    IException,    IPrintable,    IEquatable
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [COMException](../cppcx/platform-comexception-class.md) třídy.

### <a name="requirements"></a>Požadavky

**Minimální podporovaná klienta:** Windows 8

**Minimální podporovaná serverem:** systému Windows Server 2012

**Namespace:** platformy

**Metadata:** platform.winmd

## <a name="see-also"></a>Viz také

[Platform::COMException – třída](../cppcx/platform-comexception-class.md)