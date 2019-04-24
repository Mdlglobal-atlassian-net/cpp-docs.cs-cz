---
title: Méně závažná chyba nástroje ML A2008
ms.date: 08/30/2018
ms.topic: error-reference
f1_keywords:
- A2008
helpviewer_keywords:
- A2008
ms.assetid: ca24157f-c88a-4678-ae06-3bc3cd956001
ms.openlocfilehash: 7f85a3aabb7b1955cede912168dfc04618b8f2b2
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62201976"
---
# <a name="ml-nonfatal-error-a2008"></a>Méně závažná chyba nástroje ML A2008

**Chyba syntaxe:**

Token na aktuální pozici způsobila chybu syntaxe.

Jednu z následujících mohlo dojít:

- Předponu tečkou byl přidán do nebo na direktivu vynechat.

- Vyhrazené slovo (například **C** nebo **velikost**) byl použit jako identifikátor.

- Instrukce, která nebyla k dispozici pomocí aktuálního výběru procesoru nebo koprocesoru použil.

- Operátor porovnání za běhu (například `==`) byla použita ve výrazu podmíněné sestavení namísto relační operátor (například [EQ](../../assembler/masm/operator-eq.md)).

- Instrukci nebo direktivě byl zadán nedostatečný počet operandů.

- Zastaralá direktiva byl použit.

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](../../assembler/masm/ml-error-messages.md)<br/>