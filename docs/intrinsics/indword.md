---
title: __indword
ms.date: 09/02/2019
f1_keywords:
- __indword_cpp
- __indword
helpviewer_keywords:
- in instruction
- __indword intrinsic
ms.assetid: 1068d686-586e-4e36-b962-d1d7c3315260
ms.openlocfilehash: 790b65c8a565124df92b82b7ea17174788086a96
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222115"
---
# <a name="__indword"></a>__indword

**Specifické pro společnost Microsoft**

Přečte z určeného portu jedno z hodnot typu Double a pomocí `in` instrukce.

## <a name="syntax"></a>Syntaxe

```C
unsigned long __indword(
   unsigned short Port
);
```

### <a name="parameters"></a>Parametry

*Přístavní*\
pro Port, ze kterého se má číst.

## <a name="return-value"></a>Návratová hodnota

Slovo se načte z portu.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__indword`|x86, x64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Tato rutina je k dispozici pouze jako vnitřní objekt.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
