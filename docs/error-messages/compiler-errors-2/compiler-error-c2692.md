---
title: Chyba kompilátoru C2692
ms.date: 11/04/2016
f1_keywords:
- C2692
helpviewer_keywords:
- C2692
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
ms.openlocfilehash: c469f4944417c9116c7316b01642dd4b370b8c4b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257813"
---
# <a name="compiler-error-c2692"></a>Chyba kompilátoru C2692

'Název_funkce': v kompilátoru C používat plně prototypované funkce "/ clr' možnost

Při kompilaci pro .NET spravovaného kódu, kompilátor jazyka C vyžaduje deklarace funkcí ANSI. Kromě toho, pokud funkce nepřijímá žádné parametry, se musí explicitně deklarovat `void` jako typ parametru.