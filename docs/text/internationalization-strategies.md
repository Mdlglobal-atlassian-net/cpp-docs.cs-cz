---
title: Strategie internacionalizace | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
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
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1a3b8a47e70efa3268ae9b36eda311d267be2ded
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/09/2018
ms.locfileid: "40018926"
---
# <a name="internationalization-strategies"></a>Strategie internacionalizace
V závislosti na cílové operačních systémů a trhy máte několik Strategie internacionalizace:  
  
-   Vaše aplikace používá kódování Unicode.  
  
     Používat funkce specifické pro kódování Unicode a všechny znaky jsou široké 16 bitů (i když používáte znaků ANSI v některé části programu pro zvláštní účely). Knihovny run-time jazyka C poskytuje funkce, makra a datové typy pro programování výhradně kódování Unicode. Knihovna MFC je plně podporující kódování Unicode.  
  
-   Vaše aplikace používá znakovou sadu MBCS a může být spouštěn na libovolné platformě Win32.  
  
     Můžete používat funkce specifické znakové sady MBCS. Řetězce mohou obsahovat jednobajtové znaky, dvoubajtové znaky nebo obojí. Knihovny run-time jazyka C poskytuje funkce, makra a datové typy znakové sady MBCS – pouze pro programování. Knihovna MFC je plně podporují znakové sady MBCS.  
  
-   Zdrojový kód pro vaše aplikace je určené pro dokončení přenositelnost – opětovnou kompilací symbol `_UNICODE` nebo symbol `_MBCS` definována, můžete vytvářet verze, které buď použít. Další informace najdete v tématu [mapování obecného textu v souboru Tchar.h](../text/generic-text-mappings-in-tchar-h.md).  
  
     Můžete použít plně přenositelné C Runtime functions, makra a datové typy. Flexibilita knihovny MFC podporuje některý z těchto strategií.  
  
 Zbývající část těchto témat soustředit na psaní zcela přenositelný kód, který může vytvořit jako Unicode nebo znakové sady MBCS.  
  
## <a name="see-also"></a>Viz také  
 [Kódování Unicode a MBCS](../text/unicode-and-mbcs.md)   
 [Národní prostředí a kódové stránky](../text/locales-and-code-pages.md)