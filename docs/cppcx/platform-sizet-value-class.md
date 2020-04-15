---
title: Platform::SizeT – hodnotová třída
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/PlatformSizeT::SizeT constructor
helpviewer_keywords:
- Platform::SizeT Struct
ms.assetid: 0803612c-8ba1-430c-9b7b-1bebae88608d
ms.openlocfilehash: 5add9212dc2655bc37cd357741073f855b009bde
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81322152"
---
# <a name="platformsizet-value-class"></a>Platform::SizeT – hodnotová třída

Představuje velikost objektu. SizeT je nepodepsaný datový typ.

## <a name="syntax"></a>Syntaxe

```cpp
public ref class SizeT sealed : ValueType
```

### <a name="members"></a>Členové

|Člen|Popis|
|------------|-----------------|
|[SizeT::Konstruktor SizeT](#ctor)|Inicializuje novou instanci třídy se zadanou hodnotou.|

### <a name="requirements"></a>Požadavky

**Minimální podporovaný klient:** Windows 8

**Minimální podporovaný server:** Windows Server 2012

**Obor názvů:** Platforma

**Metadata:** platform.winmd

## <a name="sizetsizet-constructor"></a><a name="ctor"></a>SizeT::Konstruktor SizeT

Inicializuje novou instanci SizeT se zadanou hodnotou.

### <a name="syntax"></a>Syntaxe

```cpp
SizeT( uint32 value1 );   SizeT( void* value2 );
```

### <a name="parameters"></a>Parametry

*hodnota1*<br/>
Nepodepsaná 32bitová hodnota.

*hodnota2*<br/>
Ukazatel na nepodepsanou 32bitovou hodnotu.

## <a name="see-also"></a>Viz také

[Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)
