---
title: __readpmc
ms.date: 09/02/2019
f1_keywords:
- __readpmc
helpviewer_keywords:
- Read Performance Monitoring Counters instruction
- __readpmc intrinsic
- rdpmc instruction
ms.assetid: 14ed45a6-28b6-4635-8437-a597c04b43d4
ms.openlocfilehash: af0f1874d991771423ddebfedd4624cd0b71760f
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70221032"
---
# <a name="__readpmc"></a>__readpmc

**Specifické pro společnost Microsoft**

Vygeneruje instrukci, která načte Čítač sledování výkonu určený čítačem. `rdpmc`

## <a name="syntax"></a>Syntaxe

```C
unsigned __int64 __readpmc(
   unsigned long counter
);
```

### <a name="parameters"></a>Parametry

*objektů*\
pro Čítač výkonu, který se má přečíst.

## <a name="return-value"></a>Návratová hodnota

Hodnota zadaného čítače výkonu.

## <a name="requirements"></a>Požadavky

|Vnitřním|Architektura|
|---------------|------------------|
|`__readpmc`|x86, x64|

**Hlavičkový soubor** \<intrin. h >

## <a name="remarks"></a>Poznámky

Vnitřní funkce je k dispozici pouze v režimu jádra a rutina je k dispozici pouze jako vnitřní.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)
