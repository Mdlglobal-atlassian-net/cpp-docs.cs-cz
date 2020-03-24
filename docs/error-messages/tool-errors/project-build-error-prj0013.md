---
title: Chyba sestavení projektu PRJ0013
ms.date: 11/04/2016
f1_keywords:
- PRJ0013
helpviewer_keywords:
- PRJ0013
ms.assetid: 95e7bafd-63c8-4b2d-b778-f19cdf9ba36c
ms.openlocfilehash: d769899faa940f2754db4d2428a4d7c416b49fa4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80192728"
---
# <a name="project-build-error-prj0013"></a>Chyba sestavení projektu PRJ0013

Systémový prostředek může být kriticky nízký. Nelze vytvořit kanál potřebný ke spuštění sestavení.

Tato chyba znamená, že systémové prostředky jsou nízké. Chcete-li tuto chybu vyřešit, snižte využití systémových prostředků jinými procesy nebo aplikacemi.

K této chybě může dojít také v případě, že úroveň zabezpečení nestačí vytvořit kanály (viz [CreatePipe](/windows/win32/api/namedpipeapi/nf-namedpipeapi-createpipe)).
