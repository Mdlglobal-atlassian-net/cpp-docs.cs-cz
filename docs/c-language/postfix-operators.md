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
ms.openlocfilehash: 338e518d1939cb6ea32aaf200c54b6c352287561
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43760260"
---
# <a name="postfix-operators"></a>Operátory přípony
Příponové operátory mají nejvyšší prioritu (tightest vazby) ve vyhodnocení výrazu.  

## <a name="syntax"></a>Syntaxe

*výraz přípony*:<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*primární – výraz*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony***[***výraz***]** <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony***(***argument-expression-list*<sub>optimalizované</sub> **)**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony***.**   *identifikátor*<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony***->***identifikátor* <br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **++**<br/>
&nbsp;&nbsp;&nbsp;&nbsp;*výraz přípony*  **--**

V této úrovni priority operátorů jsou subscripty pole, volání funkce, struktury a unie členy a zvýšení příponového operátora a operátory snížení.

## <a name="see-also"></a>Viz také

[Operátory jazyka C](../c-language/c-operators.md)