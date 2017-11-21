---
title: "Závažná chyba C1510 | Microsoft Docs"
ms.custom: 
ms.date: 04/11/2017
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C1510
dev_langs: C++
helpviewer_keywords: C1510
ms.assetid: 150c827f-9514-41a9-8d7e-82f820749bcb
caps.latest.revision: "1"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 373cd74b1649fb9c1bd87cad1903df183f153c0f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="fatal-error-c1510"></a>Závažná chyba C1510
Nelze otevřít clui.dll prostředků jazyk  
  
 Kompilátor nelze načíst knihovnu DLL prostředku jazyk.  
  
Existují dvě běžné příčiny tohoto problému. Pokud používáte 32bitový kompilátor a nástroje, zobrazí se tato chyba pro rozsáhlých projektů, které používají více než 2GB paměti během odkaz. Možná řešení v systémech Windows 64-bit je nativní 64bitová verze nebo křížové kompilátoru a nástroje pro generování kódu. Toto využívá větší místo paměti, která je k dispozici pro 64bitové aplikace. Pokud kompilátoru 32-bit musíte použít, protože běží na 32bitové verzi systému, v některých případech můžete zvýšit množství paměti k dispozici linkeru 3 GB. Další informace najdete v tématu [4 GB optimalizace: nástroje BCDEdit a Boot.ini](https://msdn.microsoft.com/library/vs/alm/bb613473(v=vs.85).aspx) a [nástroje BCDEdit/set increaseuserva](https://msdn.microsoft.com/library/ff542202.aspx) příkaz.  

Obvyklou příčinou je poškozený nebo neúplná instalace sady Visual Studio. V takovém případě spusťte instalační program znovu k opravě nebo znovu nainstalujte Visual Studio.  
  