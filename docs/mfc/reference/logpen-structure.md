---
title: Logpen – struktura | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- LOGPEN
dev_langs:
- C++
helpviewer_keywords:
- LOGPEN structure [MFC]
ms.assetid: a89e8690-6b61-4af5-990c-7c82da24f3b0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: a535858a0d5540db481fd42918b4079f30c90728
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46375666"
---
# <a name="logpen-structure"></a>LOGPEN – struktura

`LOGPEN` Struktury definuje styl, šířku a barvu pera, kreslení objekt použitý k vykreslení čar a ohraničení. [CPen::CreatePenIndirect](../../mfc/reference/cpen-class.md#createpenindirect) funkce používá `LOGPEN` struktury.

## <a name="syntax"></a>Syntaxe

```
typedef struct tagLOGPEN {  /* lgpn */
    UINT lopnStyle;
    POINT lopnWidth;
    COLORREF lopnColor;
} LOGPEN;
```

#### <a name="parameters"></a>Parametry

*lopnStyle*<br/>
Určuje typ pera. Tento člen může být jeden z následujících hodnot:

- PS_SOLID vytvoří solid pera.

- PS_DASH vytváří čárkovanou pera. (Platí jenom v případě šířku pera je 1.)

- PS_DOT vytvoří tečkovaná pera. (Platí jenom v případě šířku pera je 1.)

- Vytvoří PS_DASHDOT pera s různými pomlčky a tečky. (Platí jenom v případě šířku pera je 1.)

- PS_DASHDOTDOT vytvoří a psaní perem s různými pomlčky a tečky double. (Platí jenom v případě šířku pera je 1.)

- PS_NULL vytvoří null pera.

- Funkce, které určují ohraničující obdélník PS_INSIDEFRAME vytvoří vytvořený pera nakreslí čáru uvnitř rámečku uzavřené obrazce v GDI výstup (například `Ellipse`, `Rectangle`, `RoundRect`, `Pie`, a `Chord` člena funkce). Při použití tohoto stylu s GDI výstupních funkcí, které neurčují ohraničující obdélník (například `LineTo` členská funkce), oblasti pro kreslení pera není omezeno rámečkem.

     Pokud pera PS_INSIDEFRAME styl a barvy, který neodpovídá barvu v tabulce barev logické, pera je vykreslen s tónovaná barva. Styl psaní perem PS_SOLID nelze použít k vytvoření pera dithered pro bitové barvou. Pokud šířka pera je menší než nebo rovno 1 se shoduje s PS_SOLID PS_INSIDEFRAME style.

     Při použití stylu PS_INSIDEFRAME s objekty GDI vytvořené pomocí funkcí jiné než `Ellipse`, `Rectangle`, a `RoundRect`, řádku nemusí být zcela v zadaném rámci.

*lopnWidth*<br/>
Určuje šířku pera v logických jednotkách. Pokud `lopnWidth` člen je 0, pera je 1 pixelu široké rastrové zařízení bez ohledu na aktuální režim mapování.

*lopnColor*<br/>
Určuje barvu pera.

## <a name="remarks"></a>Poznámky

`y` Hodnotu [bodu](../../mfc/reference/point-structure1.md) strukturu pro `lopnWidth` člena se nepoužívá.

## <a name="requirements"></a>Požadavky

**Záhlaví:** wingdi.h

## <a name="see-also"></a>Viz také

[Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[CPen::CreatePenIndirect](../../mfc/reference/cpen-class.md#createpenindirect)

