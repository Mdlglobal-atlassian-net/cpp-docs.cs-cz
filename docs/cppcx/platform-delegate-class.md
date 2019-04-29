---
title: Platform::Delegate – třída
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Delegate
helpviewer_keywords:
- Platform::Delegate Class
ms.assetid: 82b21271-768f-4193-9ca2-be68ddfd546e
ms.openlocfilehash: 4116de3240c3ef334db51095997f946731372708
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396090"
---
# <a name="platformdelegate-class"></a>Platform::Delegate – třída

Představuje objekt funkce.

## <a name="syntax"></a>Syntaxe

```cpp
public delegate void delegate_name();
```

### <a name="members"></a>Členové

Třída delegáta má metody Equals() GetHashCode(), a metody ToString() odvozený od [Platform::Object – třída](../cppcx/platform-object-class.md).

### <a name="remarks"></a>Poznámky

Použít [delegovat](../extensions/delegate-cpp-component-extensions.md) – klíčové slovo k vytváření delegátů; nepoužívejte Platform::Delegate – explicitně. Další informace najdete v tématu [delegáti](../cppcx/delegates-c-cx.md). Příklad toho, jak vytvářet a využívat delegáta, naleznete v tématu [vytváření komponent Windows Runtime v jazyce C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

### <a name="requirements"></a>Požadavky

**Minimální podporovaná klienta:** Windows 8

**Minimální podporovaná serveru:** Windows Server 2012

**Namespace:** Platforma

**Metadata:** platform.winmd

## <a name="see-also"></a>Viz také:

[Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)
