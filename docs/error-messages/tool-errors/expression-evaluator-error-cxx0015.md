---
title: Chyba při vyhodnocování výrazu CXX0015
ms.date: 11/04/2016
f1_keywords:
- CXX0015
helpviewer_keywords:
- CXX0015
- CAN0015
ms.assetid: 35efaf77-d578-48d8-bfc5-fdeb2a46a8b5
ms.openlocfilehash: 19cf47d6b7b718eb19b987bcc16854af3266069b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196063"
---
# <a name="expression-evaluator-error-cxx0015"></a>Chyba při vyhodnocování výrazu CXX0015

výraz je moc složitý (přetečení zásobníku).

Zadaný výraz byl příliš složitý nebo příliš hluboko pro velikost úložiště, která je k dispozici pro vyhodnocení výrazu C.

K přetečení obvykle dochází z důvodu příliš mnoha nedokončených výpočtů.

Přeuspořádejte výraz tak, aby každá komponenta výrazu mohla být vyhodnocena při jeho výskytu, a ne čekat na vypočítané další části výrazu.

Rozdělit výraz na více příkazů

Tato chyba je shodná s CAN0015.
