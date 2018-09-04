---
title: . FPO | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .FPO
dev_langs:
- C++
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: be5e20716ff414eea3eddc8490e2a3f82adeb777
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43687742"
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