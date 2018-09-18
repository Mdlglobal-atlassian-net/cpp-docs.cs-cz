---
title: Závažná chyba C1026 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1026
dev_langs:
- C++
helpviewer_keywords:
- C1026
ms.assetid: 89bb9d40-673a-44aa-a9f4-b42c07b49d44
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: db9167383df48dad274ef8941defaa53f51d3bfa
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46068985"
---
# <a name="fatal-error-c1026"></a>Závažná chyba C1026

přetečení zásobníku analyzátoru. program je moc složitý

Místo vyžadovaný pro analýzu program způsobila přetečení zásobníku kompilátoru.

Zjednodušte výrazů podle:

- Snížení úrovně vnoření v `for` a `switch` příkazy. Umístěte hlouběji vnořené příkazy do samostatné funkce.

- Rozdělení dlouhé výrazy zahrnující operátory čárkou nebo volání funkce.