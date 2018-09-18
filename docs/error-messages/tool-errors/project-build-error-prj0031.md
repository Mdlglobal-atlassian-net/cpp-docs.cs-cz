---
title: Chyba sestavení projektu PRJ0031 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0031
dev_langs:
- C++
helpviewer_keywords:
- PRJ0031
ms.assetid: b42435c6-e570-4f8e-9ad5-12a7ea69ccb2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce97e8f540295f5a2968fce22312b8e0e34cfd2a
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46076889"
---
# <a name="project-build-error-prj0031"></a>Chyba sestavení projektu PRJ0031

Vlastnost "Výstupy" použité při vlastním sestavování krok pro soubor 'file' obsažená "makro" která je vyhodnocena na "macro_expansion".

Vlastní krok sestavení na souboru má chybný výstup pravděpodobně z důvodu problému vyhodnocení makra. Tato chyba může také znamenat, že cesta je chybně vytvořený kód, obsahující znaky nebo kombinace znaků, které jsou neplatné v cestě k souboru.

Chcete-li tuto chybu vyřešit, opravte makro nebo odstraňte specifikaci cesty. Vyhodnocená cesta je absolutní cesta z adresáře projektu.