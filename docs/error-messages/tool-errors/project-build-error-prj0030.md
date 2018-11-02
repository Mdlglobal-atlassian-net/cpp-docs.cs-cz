---
title: Chyba sestavení projektu PRJ0030
ms.date: 11/04/2016
f1_keywords:
- PRJ0030
helpviewer_keywords:
- PRJ0030
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
ms.openlocfilehash: 2a6cde4ca48acb9aadfe3109084483dbb554e1e4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50488072"
---
# <a name="project-build-error-prj0030"></a>Chyba sestavení projektu PRJ0030

Rozšiřování makra došlo k chybě. Vyhodnocení překročil rekurze 32 úrovní pro $(makra).

Tato chyba je způsobena rekurzi v makrech. Pokud nastavíte například **zprostředkující adresář** vlastnosti (naleznete v tématu [Obecná stránka vlastností (projekt)](../../ide/general-property-page-project.md)) $ (IntDir), budete mít rekurze.

Chcete-li vyřešit tuto chybu, nemá definován makra nebo vlastnosti z hlediska makra, které se používají k definování.