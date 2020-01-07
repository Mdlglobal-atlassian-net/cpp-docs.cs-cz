---
title: Méně závažná chyba nástroje ML A2008
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A2008
helpviewer_keywords:
- A2008
ms.assetid: ca24157f-c88a-4678-ae06-3bc3cd956001
ms.openlocfilehash: 79448f9358ffd422b8b25a69ac2b83693e58560e
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318043"
---
# <a name="ml-nonfatal-error-a2008"></a>Méně závažná chyba nástroje ML A2008

**Chyba syntaxe:**

Token v aktuálním umístění způsobil chybu syntaxe.

Mohlo dojít k jedné z následujících akcí:

- Do direktivy byla přidána předpona tečky nebo byla vynechána.

- Rezervované slovo (například **C** nebo **Size**) bylo použito jako identifikátor.

- Použila se instrukce, která nebyla k dispozici s aktuálním procesorem nebo výběrem koprocesoru.

- Operátor běhu porovnání (například `==`) byl použit v podmíněném příkazu sestavení namísto relačního operátoru (například [EQ](operator-eq.md)).

- Instrukci nebo direktivě bylo předány příliš málo operandů.

- Byla použita zastaralá direktiva.

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](ml-error-messages.md)
