---
title: Závažná méně závažná chyba nástroje ML A2119 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2119
dev_langs:
- C++
helpviewer_keywords:
- A2119
ms.assetid: 4d4ee6da-3a58-495c-a1da-c3a405c4c18d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c1034c91f6eebd240c746c881284bed2baf5e618
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43686896"
---
# <a name="ml-nonfatal-error-a2119"></a>Méně závažná chyba nástroje ML A2119

**musí být zadán typ jazyka**

Definice procedury nebo prototypu Listener was not given typ jazyka.

Typ jazyka musí být deklarována v definici procedury nebo prototypu, pokud není zadán typ výchozího jazyka. Výchozí typ jazyka se nastavuje pomocí buď [. MODEL](../../assembler/masm/dot-model.md) směrnice, **možnost LANG**, nebo parametrů příkazového řádku ML **/GC –** nebo **/Gd**.

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)<br/>