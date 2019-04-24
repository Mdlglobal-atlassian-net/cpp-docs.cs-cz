---
title: __outbyte
ms.date: 11/04/2016
f1_keywords:
- __outbyte
helpviewer_keywords:
- out instruction
- __outbyte intrinsic
ms.assetid: c4cd1a34-8a02-4e37-993d-3201bc17901a
ms.openlocfilehash: 234892369572a2ee315687f5d70533a0c8cf4b59
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62262967"
---
# <a name="outbyte"></a>__outbyte

**Microsoft Specific**

Generuje `out` instrukce, která odesílá 1 bajtu určeného pomocí `Data` portu vstupně-výstupní operace určené `Port`.

## <a name="syntax"></a>Syntaxe

```
void __outbyte(
   unsigned short Port,
   unsigned char Data
);
```

#### <a name="parameters"></a>Parametry

*Port*<br/>
[in] Port pro odesílání dat na.

*Data*<br/>
[in] Bajt rozeslání zadaný port.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__outbyte`|x86, x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Tato rutina je k dispozici pouze jako vnitřní objekt.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)