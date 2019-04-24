---
title: Operátory přípony
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C], postfix
- postfix operators
ms.assetid: 76260011-1624-484e-8bef-72ae7ab556cc
ms.openlocfilehash: a86ede25feeaee3a9fb1c6b146cf9667b85c0c2f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62232244"
---
# <a name="postfix-operators"></a>Operátory přípony

Příponové operátory mají nejvyšší prioritu (tightest vazby) ve vyhodnocení výrazu.

## <a name="syntax"></a>Syntaxe

*postfix-expression*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*primary-expression*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **[**  *výraz*  **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **(**  *argument-expression-list*<sub>optimalizované</sub> **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **.**  *identifier*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **->**  *identifikátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*postfix-expression*  **--**

V této úrovni priority operátorů jsou subscripty pole, volání funkce, struktury a unie členy a zvýšení příponového operátora a operátory snížení.

## <a name="see-also"></a>Viz také:

[Operátory jazyka C](../c-language/c-operators.md)
