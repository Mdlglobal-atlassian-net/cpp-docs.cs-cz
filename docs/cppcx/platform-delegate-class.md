---
title: Platform::Delegate – třída
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Delegate
helpviewer_keywords:
- Platform::Delegate Class
ms.assetid: 82b21271-768f-4193-9ca2-be68ddfd546e
ms.openlocfilehash: 6a509827b3b8e14b6d28995b5b4ca468ee9a662e
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57741169"
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

Použít [delegovat](../windows/delegate-cpp-component-extensions.md) – klíčové slovo k vytváření delegátů; nepoužívejte Platform::Delegate – explicitně. Další informace najdete v tématu [delegáti](../cppcx/delegates-c-cx.md). Příklad toho, jak vytvářet a využívat delegáta, naleznete v tématu [vytváření komponent Windows Runtime v jazyce C++](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

### <a name="requirements"></a>Požadavky

**Minimální podporovaná klienta:** Windows 8

**Minimální podporovaná serveru:** Windows Server 2012

**Namespace:** Platforma

**Metadata:** platform.winmd

## <a name="see-also"></a>Viz také:

[Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)
