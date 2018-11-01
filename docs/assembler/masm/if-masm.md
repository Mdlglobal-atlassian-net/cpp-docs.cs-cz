---
title: IF (MASM)
ms.date: 08/30/2018
f1_keywords:
- if
helpviewer_keywords:
- IF directive
ms.assetid: 82e43712-4f0c-4bf6-90ce-0663e81af707
ms.openlocfilehash: 2b91698640e028bf91d822c12b85ded651a04d8d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555778"
---
# <a name="if-masm"></a>IF (MASM)

Uděluje sestavení *ifstatements* Pokud *expression1* hodnotu true (nenulovou) nebo *elseifstatements* Pokud *expression1* má hodnotu false (0) a *expression2* má hodnotu true.

## <a name="syntax"></a>Syntaxe

> Pokud *expression1*<br/>
> *ifstatements*<br/>
> [[ELSEIF *expression2*<br/>
> *elseifstatements*]]<br/>
> [[ELSE<br/>
> *elsestatements*]]<br/>
> ENDIF

## <a name="remarks"></a>Poznámky

Může být následující direktivy nahrazeno [ELSEIF](../../assembler/masm/elseif-masm.md): **ELSEIFB**, **ELSEIFDEF**, **ELSEIFDIF**, **ELSEIFDIFI** , **ELSEIFE**, **ELSEIFIDN**, **ELSEIFIDNI**, **ELSEIFNB**, a **ELSEIFNDEF** . Volitelně můžete sestaví *elsestatements* Pokud předchozí výraz je nepravdivý. Všimněte si, že výrazy jsou vyhodnocovány v době sestavení.

## <a name="see-also"></a>Viz také:

[Referenční dokumentace k direktivám](../../assembler/masm/directives-reference.md)<br/>