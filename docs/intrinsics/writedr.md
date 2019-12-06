---
title: __writedr
ms.date: 09/02/2019
f1_keywords:
- __writedr
helpviewer_keywords:
- __writedr intrinsic
ms.assetid: ac55c1ee-df2f-41d4-a429-6f369d2a934d
ms.openlocfilehash: 473e7223e9974d0125e772c152ea85ae90b97342
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74858058"
---
# <a name="__writedr"></a>__writedr

**Specifické pro společnost Microsoft**

Zapíše zadanou hodnotu do určeného registru pro ladění.

## <a name="syntax"></a>Syntaxe

```C
void __writedr(unsigned DebugRegister, unsigned DebugValue); /* x86 */
void __writedr(unsigned DebugRegister, unsigned __int64 DebugValue); /* x64 */
```

### <a name="parameters"></a>Parametry

*DebugRegister*\
pro Číslo od 0 do 7, které identifikuje registr ladění.

*DebugValue*\
pro Hodnota, která se má zapsat do registru ladění.

## <a name="remarks"></a>Poznámky

Tyto vnitřní objekty jsou k dispozici pouze v režimu jádra a rutiny jsou k dispozici pouze jako vnitřní.

## <a name="requirements"></a>Požadavky

|Vnitřní|Architektura|
|---------------|------------------|
|`__writedr`|x86, x64|

**Hlavičkový soubor** \<intrin. h >

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Vnitřní objekty kompilátoru](../intrinsics/compiler-intrinsics.md)\
[__readdr](../intrinsics/readdr.md)
