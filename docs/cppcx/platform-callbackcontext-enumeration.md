---
title: Platform::callbackcontext – výčet | Dokumentace Microsoftu
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::CallbackContext
dev_langs:
- C++
helpviewer_keywords:
- Platform::CallbackContext Enumeration
ms.assetid: 60e0c7cb-5d8f-482a-bdca-ca9335ae4899
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: fe988a7dee7fb358d9454c06811d7baf2cd4ace0
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44101960"
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