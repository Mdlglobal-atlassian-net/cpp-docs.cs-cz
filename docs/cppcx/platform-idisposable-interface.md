---
title: Platform::IDisposable – rozhraní
ms.date: 02/03/2017
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::IDisposable
helpviewer_keywords:
- Platform::IDisposable Interface
ms.assetid: f4344056-7030-42ed-bc98-b140edffddcd
ms.openlocfilehash: f114959321c0ed3879a089b944a5ff1b19843118
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637434"
---
# <a name="platformidisposable-interface"></a>Platform::IDisposable – rozhraní

Používá se k uvolnění nespravovaných prostředků.

## <a name="syntax"></a>Syntaxe

```cpp
public interface class IDisposable
```

## <a name="attributes"></a>Atributy

**GuidAttribute**("de0cbaea-8065-4a45-b196-c9d443f9bab3")

**VersionAttribute**(NTDDI_WIN8)

### <a name="members"></a>Členové

Rozhraní IDisposable dědí z rozhraní IUnknown. Rozhraní IDisposable obsahuje také následující typy členů:

**Metody**

Rozhraní IDisposable má následující metody.

|Metoda|Popis|
|------------|-----------------|
|Metody Dispose|Používá se k uvolnění nespravovaných prostředků.|

### <a name="requirements"></a>Požadavky

**Minimální podporovaná klienta:** Windows 8

**Minimální podporovaná serverem:** systému Windows Server 2012

**Namespace:** platformy