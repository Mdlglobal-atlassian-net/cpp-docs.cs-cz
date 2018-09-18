---
title: Chyba sestavení projektu PRJ0030 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- PRJ0030
dev_langs:
- C++
helpviewer_keywords:
- PRJ0030
ms.assetid: c48b3727-e166-46e7-bcd7-3e5b2ac5c1d4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 964fedd40f577a8b337c4ad0c20ba80d33ed2a23
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46099899"
---
# <a name="project-build-error-prj0030"></a>Chyba sestavení projektu PRJ0030

Rozšiřování makra došlo k chybě. Vyhodnocení překročil rekurze 32 úrovní pro $(makra).

Tato chyba je způsobena rekurzi v makrech. Pokud nastavíte například **zprostředkující adresář** vlastnosti (naleznete v tématu [Obecná stránka vlastností (projekt)](../../ide/general-property-page-project.md)) $ (IntDir), budete mít rekurze.

Chcete-li vyřešit tuto chybu, nemá definován makra nebo vlastnosti z hlediska makra, které se používají k definování.