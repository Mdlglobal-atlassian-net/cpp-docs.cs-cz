---
title: Platform::callbackcontext – výčet
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::CallbackContext
helpviewer_keywords:
- Platform::CallbackContext Enumeration
ms.assetid: 60e0c7cb-5d8f-482a-bdca-ca9335ae4899
ms.openlocfilehash: 7f4e020ab0b1e377456c27d3b4666e15b5a4f7a1
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50441351"
---
# <a name="platformcallbackcontext-enumeration"></a>Platform::callbackcontext – výčet

Určuje kontext vlákna, ve kterém se spustí funkce zpětného volání (Obslužná rutina události).

## <a name="syntax"></a>Syntaxe

```cpp
enum class CallbackContext {};
```

### <a name="members"></a>Členové

|Typ kódu|Popis|
|---------------|-----------------|
|Všechny|Funkce zpětného volání lze spustit v libovolném kontextu vlákna.|
|Stejné|Funkce zpětného volání lze spustit na pouze kontext vlákna, který spustil asynchronní operace.|

### <a name="requirements"></a>Požadavky

**Minimální podporovaná klienta:** Windows 8

**Minimální podporovaná serverem:** systému Windows Server 2012

**Namespace:** platformy

**Metadata:** platform.winmd