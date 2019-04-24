---
title: .FPO
ms.date: 08/30/2018
f1_keywords:
- .FPO
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
ms.openlocfilehash: 83d6e81ea7dd35038f27f2721f3cc41fe49ef1bc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62204055"
---
# <a name="fpo"></a>.FPO

Na. FPO – direktiva určuje emisí záznamů ladění .debug$ F segment nebo část.

## <a name="syntax"></a>Syntaxe

> FPO (*cdwLocals*, *cdwParams*, *cbProlog*, *cbRegs*, *fUseBP*, *cbFrame*)

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