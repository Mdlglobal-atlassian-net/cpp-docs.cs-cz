---
title: Závažná chyba C1510
ms.date: 04/11/2017
f1_keywords:
- C1510
helpviewer_keywords:
- C1510
ms.assetid: 150c827f-9514-41a9-8d7e-82f820749bcb
ms.openlocfilehash: f05f79ea78958a7d7a64f24bdce2d1151b93cdfb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62208502"
---
# <a name="fatal-error-c1510"></a>Závažná chyba C1510

Nejde otevřít jazykový prostředek clui.dll.

Kompilátor nemůže načíst knihovna DLL prostředků jazyka.

Existují dvě běžné příčiny tohoto problému. Při použití 32bitové verze kompilátoru a nástrojů, může se zobrazit tato chyba pro velké projekty, které používají více než 2GB paměti během odkaz. Možné řešení v 64bitových systémech Windows, je použít 64bitové nativní a křížový kompilátor a nástroje pro generování kódu. Toto využívá větší paměť k dispozici pro 64bitové aplikace. Pokud je nutné použít 32bitový kompilátor, protože běží v 32bitové verzi systému, v některých případech můžete zvýšit množství paměti k dispozici v linkeru na 3GB. Další informace najdete v tématu [optimalizace 4 GB: Nástroje BCDEdit a Boot.ini](https://msdn.microsoft.com/library/vs/alm/bb613473) a [nástroje BCDEdit/sadě increaseuserva](https://msdn.microsoft.com/library/ff542202.aspx) příkazu.

Obvyklou příčinou je poškozený nebo neúplná instalace sady Visual Studio. V takovém případě opětovným spuštěním instalačního programu opravte nebo přeinstalujte Visual Studio.
