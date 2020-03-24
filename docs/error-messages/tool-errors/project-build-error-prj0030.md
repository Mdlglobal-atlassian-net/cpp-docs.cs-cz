---
title: Chyba sestavení projektu PRJ0030
ms.date: 11/04/2016
f1_keywords:
- PRJ0030
helpviewer_keywords:
- PRJ0030
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
ms.openlocfilehash: 3675c3796ae37df848e458aa2db665d8c4aa7766
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192507"
---
# <a name="project-build-error-prj0030"></a>Chyba sestavení projektu PRJ0030

Chyba rozšíření makra Vyhodnocení rekurze překročilo 32 úrovní pro $ (makro).

Tato chyba je způsobena rekurzem v makrech. Například pokud nastavíte vlastnost **zprostředkujícího adresáře** (viz [Obecná stránka vlastností (projekt)](../../build/reference/general-property-page-project.md)) na $ (IntDir), budete mít rekurzi.

Chcete-li tuto chybu vyřešit, Nedefinujte makra ani vlastnosti v makrech, které jsou použity k definování.
