---
title: Závažná chyba nástroje NMAKE U1100
ms.date: 11/04/2016
f1_keywords:
- U1100
helpviewer_keywords:
- U1100
ms.assetid: c71910a7-c581-4d9c-a38c-d2d557d56289
ms.openlocfilehash: a1474acab4ca4929fb4db4b7b78d7a96637a0745
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50666593"
---
# <a name="nmake-fatal-error-u1100"></a>Závažná chyba nástroje NMAKE U1100

makra "makro" je neplatný v kontextu pravidla dávky "pravidlo.

NMAKE vygeneruje tuto chybu, pokud blok příkazu pravidla dávkového režimu přímo nebo nepřímo odkazuje makro zvláštní soubor, který není $<.

$< je jediným povoleným názvem makra pro pravidla dávkového režimu.