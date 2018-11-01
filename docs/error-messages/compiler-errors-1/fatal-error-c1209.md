---
title: Závažná chyba C1209
ms.date: 11/04/2016
f1_keywords:
- C1209
helpviewer_keywords:
- C1209
ms.assetid: aa9ee10f-abe3-4683-9792-adca4cbbabb5
ms.openlocfilehash: 8b23ae3459178937c6af7ccb5c8ee882dd508c93
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50508067"
---
# <a name="fatal-error-c1209"></a>Závažná chyba C1209

Sestavení Friend nejsou podporovaná ve verzi modulu runtime nainstalovaný

C1208 nastane, pokud máte pro aktuální verzi, ale společného jazykového modulu runtime z předchozí verze kompilátoru.

Některé funkce kompilátoru nemusí fungovat v době běhu předchozí verze.

Pokud chcete vyřešit C1209, nainstalujte modul common language runtime, dodávané s kompilátorem, který používáte.

Další informace najdete v tématu [přátelská sestavení (C++)](../../dotnet/friend-assemblies-cpp.md).