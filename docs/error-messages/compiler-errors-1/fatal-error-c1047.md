---
title: Závažná chyba C1047
ms.date: 11/04/2016
f1_keywords:
- C1047
helpviewer_keywords:
- C1047
ms.assetid: e1bbbc6b-a5bc-4c23-8203-488120a0ec78
ms.openlocfilehash: 053c4d828b3583d0e16ab8f4fe03a4b0bbed96f9
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62243748"
---
# <a name="fatal-error-c1047"></a>Závažná chyba C1047

Soubor objektu nebo knihovny 'file' byl vytvořen pomocí staršího kompilátoru než jiné objekty; Sestavte starší objekty a knihovny

C1047 dojde při vytváření souborů objektů nebo knihoven s **parametru/LTCG** jsou spojeny dohromady, ale pokud tyto soubory objektů nebo knihoven sestavují s různými verzemi sady nástrojů Visual C++.

To může nastat, pokud začít používat novou verzi kompilátoru, ale proveďte čisté sestavení z existujících souborů objektů nebo knihoven.

Chcete-li vyřešit C1047, opětovné sestavení všech souborů objektů nebo knihoven.