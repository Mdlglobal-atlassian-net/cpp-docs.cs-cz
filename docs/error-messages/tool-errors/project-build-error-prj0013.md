---
title: Chyba sestavení projektu PRJ0013
ms.date: 11/04/2016
f1_keywords:
- PRJ0013
helpviewer_keywords:
- PRJ0013
ms.assetid: 95e7bafd-63c8-4b2d-b778-f19cdf9ba36c
ms.openlocfilehash: c78f029a3fb0e89913ce9b5ce221569e67d8faf6
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69509926"
---
# <a name="project-build-error-prj0013"></a>Chyba sestavení projektu PRJ0013

Systémový prostředek může být kriticky nízký. Nelze vytvořit kanál potřebný ke spuštění sestavení.

Tato chyba znamená, že systémové prostředky jsou nízké. Chcete-li tuto chybu vyřešit, snižte využití systémových prostředků jinými procesy nebo aplikacemi.

K této chybě může dojít také v případě, že úroveň zabezpečení nestačí vytvořit kanály (viz [CreatePipe](/windows/win32/api/namedpipeapi/nf-namedpipeapi-createpipe)).