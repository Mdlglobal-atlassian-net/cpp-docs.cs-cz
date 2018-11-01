---
title: PROTO
ms.date: 10/22/2018
f1_keywords:
- PROTO
helpviewer_keywords:
- PROTO directive
ms.assetid: 0487ee16-9dc7-43d1-9445-cd1601f5a080
ms.openlocfilehash: 616b6be2a5c191ebc67d61288cb5fa6c183091fa
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50536714"
---
# <a name="proto"></a>PROTO

Prototypy funkce nebo procedury. Můžete volat funkce prototypem pomocí PROTO – direktiva pomocí [INVOKE](invoke.md) směrnice.

## <a name="syntax"></a>Syntaxe

> *Popisek* **PROTO** \[ *vzdálenost*] \[ *langtype*] \[ __,__ \[ *parametr*]__:__*značka*]...

### <a name="parameters"></a>Parametry

*Popisek*<br/>
Název nevolá se prototypovaná funkce.

*vzdálenost*<br/>
(Volitelné) Použít v modelech paměti 16 bitů výchozí hodnotu přepsat a uvede **NEAR** nebo **FAR** volání.

*langtype*<br/>
(Volitelné) Nastaví konvence pojmenování a volání procedury a veřejných symbolů. Podporované konvence jsou:

- 32-bit **PLOCHÝ** modelu: **C**, **STDCALL**

- modely 16 bitů: **C**, **BASIC**, **až po FORTRAN**, **PASCAL**, **SYSCALL**, **STDCALL**

*Parametr*<br/>
Volitelný název parametru funkce.

*Značka*<br/>
Typ parametru funkce.

*Parametr* a *značka* parametrů může být více než jednou, jednou pro každý předaný argument.

## <a name="example"></a>Příklad

Tento příklad ukazuje **PROTO** deklarace pro funkce s názvem `addup3` , která používá **NEAR** volání k přepsání pro volání procedur a používá výchozí model 16 bitů **C**konvence volání pro zásobníku parametrů a návratové hodnoty. Přebírá dva argumenty **slovo** a **VARARG**.

```MASM
addup3 PROTO NEAR C, argcount:WORD, arg1:VARARG
```

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](directives-reference.md)<br/>
[. Referenční informace k modelu](dot-model.md)<br/>
