---
title: Chyba kompilátoru C2692
ms.date: 11/04/2016
f1_keywords:
- C2692
helpviewer_keywords:
- C2692
ms.assetid: 02ade3b4-b757-448b-b065-d7d71bc3f441
ms.openlocfilehash: 7ce57cd50e9ec83cf80ec64e14f49eb9714f9208
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80177089"
---
# <a name="compiler-error-c2692"></a>Chyba kompilátoru C2692

' function_name ': v kompilátoru jazyka C s možností/CLR jsou vyžadovány plně prototypované funkce

Při kompilaci pro spravovaný kód .NET vyžaduje kompilátor jazyka C deklarace funkce ANSI. Kromě toho, pokud funkce přebírá žádné parametry, musí explicitně deklarovat `void` jako typ parametru.
