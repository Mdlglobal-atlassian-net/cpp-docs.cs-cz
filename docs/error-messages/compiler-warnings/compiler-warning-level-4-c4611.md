---
title: Upozornění kompilátoru (úroveň 4) C4611
ms.date: 11/04/2016
f1_keywords:
- C4611
helpviewer_keywords:
- C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
ms.openlocfilehash: 7de4cdf0eacb1b9848a4350f1d223da1fd47d1fc
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80198299"
---
# <a name="compiler-warning-level-4-c4611"></a>Upozornění kompilátoru (úroveň 4) C4611

interakce mezi funkcí a C++ zničením objektu není typu Portable.

Na některých platformách, funkce, které zahrnují **catch** , C++ nemusí podporovat sémantiku objektu zničení, pokud je mimo rozsah.

Aby nedocházelo k neočekávanému chování, vyhněte se použití **catch** ve funkcích, které mají konstruktory a destruktory.

Toto upozornění se vydá jenom jednou. viz [pragma warning](../../preprocessor/warning.md).
