---
title: Vyhodnocování výrazu CXX0015 chyba | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0015
dev_langs:
- C++
helpviewer_keywords:
- CXX0015
- CAN0015
ms.assetid: 35efaf77-d578-48d8-bfc5-fdeb2a46a8b5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1aa37a2cc7208063ce4cfa786de196842ab42b45
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46050813"
---
# <a name="expression-evaluator-error-cxx0015"></a>Chyba při vyhodnocování výrazu CXX0015

výraz je příliš složitý (přetečení zásobníku)

Výraz zadaný byla příliš složité nebo jsou vnořené moc hluboko množství úložiště k dispozici pro vyhodnocování výrazů C.

Přetečení obvykle dochází z důvodu příliš mnoha čekající výpočtů.

Změna uspořádání výraz tak, aby jednotlivé komponenty výraz lze vyhodnotit, jako je došlo k, namísto nutnosti čekání na ostatní části výraz, který má být vypočtena.

Výraz rozdělte do více příkazů.

Tato chyba se shoduje s CAN0015.