---
title: Platform::wrongthreadexception – třída
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::WrongThreadException
- VCCORLIB/Platform::WrongThreadException::WrongThreadException
helpviewer_keywords:
- Platform::WrongThreadException
ms.assetid: c193f97e-0392-4535-a4c4-0711e4e4a836
ms.openlocfilehash: dde8c9afff6be083580042a958f59e057bc44350
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396077"
---
# <a name="platformwrongthreadexception-class"></a>Platform::wrongthreadexception – třída

Vyvolána, když vlákno volá prostřednictvím ukazatele rozhraní pro objekt proxy serveru, který nepatří do objektu apartment vlákna.

## <a name="syntax"></a>Syntaxe

```cpp
public ref class WrongThreadException : COMException,    IException,    IPrintable,    IEquatable
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu [COMException](../cppcx/platform-comexception-class.md).

### <a name="requirements"></a>Požadavky

**Minimální podporovaná klienta:** Windows 8

**Minimální podporovaná serveru:** Windows Server 2012

**Namespace:** Platforma

**Metadata:** platform.winmd

## <a name="see-also"></a>Viz také:

[Platform::COMException – třída](../cppcx/platform-comexception-class.md)
