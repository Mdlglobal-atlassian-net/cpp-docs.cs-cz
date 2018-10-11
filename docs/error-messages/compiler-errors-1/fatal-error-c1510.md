---
title: Závažná chyba C1510 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 04/11/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1510
dev_langs:
- C++
helpviewer_keywords:
- C1510
ms.assetid: 150c827f-9514-41a9-8d7e-82f820749bcb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 69942cd30bfe8c61dcf522ff3d95a90232462efd
ms.sourcegitcommit: 3a141cf07b5411d5f1fdf6cf67c4ce928cf389c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/11/2018
ms.locfileid: "49081952"
---
# <a name="fatal-error-c1510"></a>Závažná chyba C1510

Nejde otevřít jazykový prostředek clui.dll.

Kompilátor nemůže načíst knihovna DLL prostředků jazyka.

Existují dvě běžné příčiny tohoto problému. Při použití 32bitové verze kompilátoru a nástrojů, může se zobrazit tato chyba pro velké projekty, které používají více než 2GB paměti během odkaz. Možné řešení v 64bitových systémech Windows, je použít 64bitové nativní a křížový kompilátor a nástroje pro generování kódu. Toto využívá větší paměť k dispozici pro 64bitové aplikace. Pokud je nutné použít 32bitový kompilátor, protože běží v 32bitové verzi systému, v některých případech můžete zvýšit množství paměti k dispozici v linkeru na 3GB. Další informace najdete v tématu [4 GB optimalizace: nástroje BCDEdit a Boot.ini](https://msdn.microsoft.com/library/vs/alm/bb613473) a [nástroje BCDEdit/sadě increaseuserva](https://msdn.microsoft.com/library/ff542202.aspx) příkazu.

Obvyklou příčinou je poškozený nebo neúplná instalace sady Visual Studio. V takovém případě opětovným spuštěním instalačního programu opravte nebo přeinstalujte Visual Studio.
