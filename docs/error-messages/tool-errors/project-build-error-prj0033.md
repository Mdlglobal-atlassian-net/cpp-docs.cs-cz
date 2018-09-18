---
title: Chyba sestavení projektu PRJ0033 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0033
dev_langs:
- C++
helpviewer_keywords:
- PRJ0033
ms.assetid: 84d4a052-0586-4b78-9315-81c1e8386c1e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c70bd942123c48866c3353443b478de4953668de
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036069"
---
# <a name="project-build-error-prj0033"></a>Chyba sestavení projektu PRJ0033

Vlastnost "Additional Dependencies" vlastního sestavení krok pro soubor 'file' obsažená "makro" která je vyhodnocena na "macro_expansion".

Vlastní krok sestavení na souboru obsahovala chybu v jeho další závislosti, pravděpodobně z důvodu problému vyhodnocení makra. Tato chyba může také znamenat, že cesta je chybně vytvořený kód, obsahující znaky nebo kombinace znaků, které jsou neplatné v cestě k souboru.

Chcete-li tuto chybu vyřešit, opravte makro nebo odstraňte specifikaci cesty. Vyhodnocená cesta je absolutní cesta z adresáře projektu.