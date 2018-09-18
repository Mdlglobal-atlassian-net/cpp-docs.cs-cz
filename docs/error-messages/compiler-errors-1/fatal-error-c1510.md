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
ms.openlocfilehash: 4d1da6a21e5156ef0b78c42215de5c4ae7e807db
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049693"
---
# <a name="fatal-error-c1510"></a>Závažná chyba C1510

Nejde otevřít jazykový prostředek clui.dll.

Kompilátor nemůže načíst knihovna DLL prostředků jazyka.

Existují dvě běžné příčiny tohoto problému. Při použití 32bitové verze kompilátoru a nástrojů, může se zobrazit tato chyba pro velké projekty, které používají více než 2GB paměti během odkaz. Možné řešení v 64bitových systémech Windows, je použít 64bitové nativní a křížový kompilátor a nástroje pro generování kódu. Toto využívá větší paměť k dispozici pro 64bitové aplikace. Pokud je nutné použít 32bitový kompilátor, protože běží v 32bitové verzi systému, v některých případech můžete zvýšit množství paměti k dispozici v linkeru na 3GB. Další informace najdete v tématu [4 GB optimalizace: nástroje BCDEdit a Boot.ini](https://msdn.microsoft.com/library/vs/alm/bb613473\(v=vs.85\).aspx) a [nástroje BCDEdit/sadě increaseuserva](https://msdn.microsoft.com/library/ff542202.aspx) příkazu.

Obvyklou příčinou je poškozený nebo neúplná instalace sady Visual Studio. V takovém případě opětovným spuštěním instalačního programu opravte nebo přeinstalujte Visual Studio.
