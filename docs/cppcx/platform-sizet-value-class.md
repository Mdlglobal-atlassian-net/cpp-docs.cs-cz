---
title: Platform::sizet – hodnotová třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 12/30/2016
ms.technology: cpp-windows
ms.topic: reference
f1_keywords:
- VCCORLIB/PlatformSizeT::SizeT constructor
dev_langs:
- C++
helpviewer_keywords:
- Platform::SizeT Struct
ms.assetid: 0803612c-8ba1-430c-9b7b-1bebae88608d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b78d205956f026fe730848afa4c0d6fe7b52b52c
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44101999"
---
# <a name="platformsizet-value-class"></a>Platform::SizeT – hodnotová třída

Představuje velikost objektu. SizeT je bez znaménka datového typu.

## <a name="syntax"></a>Syntaxe

```cpp
public ref class SizeT sealed : ValueType
```

### <a name="members"></a>Členové

|Člen|Popis|
|------------|-----------------|
|[SizeT::SizeT konstruktor](#ctor)|Inicializuje novou instanci třídy se zadanou hodnotou.|

### <a name="requirements"></a>Požadavky

**Minimální podporovaná klienta:** Windows 8

**Minimální podporovaná serverem:** systému Windows Server 2012

**Namespace:** platformy

**Metadata:** platform.winmd

## <a name="ctor"></a>  SizeT::SizeT konstruktor

Inicializuje novou instanci třídy SizeT se zadanou hodnotou.

### <a name="syntax"></a>Syntaxe

```cpp
SizeT( uint32 value1 );   SizeT( void* value2 );
```

### <a name="parameters"></a>Parametry

*Hodnota1*<br/>
32bitové hodnoty bez znaménka.

*Hodnota2*<br/>
Ukazatel na 32bitové hodnoty bez znaménka.

## <a name="see-also"></a>Viz také

[Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)