---
title: Strategie internacionalizace | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
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
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 944ba06bd7b3d81abb2ab431494096f9ade77574
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="internationalization-strategies"></a>Strategie internacionalizace
V závislosti na cílový operační systémy a trhy máte několik Strategie internacionalizace:  
  
-   Vaše aplikace používá kódování Unicode a proto se spustí v systému Windows 2000 a Windows NT, ale není v systému Windows 95 nebo Windows 98.  
  
     Použijte Unicode specifické funkce a všechny znaky jsou široké 16 bitů (i když můžete použít znaky ANSI v některých částech vašeho programu pro zvláštní účely). Běhové knihovny jazyka C poskytuje funkce, makra a datové typy pro programování výhradně kódování Unicode. MFC je plně kódování Unicode.  
  
-   Vaše aplikace používá rozhraní MBCS a může být spouštěn na libovolné platformě Win32.  
  
     Používáte funkce specifické pro MBCS. Řetězce mohou obsahovat jednobajtové znaky, dvoubajtové znaky nebo obojí. Běhové knihovny jazyka C poskytuje funkce, makra a datové typy znakové sady MBCS – pouze pro programování. MFC je plně MBCS povolen.  
  
-   Zdrojový kód pro vaši aplikaci je napsán pro dokončení přenositelnost – opětovnou kompilací symbolem **_UNICODE** nebo symbol **_MBCS** definovat, můžete vytvořit verze, využívající buď. Další informace najdete v tématu [mapování obecného textu v souboru Tchar.h](../text/generic-text-mappings-in-tchar-h.md).  
  
-   Vaše aplikace používá knihovnu obálku pro chybějící Unicode funkce v systému Windows 95, Windows 98 a Windows ME jako ten, popsané v [návrh jenom jedna aplikace kódování Unicode, který běží v systémech Windows 98 a systému Windows 2000](http://go.microsoft.com/fwlink/p/?LinkId=250770). Obálka knihovny jsou k dispozici komerčně.  
  
     Můžete používat plně přenositelné C Runtime funkcí, makra a datové typy. Flexibilita knihovny MFC podporuje některé z těchto strategií.  
  
 Zbývající část těchto témat se zaměřuje na psaní úplně přenosné kód, který můžete vytvořit ve formátu Unicode nebo jako MBCS.  
  
## <a name="see-also"></a>Viz také  
 [Kódování Unicode a MBCS](../text/unicode-and-mbcs.md)   
 [Národní prostředí a kódové stránky](../text/locales-and-code-pages.md)