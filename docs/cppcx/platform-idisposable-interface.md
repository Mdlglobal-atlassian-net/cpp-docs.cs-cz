---
title: Platform::IDisposable – rozhraní | Dokumentace Microsoftu
ms.custom: ''
ms.date: 02/03/2017
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::IDisposable
dev_langs:
- C++
helpviewer_keywords:
- Platform::IDisposable Interface
ms.assetid: f4344056-7030-42ed-bc98-b140edffddcd
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: c596e4054729855ea3c8caedf632ca8dd50b796a
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44105065"
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