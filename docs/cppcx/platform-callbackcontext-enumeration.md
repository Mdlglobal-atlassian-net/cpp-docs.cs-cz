---
title: 'Platform:: CallbackContext – výčet'
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::CallbackContext
helpviewer_keywords:
- Platform::CallbackContext Enumeration
ms.assetid: 60e0c7cb-5d8f-482a-bdca-ca9335ae4899
ms.openlocfilehash: 1daa3988fcb985dab9d3083233a3703a20cc2fdb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80214257"
---
# <a name="platformcallbackcontext-enumeration"></a>Platform:: CallbackContext – výčet

Určuje kontext vlákna, ve kterém se spustí funkce zpětného volání (obslužná rutina události).

## <a name="syntax"></a>Syntaxe

```cpp
enum class CallbackContext {};
```

### <a name="members"></a>Členové

|Kód typu|Popis|
|---------------|-----------------|
|Vše|Funkce zpětného volání může být spuštěna v jakémkoli kontextu vlákna.|
|Jedné|Funkce zpětného volání může být spuštěna pouze v kontextu vlákna, který spustil asynchronní operaci.|

### <a name="requirements"></a>Požadavky

**Minimální podporovaný klient:** Systém Windows 8

**Minimální podporovaný Server:** Windows Server 2012

**Obor názvů:** Platformy

**Metadata:** Platform. winmd
