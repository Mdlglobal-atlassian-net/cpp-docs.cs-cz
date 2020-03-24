---
title: Závažná chyba nástroje NMAKE U1100
ms.date: 11/04/2016
f1_keywords:
- U1100
helpviewer_keywords:
- U1100
ms.assetid: c71910a7-c581-4d9c-a38c-d2d557d56289
ms.openlocfilehash: d5c62c1465bbb6463afbac2bc9ad5f4290473471
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193261"
---
# <a name="nmake-fatal-error-u1100"></a>Závažná chyba nástroje NMAKE U1100

makro ' název_makra ' je v kontextu pravidla dávky ' Rule ' neplatné.

NMAKE vygeneruje tuto chybu, pokud blok příkazu pravidla dávkového režimu přímo nebo nepřímo odkazuje na speciální makro souboru, které není $ <.

$ < je jediné povolené makro pro pravidla dávkového režimu.
