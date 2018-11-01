---
title: .FPO
ms.date: 08/30/2018
f1_keywords:
- .FPO
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
ms.openlocfilehash: 83d6e81ea7dd35038f27f2721f3cc41fe49ef1bc
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50570499"
---
# <a name="fpo"></a>.FPO

Na. FPO – direktiva určuje emisí záznamů ladění .debug$ F segment nebo část.

## <a name="syntax"></a>Syntaxe

> FPO (*cdwLocals*, *cdwParams*, *cbProlog*, *cbRegs*, *fUseBP*,  *cbFrame*)

### <a name="parameters"></a>Parametry

*cdwLocals*<br/>
Počet místních proměnných, je hodnota bez znaménka 32 bitů.

*cdwParams*<br/>
Velikost parametrů v DWORD, je hodnota bez znaménka 16 bitů.

*cbProlog*<br/>
Počet bajtů v kódu prologu funkce, je hodnota bez znaménka 8 bitů.

*cbRegs*<br/>
Uložit číslo registrů.

*fUseBP*<br/>
Určuje, zda byl přidělen do registru EBP. 0 nebo 1.

*cbFrame*<br/>
Určuje typ rámce.  Zobrazit [FPO_DATA](/windows/desktop/api/winnt/ns-winnt-_fpo_data) Další informace.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>