---
title: __inword
ms.date: 09/02/2019
f1_keywords:
- __inword_cpp
- __inword
helpviewer_keywords:
- in instruction
- __inword intrinsic
ms.assetid: 5c617edd-6709-40a1-aad2-40d5e39283c6
ms.openlocfilehash: 7daaf1abd5089716061f118e30e9534e5c5c18ee
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79440974"
---
# <a name="__inword"></a>__inword

**Specifické pro společnost Microsoft**

Načte data z určeného portu pomocí instrukce `in`.

## <a name="syntax"></a>Syntaxe

```C
unsigned short __inword(
   unsigned short Port
);
```

### <a name="parameters"></a>Parametry

\ *portu*
pro Port, ze kterého se má číst.

## <a name="return-value"></a>Návratová hodnota

Slovo přečtených dat

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__inword`|x86, x64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Tato rutina je k dispozici pouze jako vnitřní objekt.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
