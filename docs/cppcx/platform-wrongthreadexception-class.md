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
ms.openlocfilehash: b59191eb739a94f305b656425ee2f3725815c7b8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50639995"
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

**Minimální podporovaná serverem:** systému Windows Server 2012

**Namespace:** platformy

**Metadata:** platform.winmd

## <a name="see-also"></a>Viz také

[Platform::COMException – třída](../cppcx/platform-comexception-class.md)