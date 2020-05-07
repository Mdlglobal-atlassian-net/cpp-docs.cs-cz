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

Operátory přípon mají nejvyšší prioritu (nejužší vazbu) ve vyhodnocení výrazu.

## <a name="syntax"></a>Syntaxe

*výraz přípony*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*primární výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*příponový výraz*  **[**  *výraz*  **]**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **(**  *argument-expression-list*<sub>opt</sub> **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony***.**    *RID*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*identifikátor výrazu přípony***->***identifier*    <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **--**

Operátory v této úrovni priority jsou dolní indexy pole, volání funkce, členy struktury a sjednocení a operátory přírůstku a snížení přípon.

## <a name="see-also"></a>Viz také

[Operátory jazyka C](../c-language/c-operators.md)
