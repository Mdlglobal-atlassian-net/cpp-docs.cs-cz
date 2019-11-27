---
title: .FPO
ms.date: 11/05/2019
f1_keywords:
- .FPO
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
ms.openlocfilehash: 650c69be17c9271c343360edbb90f093841a1047
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74398247"
---
# <a name="fpo-32-bit-masm"></a>. Rpcrt4 (32-bit MASM)

Rozhraní **. Rpcrt4** direktiva řídí emise ladících záznamů do segmentu nebo oddílu. Debug $ F. (jenom 32-bitová MASM.)

## <a name="syntax"></a>Syntaxe

> **. Rpcrt4** (*cdwLocals*, *cdwParams*, *cbProlog*, *cbRegs*, *fUseBP*, *cbFrame*)

### <a name="parameters"></a>Parametry

*cdwLocals*\
Počet místních proměnných, nepodepsaná 32 bitová hodnota.

*cdwParams*\
Velikost parametrů v hodnotách DWORD, nepodepsaná 16bitová hodnota.

*cbProlog*\
Počet bajtů v kódu prologu funkce, nepodepsaná hodnota 8 bitů.

*cbRegs*\
Počet uložených registrů.

*fUseBP*\
Uvádí, zda byl přidělen EBP registr. buď 0, nebo 1.

*cbFrame*\
Určuje typ rámce.  Další informace najdete v tématu [FPO_DATA](/windows/win32/api/winnt/ns-winnt-fpo_data) .

## <a name="see-also"></a>Viz také:

[Odkazy na direktivy](directives-reference.md)
