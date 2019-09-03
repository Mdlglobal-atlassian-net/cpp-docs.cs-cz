---
title: __inbyte
ms.date: 09/02/2019
f1_keywords:
- __inbyte
- __inbyte_cpp
helpviewer_keywords:
- in instruction
- __inbyte intrinsic
ms.assetid: 03b61799-2a08-474d-adc4-2cbf7c81a4d5
ms.openlocfilehash: f0036763ed7315a54fbfe6dcc873b46b52f0730c
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222139"
---
# <a name="__inbyte"></a>__inbyte

**Specifické pro společnost Microsoft**

Vygeneruje `Port`instrukci a vrátí jeden bajt čtený z portu určeného parametrem. `in`

## <a name="syntax"></a>Syntaxe

```C
unsigned char __inbyte(
   unsigned short Port
);
```

### <a name="parameters"></a>Parametry

*Přístavní*\
pro Port, ze kterého se má číst.

## <a name="return-value"></a>Návratová hodnota

Bajt načtený z určeného portu.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__inbyte`|x86, x64|

**Hlavičkový soubor** \<intrin. h >

**Specifické pro konec Microsoftu**

## <a name="remarks"></a>Poznámky

Tato rutina je k dispozici pouze jako vnitřní objekt.

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
