---
title: MACRO
ms.date: 12/16/2019
f1_keywords:
- MACRO
helpviewer_keywords:
- MACRO directive
ms.assetid: 89434f7c-bc2c-4e91-8940-fe2db8785233
ms.openlocfilehash: 8eb0afdf73270c3e741f43b2e1fba02fe965846c
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076137"
---
# <a name="macro"></a>MACRO

Označí blok makra nazvaný *Name* a naváže zástupné symboly *parametrů* pro argumenty předané při volání makra.

## <a name="syntax"></a>Syntaxe

> *název***makra** ⟦*parametr* ⟦ **: REQ** | : =*výchozí* | *args* **: vararg**⟧... ⟧\
> \ *příkazů*
⟦**Goto** :*macrolabelId*⟧ \
> ⟦**EXITM**⟧ \
> **ENDM** ⟦*Value*⟧

## <a name="remarks"></a>Poznámky

Funkce makra vrátí *hodnotu* do příkazu volání.

## <a name="see-also"></a>Viz také

\ – [referenční informace o direktivách](directives-reference.md)
[Goto (MASM)](goto-masm.md)\
[ENDM](endm.md)\
[Gramatika BNF MASM](masm-bnf-grammar.md)
