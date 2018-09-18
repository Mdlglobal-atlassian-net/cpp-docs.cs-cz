---
title: Upozornění nástroje BSCMAKE BK4504 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK4504
dev_langs:
- C++
helpviewer_keywords:
- BK4504
ms.assetid: b56ee2d4-ad44-40f4-98c0-75934ea44a6c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c8a2da8903dade37faf3b14175b65f3169efd908
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049762"
---
# <a name="bscmake-warning-bk4504"></a>Upozornění nástroje BSCMAKE BK4504

soubor obsahuje příliš mnoho odkazů; Další odkazy z tohoto zdroje se ignoruje

Soubor .cpp obsahuje víc než 64 000 odkazy na symboly. Když BSCMAKE došlo k 64 000 odkazy v souboru, ignoruje všechny odkazy na další.

Chcete-li tento problém, buď rozdělení souboru na dva nebo více souborů, z nichž každá má méně než 64 000 odkazy na symbol, použijte `#pragma component(browser)` direktivy preprocesoru na limit symboly, které jsou generovány pro konkrétní odkazy. Další informace najdete v tématu [komponenty](../../preprocessor/component.md).