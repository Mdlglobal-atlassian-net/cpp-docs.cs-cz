---
title: "Podpora národních prostředí | Microsoft Docs"
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
- strings [C++], international enabling
- localization [C++], character sets
- MBCS [C++], enabling
- Unicode [C++], enabling
ms.assetid: b077f4ca-5865-40ef-a46e-d9e4d686ef21
caps.latest.revision: 
author: ghogen
ms.author: ghogen
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ce0210546dafd354d0d62225c97df8b36a8d84e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="international-enabling"></a>Podpora národních prostředí
Nejvíce tradiční kód C a C++ provádí předpoklady o manipulaci znak a řetězce, které nefungují správně pro mezinárodní aplikace. Zatímco MFC a knihovna RTL – podporují kódování Unicode a MBCS, je stále pracovní musíte udělat. Vám tato část vysvětluje význam "podpora národních prostředí" v jazyce Visual C++:  
  
-   Kódování Unicode a MBCS jsou povolené prostřednictvím přenosné datové typy v seznamech parametr funkce MFC a návratové typy. Tyto typy jsou podmíněně definovány odpovídající způsoby v závislosti na tom, zda vaše sestavení definuje symbol **_UNICODE** nebo symbol **_MBCS** (to znamená DBCS). Různé varianty knihovny MFC jsou automaticky propojení s vaší aplikací, v závislosti na tom, která z těchto dvou symbolů vaše sestavení definuje.  
  
-   Kód knihovny tříd používá k zajištění správné chování Unicode nebo MBCS přenosné běhové funkce a jiným způsobem.  
  
-   Stále musíte zpracovat určité druhy internacionalizace úloh ve vašem kódu:  
  
    -   Použijte stejné přenosné běhové funkce, které vytváří knihovna MFC přenosné pod buď prostředí.  
  
    -   Vytvořte literály a znaky přenositelných pod buď prostředí pomocí **_T** makro. Další informace najdete v tématu [mapování obecného textu v souboru Tchar.h](../text/generic-text-mappings-in-tchar-h.md).  
  
    -   Při analýze řetězce v rámci MBCS je potřeba zaveďte opatření. Tato opatření nejsou potřeba v kódování Unicode. Další informace najdete v tématu [tipy pro programování MBCS](../text/mbcs-programming-tips.md).  
  
    -   Ujistěte se, pokud zároveň ANSI (8 bitů) a znaky znakové sady Unicode (16 bitů) ve vaší aplikaci. Je možné použít znaky ANSI v některých částech vašeho programu a znaky kódování Unicode v jiné, ale není možné kombinovat ve stejném řetězci.  
  
    -   Řetězce pevné kódování ve vaší aplikaci udělat. Místo toho je proveďte STRINGTABLE zdrojích jejich přidáním do souboru .rc aplikace. Aplikace může být lokalizována bez nutnosti změny zdrojového kódu nebo opětovnou kompilaci. Další informace o prostředcích STRINGTABLE najdete v tématu [Editor řetězce](../windows/string-editor.md).  
  
> [!NOTE]
>  Znakové sady Evropské a MBCS mají některé znaky, jako je například písmena s diakritikou s větší než 0x80 kódy znaků. Protože většinu kódu používá podepsané znaky, jsou tyto znaky, které jsou větší než 0x80 rozšířeny při převodu do `int`. Tento problém pro indexování pole je vzhledem k tomu, že znaky s rozšířeným negativní, indexy mimo pole. Jazyky, které používají MBCS, jako je například v japonštině, jsou také jedinečné. Vzhledem k tomu může znak obsahovat 1 nebo 2 bajtů, by měla vždycky upravit obou bajtů ve stejnou dobu.  
  
## <a name="see-also"></a>Viz také  
 [Kódování Unicode a MBCS](../text/unicode-and-mbcs.md)   
 [Strategie internacionalizace](../text/internationalization-strategies.md)