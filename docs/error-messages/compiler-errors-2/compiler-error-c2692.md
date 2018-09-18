---
title: Chyba kompilátoru C2692 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2692
dev_langs:
- C++
helpviewer_keywords:
- C2692
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 03a9006889c5853e77b5603484ea9d18f2474241
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088368"
---
# <a name="compiler-error-c2692"></a>Chyba kompilátoru C2692

'Název_funkce': v kompilátoru C používat plně prototypované funkce "/ clr' možnost

Při kompilaci pro .NET spravovaného kódu, kompilátor jazyka C vyžaduje deklarace funkcí ANSI. Kromě toho, pokud funkce nepřijímá žádné parametry, se musí explicitně deklarovat `void` jako typ parametru.