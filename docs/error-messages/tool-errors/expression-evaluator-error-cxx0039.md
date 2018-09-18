---
title: Vyhodnocování výrazu CXX0039 chyba | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- CXX0039
dev_langs:
- C++
helpviewer_keywords:
- CXX0039
- CAN0039
ms.assetid: 8bf698d2-e015-4595-944f-72b81aa43d22
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b5397426618c5dfcbaa6307105781ff2e6f2eb97
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048328"
---
# <a name="expression-evaluator-error-cxx0039"></a>Chyba při vyhodnocování výrazu CXX0039

nejednoznačný symbol

Vyhodnocovací filtr výrazů C nemůže určit, která instance symbol, který chcete použít ve výrazu. Symbol vyskytuje více než jednou ve stromu dědičnosti.

Je nutné použít operátor rozlišení oboru (`::`) s ohledem na instance, kterou chcete použít ve výrazu.

Tato chyba se shoduje s CAN0039.