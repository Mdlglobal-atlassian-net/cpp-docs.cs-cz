---
title: Chyba linkerů LNK1241
ms.date: 11/04/2016
f1_keywords:
- LNK1241
helpviewer_keywords:
- LNK1241
ms.assetid: 7b8b52eb-0231-4521-b52a-2bce8d3e8956
ms.openlocfilehash: 87f73680d7ed40b9b2db9f40f9140976d552ab6b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584545"
---
# <a name="linker-tools-error-lnk1241"></a>Chyba linkerů LNK1241

soubor prostředků zdroj souboru, který již zadán

Tato chyba je generována při spuštění **cvtres** ručně z příkazového řádku a pokud se pak předejte výsledný .obj souborů v linkeru kromě na jiné soubory .res.

Pokud chcete zadat více souborů res, předat je vše do linkeru jako soubory res, není v rámci soubory .obj vytvořil **cvtres**.