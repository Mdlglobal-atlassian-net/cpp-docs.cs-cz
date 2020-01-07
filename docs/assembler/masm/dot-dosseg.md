---
title: .DOSSEG
ms.date: 11/05/2019
f1_keywords:
- .DOSSEG
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
ms.openlocfilehash: e27b0ae185542c11ee29119575d5c8225501f71e
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75313844"
---
# <a name="dosseg-32-bit-masm"></a>. DOSSEG – (32-bit MASM)

Seřadí segmenty podle konvence segmentů pro systém MS-DOS: nejprve CODE, pak segmenty nejsou v DGROUP a pak segmenty v DGROUP. (jenom 32-bitová MASM.)

## <a name="syntax"></a>Syntaxe

> **.DOSSEG**

## <a name="remarks"></a>Poznámky

Segmenty v DGROUP se řídí tímto pořadím: segmenty nejsou v BSS nebo STACK, pak segmenty BSS a nakonec segmenty zásobníku. Primárně se používá pro zajištění podpory CodeView v samostatných programech MASM. Stejné jako [dosseg –](dosseg.md).

## <a name="see-also"></a>Viz také:

\ – [referenční informace o direktivách](directives-reference.md)
[Gramatika BNF MASM](masm-bnf-grammar.md)
