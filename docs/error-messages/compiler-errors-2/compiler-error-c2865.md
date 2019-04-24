---
title: Chyba kompilátoru C2865
ms.date: 11/04/2016
f1_keywords:
- C2865
helpviewer_keywords:
- C2865
ms.assetid: 973eb6a0-c99a-4d25-b3e5-fe0539794d77
ms.openlocfilehash: 38b7dd86a57c3cd89811c6489e51fb4271fd7b79
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62165141"
---
# <a name="compiler-error-c2865"></a>Chyba kompilátoru C2865

'function': Neplatné porovnání pro handle_or_pointer

Můžete porovnat odkazy na [třídy a struktury](../../extensions/classes-and-structs-cpp-component-extensions.md) nebo spravované odkazové typy pouze pro rovnost zobrazíte, pokud se odkazují na stejný objekt (==) nebo k různým objektům (! =).

Nelze porovnávat je pro řazení, protože modul .NET runtime může být přesunout spravované objekty v okamžiku, změna výsledek testu.