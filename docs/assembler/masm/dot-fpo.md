---
title: .FPO
ms.date: 08/30/2018
f1_keywords:
- .FPO
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
ms.openlocfilehash: 3bdb6af98aa71fef3d4af24091dc7463d917ce15
ms.sourcegitcommit: 46d24d6e70c03e05484923d9efc6ed5150e96a64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2019
ms.locfileid: "68915952"
---
# <a name="fpo"></a>.FPO

Okně. Rpcrt4 direktiva řídí emise ladících záznamů do segmentu nebo oddílu. Debug $ F.

## <a name="syntax"></a>Syntaxe

> FPO (*cdwLocals*, *cdwParams*, *cbProlog*, *cbRegs*, *fUseBP*, *cbFrame*)

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
Určuje typ rámce.  Další informace najdete v tématu [FPO_DATA](/windows/desktop/api/winnt/ns-winnt-fpo_data) .

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>
