---
title: Závažná chyba C1210
ms.date: 11/04/2016
f1_keywords:
- C1210
helpviewer_keywords:
- C1210
ms.assetid: e2208309-c284-425c-a7e8-48e96e66f35b
ms.openlocfilehash: a90ca3e3b55642f1a6cd847997b83e4b7db46818
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50591801"
---
# <a name="fatal-error-c1210"></a>Závažná chyba C1210

> / CLR: pure a/CLR: safe nejsou podporované ve verzi modulu runtime nainstalovaný

**/CLR: pure** a **/CLR: safe** – možnosti kompilátoru jsou zastaralé v sadě Visual Studio 2015 a není podporována v sadě Visual Studio 2017.

C1210 nastane, pokud máte pro aktuální verzi, ale společného jazykového modulu runtime z předchozí verze kompilátoru.

Některé funkce kompilátoru nemusí fungovat v době běhu předchozí verze.

Chcete-li vyřešit C1210 nainstalovat verze společného běhového jazykového, která je určena pro použití s kompilátoru.