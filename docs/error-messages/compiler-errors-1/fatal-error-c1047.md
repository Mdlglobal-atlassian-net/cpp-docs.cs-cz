---
title: Závažná chyba C1047 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1047
dev_langs:
- C++
helpviewer_keywords:
- C1047
ms.assetid: e1bbbc6b-a5bc-4c23-8203-488120a0ec78
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1983fa0a18667d98f84dfe5049afd4e872d87d93
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46021587"
---
# <a name="fatal-error-c1047"></a>Závažná chyba C1047

Soubor objektu nebo knihovny 'file' byl vytvořen pomocí staršího kompilátoru než jiné objekty; Sestavte starší objekty a knihovny

C1047 dojde při vytváření souborů objektů nebo knihoven s **parametru/LTCG** jsou spojeny dohromady, ale pokud tyto soubory objektů nebo knihoven sestavují s různými verzemi sady nástrojů Visual C++.

To může nastat, pokud začít používat novou verzi kompilátoru, ale proveďte čisté sestavení z existujících souborů objektů nebo knihoven.

Chcete-li vyřešit C1047, opětovné sestavení všech souborů objektů nebo knihoven.