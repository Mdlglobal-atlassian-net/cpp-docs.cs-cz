---
title: Chyba sestavení projektu PRJ0030
ms.date: 11/04/2016
f1_keywords:
- PRJ0030
helpviewer_keywords:
- PRJ0030
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
ms.openlocfilehash: aa1c8539247287f7644742857c3cb7de321a20a2
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811473"
---
# <a name="project-build-error-prj0030"></a>Chyba sestavení projektu PRJ0030

Rozšiřování makra došlo k chybě. Vyhodnocení překročil rekurze 32 úrovní pro $(makra).

Tato chyba je způsobena rekurzi v makrech. Pokud nastavíte například **zprostředkující adresář** vlastnosti (naleznete v tématu [Obecná stránka vlastností (projekt)](../../build/reference/general-property-page-project.md)) $ (IntDir), budete mít rekurze.

Chcete-li vyřešit tuto chybu, nemá definován makra nebo vlastnosti z hlediska makra, které se používají k definování.