---
title: IF (MASM) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- if
dev_langs:
- C++
helpviewer_keywords:
- IF directive
ms.assetid: 82e43712-4f0c-4bf6-90ce-0663e81af707
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ca0cce834924f7fc147b1ef301d5bd345dfd2973
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43685304"
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