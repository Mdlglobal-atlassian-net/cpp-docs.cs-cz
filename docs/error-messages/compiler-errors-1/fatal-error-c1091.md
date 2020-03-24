---
title: Závažná chyba C1091
ms.date: 11/04/2016
f1_keywords:
- C1091
helpviewer_keywords:
- C1091
ms.assetid: 812d4201-9154-48b0-b9af-5959c082ca33
ms.openlocfilehash: 76492be7abab6deb740f1670b85274b8c296c783
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203889"
---
# <a name="fatal-error-c1091"></a>Závažná chyba C1091

limit kompilátoru: řetězec přesahuje délku bajtů.

Řetězcová konstanta překročila aktuální limit délky řetězců.

Můžete chtít rozdělit statický řetězec na dvě (nebo více) proměnné a použít [strcpy_s](../../c-runtime-library/reference/strcpy-s-wcscpy-s-mbscpy-s.md) pro připojení výsledku jako součást deklarace nebo za běhu.
