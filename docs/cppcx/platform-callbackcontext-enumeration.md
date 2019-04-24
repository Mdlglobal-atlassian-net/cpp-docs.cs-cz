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
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62161663"
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
|Jakýkoli|Funkce zpětného volání lze spustit v libovolném kontextu vlákna.|
|Stejné|Funkce zpětného volání lze spustit na pouze kontext vlákna, který spustil asynchronní operace.|

### <a name="requirements"></a>Požadavky

**Minimální podporovaná klienta:** Windows 8

**Minimální podporovaná serveru:** Windows Server 2012

**Namespace:** Platforma

**Metadata:** platform.winmd