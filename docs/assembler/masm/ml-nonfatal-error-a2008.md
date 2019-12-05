---
title: Méně závažná chyba nástroje ML A2008
ms.date: 08/30/2018
ms.custom: error-reference
f1_keywords:
- A2008
helpviewer_keywords:
- A2008
ms.assetid: ca24157f-c88a-4678-ae06-3bc3cd956001
ms.openlocfilehash: 192d82186a58d4e6b534ab5ec65b696d4d7ce3ee
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74856750"
---
# <a name="ml-nonfatal-error-a2008"></a>Méně závažná chyba nástroje ML A2008

**Chyba syntaxe:**

Token v aktuálním umístění způsobil chybu syntaxe.

Mohlo dojít k jedné z následujících akcí:

- Do direktivy byla přidána předpona tečky nebo byla vynechána.

- Rezervované slovo (například **C** nebo **Size**) bylo použito jako identifikátor.

- Použila se instrukce, která nebyla k dispozici s aktuálním procesorem nebo výběrem koprocesoru.

- Operátor běhu porovnání (například `==`) byl použit v podmíněném příkazu sestavení namísto relačního operátoru (například [EQ](../../assembler/masm/operator-eq.md)).

- Instrukci nebo direktivě bylo předány příliš málo operandů.

- Byla použita zastaralá direktiva.

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)<br/>