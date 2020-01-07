---
title: .FPO
ms.date: 11/05/2019
f1_keywords:
- .FPO
helpviewer_keywords:
- .FPO directive
ms.assetid: 35f4cd61-32f9-4262-b657-73f04f775d09
ms.openlocfilehash: ec08be4941f81abed55420884b34dc817caf3f13
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317731"
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

\ – [referenční informace o direktivách](directives-reference.md)
[Gramatika BNF MASM](masm-bnf-grammar.md)
