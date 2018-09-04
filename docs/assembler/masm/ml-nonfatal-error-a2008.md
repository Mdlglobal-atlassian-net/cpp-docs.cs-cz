---
title: Závažná méně závažná chyba nástroje ML A2008 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: error-reference
f1_keywords:
- A2008
dev_langs:
- C++
helpviewer_keywords:
- A2008
ms.assetid: ca24157f-c88a-4678-ae06-3bc3cd956001
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 774cf4c2a51bf084fb63e572cc99b0c8e3cba26f
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43679372"
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