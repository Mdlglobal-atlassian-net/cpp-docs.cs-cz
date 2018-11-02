---
title: Platform::disconnectedexception – třída
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::DisconnectedException
- VCCORLIB/Platform::DisconnectedException::DisconnectedException
helpviewer_keywords:
- Platform::DisconnectedException
ms.assetid: c25e0d64-5bff-4c21-88e5-c4ec2776fa7f
ms.openlocfilehash: 2d4f8f4cb52fdb7e50c36eb3f0255bd85c15dbb1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50477139"
---
# <a name="platformdisconnectedexception-class"></a>Platform::disconnectedexception – třída

Vyvolána, když se pokusí odkazovat na server COM, který již existuje objekt proxy modelu COM

## <a name="syntax"></a>Syntaxe

```
public ref class DisconnectedException : COMException,    IException,    IPrintable,    IEquatable
```

### <a name="remarks"></a>Poznámky

Když třídy A odkazy na jiné třídy (třídy B), který je v samostatném procesu, třídy A vyžaduje objekt proxy pro komunikaci se serverem COM mimo proces, který obsahuje třídu B. Někdy přejít na serveru nedostatek paměti bez třídy znalosti o něm. V takovém případě je vyvolána výjimka RPC_E_DISCONNECTED a získá přeložit na Platform::disconnectedexception –. Jeden scénář, ve kterém je, vyvolá se při zdroje událostí vyvolá delegáta, který byl předán, ale delegáta zlikvidování v určitém okamžiku po odběru přihlásili k této události. Pokud k tomu dojde, zdroj události tohoto delegátu zruší jeho vyvolávacím seznamu.

Další informace najdete v tématu [COMException](../cppcx/platform-comexception-class.md) třídy.

### <a name="requirements"></a>Požadavky

**Minimální podporovaná klienta:** Windows 8

**Minimální podporovaná serverem:** systému Windows Server 2012

**Namespace:** platformy

**Metadata:** platform.winmd

## <a name="see-also"></a>Viz také

[Platform::COMException – třída](../cppcx/platform-comexception-class.md)