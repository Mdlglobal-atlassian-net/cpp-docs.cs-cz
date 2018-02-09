---
title: Strategie internacionalizace | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- globalization [C++], character sets
- language-portable code [C++]
- MBCS [C++], internationalization strategies
- Windows API [C++], international programming strategies
- Win32 [C++], international programming strategies
- Unicode [C++], globalizing applications
- character sets [C++], international programming strategies
- localization [C++], character sets
ms.assetid: b09d9854-0709-4b9a-a00c-b0b8bc4199b1
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ead6470bbbeacd43326f4373877eb991e5899116
ms.sourcegitcommit: a5916b48541f804a79891ff04e246628b5f9a24a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/09/2018
---
# <a name="internationalization-strategies"></a>Strategie internacionalizace
V závislosti na cílový operační systémy a trhy máte několik Strategie internacionalizace:  
  
-   Vaše aplikace používá kódování Unicode.  
  
     Použijte Unicode specifické funkce a všechny znaky jsou široké 16 bitů (i když můžete použít znaky ANSI v některých částech vašeho programu pro zvláštní účely). Běhové knihovny jazyka C poskytuje funkce, makra a datové typy pro programování výhradně kódování Unicode. MFC je plně kódování Unicode.  
  
-   Vaše aplikace používá rozhraní MBCS a může být spouštěn na libovolné platformě Win32.  
  
     Používáte funkce specifické pro MBCS. Řetězce mohou obsahovat jednobajtové znaky, dvoubajtové znaky nebo obojí. Běhové knihovny jazyka C poskytuje funkce, makra a datové typy znakové sady MBCS – pouze pro programování. MFC je plně MBCS povolen.  
  
-   Zdrojový kód pro vaši aplikaci je napsán pro dokončení přenositelnost – opětovnou kompilací symbolem **_UNICODE** nebo symbol **_MBCS** definovat, můžete vytvořit verze, využívající buď. Další informace najdete v tématu [mapování obecného textu v souboru Tchar.h](../text/generic-text-mappings-in-tchar-h.md).  
  
     Můžete používat plně přenositelné C Runtime funkcí, makra a datové typy. Flexibilita knihovny MFC podporuje některé z těchto strategií.  
  
 Zbývající část těchto témat se zaměřuje na psaní úplně přenosné kód, který můžete vytvořit ve formátu Unicode nebo jako MBCS.  
  
## <a name="see-also"></a>Viz také  
 [Kódování Unicode a MBCS](../text/unicode-and-mbcs.md)   
 [Národní prostředí a kódové stránky](../text/locales-and-code-pages.md)