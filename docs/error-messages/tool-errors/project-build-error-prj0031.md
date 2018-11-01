---
title: Chyba sestavení projektu PRJ0031
ms.date: 11/04/2016
f1_keywords:
- PRJ0031
helpviewer_keywords:
- PRJ0031
ms.assetid: b42435c6-e570-4f8e-9ad5-12a7ea69ccb2
ms.openlocfilehash: e5edae0c1b7464e4a3a5e9523332ce956d0dcf92
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648588"
---
# <a name="project-build-error-prj0031"></a>Chyba sestavení projektu PRJ0031

Vlastnost "Výstupy" použité při vlastním sestavování krok pro soubor 'file' obsažená "makro" která je vyhodnocena na "macro_expansion".

Vlastní krok sestavení na souboru má chybný výstup pravděpodobně z důvodu problému vyhodnocení makra. Tato chyba může také znamenat, že cesta je chybně vytvořený kód, obsahující znaky nebo kombinace znaků, které jsou neplatné v cestě k souboru.

Chcete-li tuto chybu vyřešit, opravte makro nebo odstraňte specifikaci cesty. Vyhodnocená cesta je absolutní cesta z adresáře projektu.