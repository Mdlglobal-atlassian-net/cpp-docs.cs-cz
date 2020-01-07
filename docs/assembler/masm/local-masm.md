---
title: LOCAL (MASM)
ms.date: 12/16/2019
f1_keywords:
- Local
helpviewer_keywords:
- LOCAL directive
ms.assetid: 76147e2d-23ca-4f1e-8817-81428becd113
ms.openlocfilehash: 2bef6b26f1b922be6512bd6ebe8e0b2627e86f45
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317146"
---
# <a name="local"></a>LOCAL

V první direktivě v rámci makra **místní** definuje popisky, které jsou jedinečné pro jednotlivé instance makra.

## <a name="syntax"></a>Syntaxe

> **Místní** *LocalId* ⟦, *LocalId* ... ⟧
>
> **Local** *labelId* ⟦ __\[__ *Count* __]__ ⟧ ⟦ __:__ *qualifiedType*⟧ ⟦ __,__ *labelId* ⟦ __\[__ *Count* __]__ *⟧ ⟦ qualifiedType ⟧.* .. ⟧

## <a name="remarks"></a>Poznámky

V druhé direktivě v rámci definice procedury (**proc**) vytvoří **místní** proměnné založené na zásobníku, které existují po dobu trvání procedury. *LabelId* může být jednoduchá proměnná nebo pole obsahující *počet* prvků, kde *Count* je konstantní výraz.

## <a name="see-also"></a>Viz také:

\ – [referenční informace o direktivách](directives-reference.md)
[Gramatika BNF MASM](masm-bnf-grammar.md)
