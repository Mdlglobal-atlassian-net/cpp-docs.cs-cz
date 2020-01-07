---
title: MACRO
ms.date: 12/16/2019
f1_keywords:
- MACRO
helpviewer_keywords:
- MACRO directive
ms.assetid: 89434f7c-bc2c-4e91-8940-fe2db8785233
ms.openlocfilehash: 23c6b0aefae856da449da574669e8475122c7556
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75312947"
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

## <a name="see-also"></a>Viz také:

\ – [referenční informace o direktivách](directives-reference.md)
[Goto (MASM)](goto-masm.md)\
[ENDM](endm.md)\
[Gramatika BNF MASM](masm-bnf-grammar.md)

