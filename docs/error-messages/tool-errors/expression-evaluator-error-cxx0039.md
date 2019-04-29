---
title: Chyba při vyhodnocování výrazu CXX0039
ms.date: 11/04/2016
f1_keywords:
- CXX0039
helpviewer_keywords:
- CXX0039
- CAN0039
ms.assetid: 8bf698d2-e015-4595-944f-72b81aa43d22
ms.openlocfilehash: 053e57a21f0cb75cbd96732edb6812b3557bcd50
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62396974"
---
# <a name="expression-evaluator-error-cxx0039"></a>Chyba při vyhodnocování výrazu CXX0039

nejednoznačný symbol

Vyhodnocovací filtr výrazů C nemůže určit, která instance symbol, který chcete použít ve výrazu. Symbol vyskytuje více než jednou ve stromu dědičnosti.

Je nutné použít operátor rozlišení oboru (`::`) s ohledem na instance, kterou chcete použít ve výrazu.

Tato chyba se shoduje s CAN0039.