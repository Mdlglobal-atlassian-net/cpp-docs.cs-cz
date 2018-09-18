---
title: Příznak směru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.flags
dev_langs:
- C++
helpviewer_keywords:
- direction flag
ms.assetid: 0836b4af-dbbb-4ab8-a4b2-156f2e2099e2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7db91b20b76ef06130cbb8357344352b820ed731
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093194"
---
# <a name="direction-flag"></a>Příznak směru

Příznak směru je příznak procesoru specifické pro procesory Intel 80 x 86. Platí pro všechny pokyny k sestavení, které používají předpona REP (opakování), například MOVS, MOVSD, MOVSW a dalších. Adresy, které jsou k dispozici na příslušné pokyny jsou zvýšena, pokud se vymaže příznak směru.

Běhové rutiny jazyka C předpokládá, že se vymaže příznak směru. Pokud používáte jiné funkce s funkcí jazyka C za běhu, musíte zajistit, že jiné funkce ponechat stávající příznak směru samostatně, nebo jej obnovit do původního stavu. Příznak směru, aby se nezapomnělo při vstupu je očekáván díky za běhu kódu rychlejší a efektivnější.

Příznak směru, aby se nezapomnělo očekávat, že funkce knihovny C Run-Time, jako je například rutiny zacházení s řetězci a zacházení s vyrovnávací pamětí.

## <a name="see-also"></a>Viz také

[Funkce knihovny CRT](../c-runtime-library/crt-library-features.md)