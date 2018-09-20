---
title: __inbyte | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- __inbyte
- __inbyte_cpp
dev_langs:
- C++
helpviewer_keywords:
- in instruction
- __inbyte intrinsic
ms.assetid: 03b61799-2a08-474d-adc4-2cbf7c81a4d5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7e9b4950c16cdab8dd282f772e84f7f222246328
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46414456"
---
# <a name="inbyte"></a>__inbyte

**Specifické pro Microsoft**

Generuje `in` instrukce, vrací jeden bajt čtení z portu určené `Port`.

## <a name="syntax"></a>Syntaxe

```
unsigned char __inbyte(
   unsigned short Port
);
```

#### <a name="parameters"></a>Parametry

*Port*<br/>
[in] Port, který se má číst z.

## <a name="return-value"></a>Návratová hodnota

Číst bajt z zadaný port.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__inbyte`|x86, x64|

**Soubor hlaviček** \<intrin.h >

**Specifické pro END Microsoft**

## <a name="remarks"></a>Poznámky

Tato rutina je k dispozici pouze jako vnitřní objekt.

## <a name="see-also"></a>Viz také

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)