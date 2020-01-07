---
title: ASSUME
ms.date: 11/05/2019
f1_keywords:
- ASSUME
helpviewer_keywords:
- ASSUME directive
ms.assetid: cd162070-aee9-4c65-babc-005c6cc73d7c
ms.openlocfilehash: a74a5336e626f561f1fc61e866792ce193332d84
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316535"
---
# <a name="assume"></a>ASSUME

Povoluje kontrolu chyb hodnot registru. (jenom 32-bitová MASM.)

## <a name="syntax"></a>Syntaxe

> **Předpokládejme**  *segregister* __:__ *název* ⟦ __,__ *segregister* __:__ *název*... ⟧\
> **Předpokládejme**  *dataregister* __:__ *Zadejte* ⟦ __,__ *dataregistry* __:__ *Type*... ⟧\
> **Předpokládat**  *registraci* __: Chyba__ ⟦ __,__ *Register* __: Error__... ⟧\
> **Předpokládat** ⟦*registr* __:__ ⟧**Nothing** ⟦ __;__ *Register* __: Nothing__... ⟧

## <a name="remarks"></a>Poznámky

Po navýšení **předpokládáme** , že Assembler sleduje změny v hodnotách daných registrů. **Při** použití registru dojde k chybě. **Nic** neodebere kontrolu chyb registru. V jednom příkazu můžete kombinovat různé druhy předpokladů.

## <a name="see-also"></a>Viz také:

\ – [referenční informace o direktivách](directives-reference.md)
[Gramatika BNF MASM](masm-bnf-grammar.md)
