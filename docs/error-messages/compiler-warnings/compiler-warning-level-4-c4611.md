---
title: Kompilátor upozornění (úroveň 4) C4611
ms.date: 11/04/2016
f1_keywords:
- C4611
helpviewer_keywords:
- C4611
ms.assetid: bd90d0a6-75f9-4e97-968d-dda6773e9fd8
ms.openlocfilehash: b799c568d73a081a4d4cf5616f376f3efc9eeffb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62349669"
---
# <a name="compiler-warning-level-4-c4611"></a>Kompilátor upozornění (úroveň 4) C4611

interakce mezi 'function' a destrukcí objektu C++ není typu portable.

Na některých platformách, funkce, které zahrnují **catch** nemusí podporovat sémantiku objektu C++ odstranění, když jsou mimo rozsah.

Abyste zabránili neočekávanému chování, vyhněte se použití **catch** ve funkcích, které mají konstruktory a destruktory.

Se objeví toto upozornění jen jednou; Zobrazit [– Direktiva pragma upozornění](../../preprocessor/warning.md).