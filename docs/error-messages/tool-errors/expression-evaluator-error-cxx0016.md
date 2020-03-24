---
title: Chyba při vyhodnocování výrazu CXX0016
ms.date: 11/04/2016
f1_keywords:
- CXX0016
helpviewer_keywords:
- CAN0016
- CXX0016
ms.assetid: af94a2ae-e835-4da6-8d2f-5c879f72eda2
ms.openlocfilehash: 9f280eeb6d59eb2f81d6d27225441f807664ce27
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80196024"
---
# <a name="expression-evaluator-error-cxx0016"></a>Chyba při vyhodnocování výrazu CXX0016

Konstanta je moc velká.

Vyhodnocovací filtr výrazů jazyka C nemůže přijmout unsigned integer konstantu větší než 4 294 967 295 (0FFFFFFFF hexadecimální) nebo konstanty s plovoucí desetinnou čárkou, jejíž velikost je větší než přibližně 1.8 E + 308.

Tato chyba je shodná s CAN0016.
