---
title: __writeeflags
ms.date: 09/02/2019
f1_keywords:
- __writeeflags
helpviewer_keywords:
- __writeeflags intrinsics
ms.assetid: a62a522c-d7fa-4f10-a620-a3b32bdf3f17
ms.openlocfilehash: 6b9b6976369ed810789e5749a2e30029cad4c2d7
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74858045"
---
# <a name="__writeeflags"></a>__writeeflags

**Specifické pro společnost Microsoft**

Zapíše zadanou hodnotu do registru status program and Control (EFLAGS).

## <a name="syntax"></a>Syntaxe

```C
void __writeeflags(unsigned Value); /* x86 */
void __writeeflags(unsigned __int64 Value); /* x64 */
```

### <a name="parameters"></a>Parametry

*Hodnota*\
pro Hodnota, která se má zapsat do registru EFLAGS Parametr `Value` je pro 32 bitovou platformu dlouhý 32 bitů a v případě 64bitové platformy se 64 bity 64 prodlouží.

## <a name="remarks"></a>Poznámky

Tyto rutiny jsou k dispozici pouze jako vnitřní objekty.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__writeeflags`|x86, x64|

**Hlavičkový soubor** \<intrin. h >

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[__readeflags](../intrinsics/readeflags.md)
