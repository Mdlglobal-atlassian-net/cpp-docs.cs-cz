---
title: Chyba při vyhodnocování výrazu CXX0030
ms.date: 11/04/2016
f1_keywords:
- CXX0030
helpviewer_keywords:
- CAN0030
- CXX0030
ms.assetid: ada8b48c-09c8-49bf-ae23-313ed663c4fe
ms.openlocfilehash: 477ec31d18924e91baf2d8b7b732bc7a50eee53b
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195614"
---
# <a name="expression-evaluator-error-cxx0030"></a>Chyba při vyhodnocování výrazu CXX0030

výraz není evaluatable

Vyhodnocovacímu filtru výrazů pro ladicí program se nepovedlo získat hodnotu pro výraz jako zapsaný. Jedním z pravděpodobných příčin je, že výraz odkazuje na paměť, která je mimo adresní prostor programu (v jednom příkladu je odkazováno na ukazatel s hodnotou null). Systém Windows nepovoluje přístup k paměti, která je mimo adresní prostor programu.

Můžete chtít přepsat výraz pomocí závorek pro řízení pořadí vyhodnocení.

Tato chyba je shodná s CAN0030.
