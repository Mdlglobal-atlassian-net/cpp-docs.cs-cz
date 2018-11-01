---
title: Operátory přípony
ms.date: 11/04/2016
helpviewer_keywords:
- operators [C], postfix
- postfix operators
ms.assetid: 76260011-1624-484e-8bef-72ae7ab556cc
ms.openlocfilehash: 45f7b67b62657c498bdd9ebcf5d85379cdcdd211
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50440701"
---
# <a name="postfix-operators"></a>Operátory přípony

Příponové operátory mají nejvyšší prioritu (tightest vazby) ve vyhodnocení výrazu.

## <a name="syntax"></a>Syntaxe

*výraz přípony*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*primární – výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **[**  *výraz*  **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **(**  *argument-expression-list*<sub>optimalizované</sub> **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **.**  *identifikátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **->**  *identifikátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **--**

V této úrovni priority operátorů jsou subscripty pole, volání funkce, struktury a unie členy a zvýšení příponového operátora a operátory snížení.

## <a name="see-also"></a>Viz také

[Operátory jazyka C](../c-language/c-operators.md)