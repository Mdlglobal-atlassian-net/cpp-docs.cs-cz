---
title: Závažná chyba C1091
ms.date: 11/04/2016
f1_keywords:
- C1091
helpviewer_keywords:
- C1091
ms.assetid: 812d4201-9154-48b0-b9af-5959c082ca33
ms.openlocfilehash: 9758d4b779f4727012041da60632bcea8ce18d42
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208530"
---
# <a name="fatal-error-c1091"></a>Závažná chyba C1091

limit kompilátoru: řetězec přesahuje délku bajtů 'délka.

Řetězcová konstanta překročil aktuální limit délky řetězce.

Můžete chtít statický řetězec rozdělit do dvou (nebo více) proměnné a používat [strcpy_s](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) k připojení výsledku jako součást deklarace nebo za běhu.