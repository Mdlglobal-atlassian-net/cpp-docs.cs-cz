---
title: Platform::SizeT – hodnotová třída
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/PlatformSizeT::SizeT constructor
helpviewer_keywords:
- Platform::SizeT Struct
ms.assetid: 0803612c-8ba1-430c-9b7b-1bebae88608d
ms.openlocfilehash: 02fe62165ce40d267f156eaeb3ad93f636c9ab73
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604214"
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