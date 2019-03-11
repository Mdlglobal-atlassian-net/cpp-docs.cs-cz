---
title: Platform::ValueType – třída
ms.date: 02/03/2017
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ValueType::ToString
helpviewer_keywords:
- Platform::ValueType Class
ms.assetid: 79aa8754-b140-4974-a5b1-be046938a10a
ms.openlocfilehash: 889cf3a53468491517d37978ca09472756ad9b7e
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57747148"
---
# <a name="platformvaluetype-class"></a>Platform::ValueType – třída

Základní třída pro instance typů hodnot.

## <a name="syntax"></a>Syntaxe

```cpp
public ref class ValueType : Object
```

## <a name="public-methods"></a>Veřejné metody

|||
|-|-|
|[ValueType::ToString](#tostring)|Vrátí řetězcovou reprezentaci objektu. Zděděno z [Platform::Object](../cppcx/platform-object-class.md).|

### <a name="remarks"></a>Poznámky

ValueType třída se používá k vytvoření typů hodnot. Typ hodnoty je odvozen od objektu, jehož členové se základním členstvím. Kompilátor však odpojí tyto členy základní úrovně z typů hodnot, které jsou odvozeny z třídy ValueType. Kompilátor znovu tyto členy základní úrovně, když je typ hodnoty v poli.

### <a name="requirements"></a>Požadavky

**Minimální podporovaná klienta:** Windows 8

**Minimální podporovaná serveru:** Windows Server 2012

**Namespace:** Platforma

**Metadata:** platform.winmd

## <a name="tostring"></a> ValueType::ToString – metoda

Vrátí řetězcovou reprezentaci objektu.

### <a name="syntax"></a>Syntaxe

```cpp
Platform::String ToString();
```

### <a name="return-value"></a>Návratová hodnota

Platform::String, který představuje hodnotu.

## <a name="see-also"></a>Viz také:

[Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)
