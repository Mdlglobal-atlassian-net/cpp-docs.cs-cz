---
title: Chyba při vyhodnocování výrazu CXX0017
ms.date: 11/04/2016
f1_keywords:
- CXX0017
helpviewer_keywords:
- CAN0017
- CXX0017
ms.assetid: af74db02-a64d-49ca-8363-3e044a107580
ms.openlocfilehash: 64ebce0161d67c298d55095f6bc409820120c34a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196011"
---
# <a name="expression-evaluator-error-cxx0017"></a>Chyba při vyhodnocování výrazu CXX0017

symbol se nenašel.

Symbol zadaný ve výrazu se nepovedlo najít.

Jednou z možných příčin této chyby je neshoda velkých a malých písmen v názvu symbolu. Vzhledem k tomu C++ , že jazyk C a jsou jazyky s rozlišováním velkých a malých písmen, musí být název symbolu uveden v přesném případě, v němž je definován ve zdroji.

K této chybě může dojít při pokusu o přetypovat proměnné za účelem sledování proměnné během ladění. `typedef` deklaruje nový název typu, ale nedefinuje nový typ. Přetypovat pokus v ladicím programu vyžaduje název definovaného typu.

Tato chyba je shodná s CAN0017.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Oprava pomocí následujících možných řešení

1. Ujistěte se, že symbol je již deklarován v bodě v programu, kde je používán.

1. Použijte skutečný název typu pro přetypování proměnných v ladicím programu místo názvu `typedef`definovaného.
