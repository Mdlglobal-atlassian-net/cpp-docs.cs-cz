---
title: Závažná chyba C1209
ms.date: 11/04/2016
f1_keywords:
- C1209
helpviewer_keywords:
- C1209
ms.assetid: aa9ee10f-abe3-4683-9792-adca4cbbabb5
ms.openlocfilehash: 0948debc2573ace269419641ca8facd495792341
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80203434"
---
# <a name="fatal-error-c1209"></a>Závažná chyba C1209

Sestavení Friend nejsou podporovaná nainstalovanou verzí modulu runtime.

K C1208 dojde, když máte kompilátor pro aktuální vydání, ale modul CLR (Common Language Runtime) z předchozí verze.

Některé funkce kompilátoru nemusí fungovat v předchozí verzi doby běhu.

Chcete-li vyřešit C1209, nainstalujte modul CLR (Common Language Runtime), který byl dodán s vámi použitým kompilátorem.

Další informace naleznete v tématu [Friend Assemblies (C++)](../../dotnet/friend-assemblies-cpp.md).
