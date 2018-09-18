---
title: Operátory přípony | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- operators [C], postfix
- postfix operators
ms.assetid: 76260011-1624-484e-8bef-72ae7ab556cc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 3d8d3a762cb3eed3b0182185561c33b073b571b1
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036056"
---
# <a name="postfix-operators"></a>Operátory přípony

Příponové operátory mají nejvyšší prioritu (tightest vazby) ve vyhodnocení výrazu.

## <a name="syntax"></a>Syntaxe

*výraz přípony*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*primární – výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony***[***výraz***]** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony***(***argument-expression-list*<sub>optimalizované</sub> **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony***.**  *identifikátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony***->***identifikátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **--**

V této úrovni priority operátorů jsou subscripty pole, volání funkce, struktury a unie členy a zvýšení příponového operátora a operátory snížení.

## <a name="see-also"></a>Viz také

[Operátory jazyka C](../c-language/c-operators.md)