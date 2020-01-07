---
title: Závažná chyba nástroje ML A1007
ms.date: 12/17/2019
ms.custom: error-reference
f1_keywords:
- A1007
helpviewer_keywords:
- A1007
ms.assetid: bcf9c826-beb3-4e93-91fe-1ffd34995fbf
ms.openlocfilehash: c9527769e0d9397de90f49cbce98b2cca42bed50
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317120"
---
# <a name="ml-fatal-error-a1007"></a>Závažná chyba nástroje ML A1007

**příliš hluboká úroveň vnořování**

Assembler dosáhl svého limitu vnořování. Limit je 20 úrovní s výjimkou případů, kdy je uvedeno jinak.

Jedna z následujících možností byla vnořena příliš hluboko:

- Direktiva vysoké úrovně, například [. Pokud](dot-if.md), [. Opakujte akci](dot-repeat.md), nebo [. WHILe](dot-while.md).

- Definice struktury.

- Direktiva podmíněného sestavení.

- Definice procedury.

- Direktiva [PUSHCONTEXT](pushcontext.md) (limit je 10).

- Definice segmentu.

- Soubor zahrnutí.

- Makro.

## <a name="see-also"></a>Viz také:

[Chybové zprávy ML](ml-error-messages.md)
