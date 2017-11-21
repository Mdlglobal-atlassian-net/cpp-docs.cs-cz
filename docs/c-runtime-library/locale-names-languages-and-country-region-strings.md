---
title: "Názvy národních prostředí, jazyků a řetězce zemí oblastí | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.strings
dev_langs: C++
helpviewer_keywords:
- country/region strings
- localization, locale
- locales
- setlocale function
- language strings
ms.assetid: a0e5a0c5-5602-4da0-b65f-de3d6c8530a2
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 54a309b75d5e6b1773b7dd9bb294a1538397fd05
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="locale-names-languages-and-countryregion-strings"></a>Řetězce s názvy národních prostředí, jazyků a zemí/oblastí
*Národního prostředí* argument `setlocale` a `_create_locale` funkce lze nastavit pomocí názvy národních prostředí, jazyků, kódy zemí a znakové stránky, které jsou podporované rozhraním API systému Windows NLS. *Národního prostředí* argument má následující podobu:  
  
> *národní prostředí* :: "*název_národního_prostředí*"  
&nbsp;&nbsp;&nbsp;&nbsp;| "*jazyk*\[\_*země oblast*]\[. *code_page*]] "  
&nbsp;&nbsp;&nbsp;&nbsp;| ". *code_page*"  
&nbsp;&nbsp;&nbsp;&nbsp;| "C"  
&nbsp;&nbsp;&nbsp;&nbsp;| ""  
&nbsp;&nbsp;&nbsp;&nbsp;| HODNOTU NULL  
  
 Název formuláře národního prostředí je upřednostňovaný; například použít `en-US` pro angličtinu (Spojené státy) nebo `bs-Cyrl-BA` pro Bosenština (cyrilici, Bosny a Hercegoviny). Sada názvů národního prostředí je popsaná v [názvy národních prostředí](http://msdn.microsoft.com/library/windows/desktop/dd373814.aspx). Seznam názvů podporované národní prostředí podle verze operačního systému Windows, najdete v článku **název jazykové verze** sloupec [referenční dokumentace rozhraní API National jazykové podpory (NLS)](https://www.microsoft.com/resources/msdn/goglobal/default.mspx). Tento materiál obsahuje seznam podporovaných částí názvů národních prostředí, jež udávají jazyk, způsob zápisu a oblast. Informace o názvech podporované národní prostředí, které mají jiné než výchozí pořadí řazení, najdete v článku **název národního prostředí** sloupec v [identifikátory pořadí řazení](http://msdn.microsoft.com/library/windows/desktop/dd374060.aspx). Další informace o podpoře jazyka a umístění v operačním systému Windows verze najdete v tématu [příloha A: produktu chování](http://msdn.microsoft.com/goglobal/bb896001.aspx) v [MS-LCID]: odkaz na Windows jazyk kódu identifikátor (LCID). V části Windows 10 nebo novější jsou povolené názvy národních prostředí, které odpovídají platných značek pro jazyk BCP 47. Například `jp-US` je platnou značku BCP 47, ale je efektivně pouze `US` pro funkci národního prostředí.  
  
 *Jazyk*[*_country_region*[. *code_page*]] formuláře je uložená v nastavení národního prostředí pro kategorii když jazyk řetězec nebo řetězec jazyka a řetězec země nebo oblast se používá k vytvoření národní prostředí. Sada podporované jazykové řetězce je popsaná v [řetězce jazyků](../c-runtime-library/language-strings.md), a seznam řetězců, podporované země nebo oblast je uvedené v [řetězce zemí/oblastí](../c-runtime-library/country-region-strings.md). Pokud zadaný jazyk není spojen se zadanou zemí nebo oblastí, uloží se v nastavení národního prostředí výchozí jazyk pro zadanou zemi nebo oblast. Tuto formu řetězců národního prostředí vložených do kódu nebo serializovaných do úložiště nedoporučujeme, protože tyto řetězce s větší pravděpodobností podlehnou změně při aktualizaci operačního systému než u formy s názvem národního prostředí.  
  
 Znaková stránka je znaková stránka ANSI/OEM spojená s daným národním prostředím. Znakovou stránku za vás určíme, pokud zadáte národní prostředí pouze pomocí jazyka nebo jazyka a země či oblasti. Speciální hodnota `.ACP` Určuje znakovou stránku ANSI pro zemi nebo oblasti. Speciální hodnota `.OCP` určuje OEM znakovou stránku pro zemi nebo oblasti. Pokud zadáte třeba `"Greek_Greece.ACP"` jako národní prostředí, národní prostředí je uložena jako `Greek_Greece.1253` (ANSI znaková stránka pro řečtina), a pokud zadáte `"Greek_Greece.OCP"` jako národní prostředí, je uloženo jako `Greek_Greece.737` (kódové stránky OEM pro řečtina). Další informace o znakové stránky najdete v tématu [znakové stránky](../c-runtime-library/code-pages.md). Seznam podporovaných znakové stránky v systému Windows, naleznete v části [kódu stránky identifikátory](http://msdn.microsoft.com/library/windows/desktop/dd317756.aspx).  
  
 Pokud určíte národní prostředí pouze pomocí znakové stránky, použije se výchozí jazyk a země/oblast v systému. Pokud zadáte například `".1254"` (ANSI turečtina) jako národní prostředí v systému, který je nakonfigurován pro angličtinu (Spojené státy), je jako národní prostředí, který je uložený `English_United States.1254`. Tuto formu ukládání nedoporučujeme, protože může způsobit nekonzistentní chování.  
  
A *národního prostředí* hodnotu argumentu `C` Určuje minimální prostředí vyhovující ANSI C překlad. `C` Národního prostředí předpokládá, že každý `char` datový typ je 1 bajtů a jeho hodnota může být vždy menší než 256. Pokud *národního prostředí* bodů na prázdný řetězec, národní prostředí je definované implementací nativní prostředí.  
  
Zadejte všechny kategorie národního prostředí ve stejnou dobu pro `setlocale` a `_wsetlocale` funkce pomocí `LC_ALL` kategorie. Všechny kategorie mohou být nastaveny na stejné národní prostředí nebo můžete nastavit každou kategorii samostatně pomocí argumentu národního prostředí, který má tento tvar:  
  
> LC_ALL_specifier:: národní prostředí  
&nbsp;&nbsp;&nbsp;&nbsp;| [Lc_collate – národní prostředí =] [; LC_CTYPE – národní prostředí =] [; Lc_monetary – národní prostředí =] [; Lc_numeric – národní prostředí =] [; Lc_time – národní prostředí =]  
  
Můžete zadat více typů kategorií oddělených středníky. Typy kategorií, které nejsou zadány, používají aktuální nastavení národního prostředí. Například tento fragment kódu nastaví aktuální národní prostředí pro všechny kategorie pro `de-DE`a poté nastaví kategorie `LC_MONETARY` k `en-GB` a `LC_TIME` k `es-ES`:  
  
```C  
_wsetlocale(LC_ALL, L"de-DE");  
_wsetlocale(LC_ALL, L"LC_MONETARY=en-GB;LC_TIME=es-ES");  
```  
  
## <a name="see-also"></a>Viz také  
 [Referenční dokumentace běhové knihovny jazyka C](../c-runtime-library/c-run-time-library-reference.md)   
 [_get_current_locale –](../c-runtime-library/reference/get-current-locale.md)   
 [setlocale –, _wsetlocale –](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [_create_locale –, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)   
 [Řetězce jazyků](../c-runtime-library/language-strings.md)   
 [Řetězce zemí/oblastí](../c-runtime-library/country-region-strings.md)