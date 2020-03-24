---
title: Chyba při vyhodnocování výrazu CXX0039
ms.date: 11/04/2016
f1_keywords:
- CXX0039
helpviewer_keywords:
- CXX0039
- CAN0039
ms.assetid: 8bf698d2-e015-4595-944f-72b81aa43d22
ms.openlocfilehash: 5706d002eb3d566d05b059cb04b6b1626fdb3d33
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80185123"
---
# <a name="expression-evaluator-error-cxx0039"></a>Chyba při vyhodnocování výrazu CXX0039

symbol je dvojznačný.

Vyhodnocovací filtr výrazů jazyka C nemůže určit, která instance symbolu použít ve výrazu. Symbol se vyskytuje ve stromu dědičnosti více než jednou.

K explicitnímu určení instance, která se má použít ve výrazu, je nutné použít operátor rozlišení oboru (`::`).

Tato chyba je shodná s CAN0039.
