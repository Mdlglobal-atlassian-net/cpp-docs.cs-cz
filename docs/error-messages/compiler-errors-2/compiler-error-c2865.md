---
title: Chyba kompilátoru C2865 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2865
dev_langs:
- C++
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cc0a49f8e6ab42f7e607cd5f4f7cc91f6895abe0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46035160"
---
# <a name="compiler-error-c2865"></a>Chyba kompilátoru C2865

'function': Neplatné porovnání pro handle_or_pointer

Můžete porovnat odkazy na [třídy a struktury](../../windows/classes-and-structs-cpp-component-extensions.md) nebo spravované odkazové typy pouze pro rovnost zobrazíte, pokud se odkazují na stejný objekt (==) nebo k různým objektům (! =).

Nelze porovnávat je pro řazení, protože modul .NET runtime může být přesunout spravované objekty v okamžiku, změna výsledek testu.