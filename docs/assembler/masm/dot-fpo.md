---
title: .FPO
ms.date: 11/05/2019
f1_keywords:
- .FPO
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
ms.openlocfilehash: 3938d9194c35d567ea670e0b92a731193ccd2254
ms.sourcegitcommit: 45f1d889df633f0f7e4a8e813b46fa73c9858b81
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/06/2019
ms.locfileid: "73703798"
---
# <a name="fpo-32-bit-masm"></a>. Rpcrt4 (32-bit MASM)

Okně. Rpcrt4 direktiva řídí emise ladících záznamů do segmentu nebo oddílu. Debug $ F. (jenom 32-bitová MASM.)

## <a name="syntax"></a>Syntaxe

> Rpcrt4 (*cdwLocals*, *cdwParams*, *cbProlog*, *cbRegs*, *fUseBP*, *cbFrame*)

### <a name="parameters"></a>Parametry

*cdwLocals*<br/>
Počet místních proměnných, nepodepsaná 32 bitová hodnota.

*cdwParams*<br/>
Velikost parametrů v hodnotách DWORD, nepodepsaná 16bitová hodnota.

*cbProlog*<br/>
Počet bajtů v kódu prologu funkce, nepodepsaná hodnota 8 bitů.

*cbRegs*<br/>
Počet uložených registrů.

*fUseBP*<br/>
Uvádí, zda byl přidělen EBP registr. buď 0, nebo 1.

*cbFrame*<br/>
Určuje typ rámce.  Další informace najdete v tématu [FPO_DATA](/windows/win32/api/winnt/ns-winnt-fpo_data) .

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>
