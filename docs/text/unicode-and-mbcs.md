---
title: Kódování Unicode a MBCS | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- _mbcs
dev_langs:
- C++
helpviewer_keywords:
- MBCS [C++], Unicode
- MFC [C++], character sets
- character sets [C++], multibyte
- run-time libraries [C++], language portability
- character sets [C++], Unicode
- Unicode [C++], MFC and C run-time functions
- multibyte characters [C++]
- runtime [C++], language portability
ms.assetid: 677baec6-71b4-4579-94df-64f18bc117c4
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2e10c07e11cbe940b5f7cfee460ddd33f6f5ff1f
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33857347"
---
# <a name="unicode-and-mbcs"></a>Unicode a MBCS
Knihovna Microsoft Foundation třídy (MFC), běhové knihovny jazyka C pro Visual C++ a vývojové prostředí Visual C++ jsou povolené pomůže mezinárodní programování. Poskytují:  
  
-   Podpora standardu Unicode v systému Windows. Znaková sada Unicode je aktuálním standardem a měla by být použita vždy, kdy je to možné.  
  
     Unicode je znak 16bitové kódování, poskytující dostatek kódování pro všechny jazyky. Všechny znaky ASCII jsou součástí Unicode jako rozšířené znaky.  
  
-   Podpora pro formulář vícebajtové znakové sady (MBCS) názvem dvoubajtové znakové sady (DBCS) na všech platformách.  
  
     Znaky DBCS se skládají z 1 nebo 2 bajty. Některé rozsahy bajtů jsou vyhrazeny pro použití jako úvodní bajty. Úvodní bajt určuje, že ji a následující druhý bajt tvoří jeden znak 2 bajty dlouhý. Musí udržovat přehled o bajtů, které jsou úvodní bajty. V sadě konkrétní vícebajtových znaků úvodní bajty spadá do určitého rozsahu, jako druhé bajty. Když tyto rozsahy překrývají, může být nutné vyhodnotit kontext pro zjištění, zda je daný bajt funguje jako úvodní bajt nebo druhý bajt.  
  
-   Podpora nástroje, které zjednodušují programování MBCS aplikace napsané pro mezinárodní trhy.  
  
     Při spuštění v znakovou sadou MBCS verzi operačního systému Windows, vývoj systému Visual C++ – včetně integrovaného editoru zdrojového kódu, ladicího programu a nástroje příkazového řádku – je zcela MBCS povolen. Další informace najdete v tématu [Podpora znakové sady MBCS v jazyku Visual C++](../text/mbcs-support-in-visual-cpp.md).  
  
> [!NOTE]
>  V této dokumentaci MBCS slouží k popisu podporu pro více-bajtové znaky kódování Unicode. V jazyce Visual C++ MBCS vždy znamená DBCS. Znakových sad větší než 2 bajty nejsou podporovány.  
  
 Podle definice je znaková sada ASCII podmnožinou všech vícebajtových znakových sad. V mnoha vícebajtových znakových sad každý znak v rozsahu 0x00 – 0x7F je stejný jako znak, který má stejnou hodnotu ve znakové sadě ASCII. Například v ASCII a MBCS znakové řetězce, 1bajtů **NULL** (\0) má hodnotu 0x00 a označuje ukončující znak hodnoty null.  
  
## <a name="see-also"></a>Viz také  
 [Text a řetězce](../text/text-and-strings-in-visual-cpp.md)   
 [Podpora národních prostředí](../text/international-enabling.md)