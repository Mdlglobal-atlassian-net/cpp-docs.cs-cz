---
title: Zastaralé konvence volání | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- __fortran
- __pascal
- __syscall
dev_langs:
- C++
helpviewer_keywords:
- WINAPI [C++]
- __syscall keyword [C++]
- __pascal keyword [C++]
- __fortran keyword [C++]
- calling conventions, obsolete
ms.assetid: a91fc665-034a-48ce-b6bd-d27125f308a7
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: eec6f8370103ed0256471c009d6e97cc693a1cd7
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071338"
---
# <a name="obsolete-calling-conventions"></a>Zastaralé konvence volání

## <a name="microsoft-specific"></a>Specifické pro Microsoft

**__Pascal**, **__fortran**, a **__syscall** již nejsou podporovány konvence volání. Jejich funkce lze simulovat pomocí jedné z podporovaných konvencí volání a vhodné možnosti linkeru.

\<Windows.h > nyní podporuje makro WINAPI, které se přeloží na odpovídající konvenci volání pro cíl. Použití rozhraní WINAPI, kde jste dříve používali PASCAL nebo **__far \__pascal**.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Konvence předávání a pojmenování argumentů](../cpp/argument-passing-and-naming-conventions.md)