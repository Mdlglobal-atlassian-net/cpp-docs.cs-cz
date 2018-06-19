---
title: Logpen – struktura | Microsoft Docs
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
ms.openlocfilehash: 4c0e07ce3a38eaca54e860ebe821924c0f564c69
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33374147"
---
# <a name="logpen-structure"></a>LOGPEN – struktura
`LOGPEN` Struktura definuje styl, šířku a barvy pera, objektu použitý k vykreslení čar a ohraničení. [CPen::CreatePenIndirect](../../mfc/reference/cpen-class.md#createpenindirect) využívá `LOGPEN` struktura.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
typedef struct tagLOGPEN {  /* lgpn */  
    UINT lopnStyle;  
    POINT lopnWidth;  
    COLORREF lopnColor;  
} LOGPEN;  
```  
  
#### <a name="parameters"></a>Parametry  
 *lopnStyle*  
 Určuje typ pera. Tento člen může být jedna z následujících hodnot:  
  
- **PS_SOLID** vytvoří pera plnou.  
  
- **PS_DASH** vytvoří pera přerušovanou. (Platí jenom v případě, že šířku pera je 1.)  
  
- **PS_DOT** vytvoří pera s tečkou. (Platí jenom v případě, že šířku pera je 1.)  
  
- **PS_DASHDOT** vytvoří pera s různými pomlčky a tečky. (Platí jenom v případě, že šířku pera je 1.)  
  
- **PS_DASHDOTDOT** vytvoří pera s různými pomlčky a tečky double. (Platí jenom v případě, že šířku pera je 1.)  
  
- **PS_NULL** vytvoří pera hodnotu null.  
  
- **PS_INSIDEFRAME** vytvoří pera, který se vykreslí řádku uvnitř rámečku uzavřené obrazce vyprodukované GDI výstup funkce, které zadejte ohraničující obdélník (například **elipsy**, **obdélníku**, `RoundRect`, `Pie`, a `Chord` členské funkce). Pokud je tento styl používá pomocí GDI výstup funkce, které neurčují ohraničující obdélník (například `LineTo` – členská funkce), oblasti výkresu pera není omezeno rámečku.  
  
     Pokud má pera **PS_INSIDEFRAME** stylu a barvy, která neodpovídá barvu v tabulce barev logické pera vykreslením s tónovaná barva. **PS_SOLID** styl pera nelze použít k vytvoření pera s tónovaná barva. **PS_INSIDEFRAME** styl je stejný jako **PS_SOLID** Pokud šířku pera je menší než nebo rovna 1.  
  
     Když **PS_INSIDEFRAME** styl se používá s objekty GDI vyprodukované funkce jiné než **elipsy**, **obdélníku**, a `RoundRect`, řádku nemusí být zcela uvnitř zadaného rámce.  
  
 *lopnWidth*  
 Určuje šířku pera v logické jednotky. Pokud **lopnWidth** člen je 0, 1 pixel široká na rastrové zařízení bez ohledu na aktuální režim mapování pera.  
  
 *lopnColor*  
 Určuje barvu pera.  
  
## <a name="remarks"></a>Poznámky  
 **y** hodnotu [bodu](../../mfc/reference/point-structure1.md) struktury pro **lopnWidth** člen není použit.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** wingdi.h systému  
  
## <a name="see-also"></a>Viz také  
 [Struktury, styly, zpětná volání a mapy zpráv](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [CPen::CreatePenIndirect](../../mfc/reference/cpen-class.md#createpenindirect)

