---
title: __readmsr
ms.date: 11/04/2016
f1_keywords:
- __readmsr
helpviewer_keywords:
- Read Model Specific Register
- rdmsr instruction
- __readmsr intrinsic
ms.assetid: 7ab1f8e8-72cb-4ce4-817d-3e728a3c9716
ms.openlocfilehash: 2c866213c452f3b8791bf0fe031a43bb024e91fb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62262772"
---
# <a name="readmsr"></a>__readmsr

**Microsoft Specific**

Generuje `rdmsr` instrukce, který čte register specifické pro model určený `register` a vrátí jeho hodnotu.

## <a name="syntax"></a>Syntaxe

```
__int64 __readmsr(
   int register
);
```

#### <a name="parameters"></a>Parametry

*register*<br/>
[in] Model konkrétním registru ke čtení.

## <a name="return-value"></a>Návratová hodnota

Hodnota do zadaného registru.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__readmsr`|x86, x64|

**Soubor hlaviček** \<intrin.h >

## <a name="remarks"></a>Poznámky

Tato funkce je dostupná pouze v režimu jádra a rutina je dostupný jenom jako vnitřní.

Další informace najdete v dokumentaci k AMD.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Vnitřní funkce kompilátoru](../intrinsics/compiler-intrinsics.md)