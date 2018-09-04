---
title: . DOSSEG | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- .DOSSEG
dev_langs:
- C++
helpviewer_keywords:
- .DOSSEG directive
ms.assetid: 175ad470-0a2b-4e2b-b078-65e224fec040
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 33ee0b0b049ece65786c4d4857c2e082a067fee4
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43693229"
---
# <a name="dosseg"></a>.DOSSEG

Seřadí segmentů podle úmluvy segmentu zástupného kódu MS-DOS: kód nejprve pak segmenty nejsou v DGROUP a potom segmenty v DGROUP.

## <a name="syntax"></a>Syntaxe

> .DOSSEG

## <a name="remarks"></a>Poznámky

Toto pořadí podle segmentů v DGROUP: segmenty nejsou v BSS nebo zásobníku, pak BSS segmentů a nakonec zásobníku segmentů. Používá se především pro zajištění podpory CodeView v programech samostatného MASM. Stejné jako [DOSSEG](../../assembler/masm/dosseg.md).

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>