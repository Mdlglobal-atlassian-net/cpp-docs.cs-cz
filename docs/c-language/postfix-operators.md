---
title: Operátory přípony
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C], postfix
- postfix operators
ms.assetid: 76260011-1624-484e-8bef-72ae7ab556cc
ms.openlocfilehash: a86ede25feeaee3a9fb1c6b146cf9667b85c0c2f
ms.sourcegitcommit: f4be868c0d1d78e550fba105d4d3c993743a1f4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/12/2019
ms.locfileid: "56147903"
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
