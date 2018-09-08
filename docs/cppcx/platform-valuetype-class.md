---
title: Platform::ValueType – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/03/2017
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::ValueType::ToString
dev_langs:
- C++
helpviewer_keywords:
- Platform::ValueType Class
ms.assetid: 79aa8754-b140-4974-a5b1-be046938a10a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ae1cab3d5cde3bc39f131acd1b01976dcb6d522b
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44105104"
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

**Minimální podporovaná serverem:** systému Windows Server 2012

**Namespace:** platformy

**Metadata:** platform.winmd

## <a name="tostring"></a> ValueType::ToString – metoda

Vrátí řetězcovou reprezentaci objektu.

### <a name="syntax"></a>Syntaxe

```cpp
Platform::String ToString();
```

### <a name="return-value"></a>Návratová hodnota

Platform::String, který představuje hodnotu.

## <a name="see-also"></a>Viz také

[Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)