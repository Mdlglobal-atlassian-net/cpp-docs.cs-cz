---
title: Upozornění kompilátoru (úroveň 1) C4952
ms.date: 08/27/2018
f1_keywords:
- C4952
helpviewer_keywords:
- C4952
ms.assetid: 593324f0-5cfe-42fb-b221-2f71308765dd
ms.openlocfilehash: 560705edeb0bbdd6be760736a8d4a19d914133d2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80174567"
---
# <a name="compiler-warning-level-1-c4952"></a>Upozornění kompilátoru (úroveň 1) C4952

> '*Function*': v databázi programu '*pgd_file*' nebyla nalezena žádná data profilu

Při použití [/LTCG: PGUPDATE](../../build/reference/ltcg-link-time-code-generation.md)Kompilátor zjistil vstupní modul, který byl znovu zkompilován po `/LTCG:PGINSTRUMENT` a má k dispozici novou funkci (*Function*).

Toto upozornění je informativní. Chcete-li vyřešit toto upozornění, spusťte `/LTCG:PGINSTRUMENT`, znovu proveďte všechny testovací běhy a spusťte `/LTCG:PGOPTIMIZE`.

Toto upozornění by bylo nahrazeno chybou, pokud byla `/LTCG:PGOPTIMIZE` použita.
