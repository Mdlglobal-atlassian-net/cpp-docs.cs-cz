---
title: Platform::changedstateexception – třída
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ChangedStateException
- VCCORLIB/Platform::ChangedStateException::ChangedStateException
helpviewer_keywords:
- Platform::ChangedStateException
ms.assetid: f894beac-9e80-4fac-ac25-89f1dbc0a6a4
ms.openlocfilehash: 79181702c95f8c666b06bdb26319ccb06e55db0a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161709"
---
# <a name="platformchangedstateexception-class"></a>Platform::changedstateexception – třída

Vyvolána, když vnitřní stav objektu došlo ke změně, a proto už není platná výsledky metody.

## <a name="syntax"></a>Syntaxe

```cpp
public ref class ChangedStateException : COMException,    IException,    IPrintable,    IEquatable
```

### <a name="remarks"></a>Poznámky

Jedním z příkladů kde vyvolání této výjimky je při volání metody iterátoru shromažďování nebo zobrazení kolekce po změně kolekce nadřazených, proto už není platná výsledky metody.

Další informace najdete v tématu [COMException](../cppcx/platform-comexception-class.md) třídy.

### <a name="requirements"></a>Požadavky

**Minimální podporovaná klienta:** Windows 8

**Minimální podporovaná serveru:** Windows Server 2012

**Namespace:** Platforma

**Metadata:** platform.winmd

## <a name="see-also"></a>Viz také:

[Platform::COMException – třída](../cppcx/platform-comexception-class.md)
