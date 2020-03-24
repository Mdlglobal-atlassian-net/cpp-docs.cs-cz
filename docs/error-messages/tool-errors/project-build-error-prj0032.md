---
title: Chyba sestavení projektu PRJ0032
ms.date: 11/04/2016
f1_keywords:
- PRJ0032
helpviewer_keywords:
- PRJ0032
ms.assetid: bc6acbea-4041-4237-8b5a-f0434705d89f
ms.openlocfilehash: 62efa0e72c6fbe4bd38983ff0507923392427c04
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192481"
---
# <a name="project-build-error-prj0032"></a>Chyba sestavení projektu PRJ0032

Vlastnost Outputs vlastního kroku sestavení na úrovni projektu obsahovala ' Macro ', která je vyhodnocena na hodnotu ' macro_expansion '.

Vlastní krok sestavení v projektu má pravděpodobně špatný výstup z důvodu problému s vyhodnocením makra. Tato chyba by mohla také znamenat, že cesta je chybně vytvořená, obsahuje znaky nebo kombinace znaků, které jsou v cestě k souboru neplatné.

Chcete-li tuto chybu vyřešit, opravte makro nebo opravte specifikaci cesty. Vyhodnocená cesta je absolutní cesta z adresáře projektu.
