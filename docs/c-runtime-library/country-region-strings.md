---
title: "Řetězce zemí oblastí | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.strings
dev_langs: C++
helpviewer_keywords: country/region strings
ms.assetid: 5baf0ccf-0d9b-40dc-83bd-323705287930
caps.latest.revision: "14"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 3c250e47688e5fbcb32779d58dd8fe8973cdc96c
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="countryregion-strings"></a>Řetězce zemí/oblastí
Řetězce zemí a oblastí, mohou být kombinovány s řetězec jazyk specifikace národního prostředí pro vytvoření `setlocale`, `_wsetlocale`, `_create_locale`, a `_wcreate_locale` funkce. Seznam názvů země nebo oblast, které jsou podporovány v různých verzích operačního systému Windows, najdete v části [referenční dokumentace rozhraní API National jazykové podpory (NLS)](https://www.microsoft.com/resources/msdn/goglobal/default.mspx). V seznamu, může být řetězec země nebo oblast země hodnot v **národní prostředí – jazyk země nebo oblast** sloupce, nebo libovolná z zkratky v **zemi nebo oblast zkratka název** sloupce. Další jazyková podpora informace v operačních systémech Windows verze najdete v tématu [příloha A: produktu chování](http://msdn.microsoft.com/goglobal/bb896001.aspx) v [MS-LCID]: odkaz na Windows jazyk kódu identifikátor (LCID).  
  
 Implementace běhové knihovny jazyka C také podporuje následující řetězce další zemi nebo oblast a zkratky:  
  
|Řetězec země nebo oblast|Zkratka|Název ekvivalentní národní prostředí|  
|----------------------------|------------------|----------------------------|  
|Amerika|USA|en US|  
|Británie|GBR|en-GB|  
|Čína|CHN|zh-CN|  
|Čeština|CZE|cs-CZ|  
|v Anglii|GBR|en-GB|  
|Velká Británie|GBR|en-GB|  
|Holandsko|NLD|NL-NL|  
|Hongkong –|HKG|zh-HK|  
|Nový Zéland|NZL|en-NZ|  
|Nz|NZL|en-NZ|  
|Kód pr Čína|CHN|zh-CN|  
|Kód pr Čína|CHN|zh-CN|  
|Portoriko|PRI|ES-PR|  
|Slovenština|SVK|sk-SK|  
|Jihoafrická republika|ZAF|af ZA|  
|Korejská – jih|KOR|ko-KR|  
|Jihoafrická republika|ZAF|af ZA|  
|Korejská – jih|KOR|ko-KR|  
|Trinidad a tobago|CHCETE-LI|en-TT|  
|Spojené království|GBR|en-GB|  
|Spojené království|GBR|en-GB|  
|Spojené státy|USA|en US|  
|nám|USA|en US|  
  
## <a name="see-also"></a>Viz také  
 [Názvy národních prostředí, jazyků a řetězce zemí/oblastí](../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [Řetězce jazyků](../c-runtime-library/language-strings.md)   
 [setlocale –, _wsetlocale –](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [_create_locale –, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)