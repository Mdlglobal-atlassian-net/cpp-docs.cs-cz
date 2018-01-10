---
title: "Řetězce jazyků | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.strings
dev_langs: C++
helpviewer_keywords: language strings
ms.assetid: bbee63b1-af0b-4e44-9eaf-dd3e265c05fd
caps.latest.revision: "17"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 85f0c9b06ae85128209f06d95375e09043b3f9c8
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="language-strings"></a>Řetězce jazyků
`setlocale` a `_create_locale` funkce můžete použít rozhraní API systému Windows NLS podporované jazyky v operačních systémech, které nepoužívají znaková stránka kódování Unicode. Seznam podporovaných jazyků podle verze operačního systému najdete v tématu [referenční dokumentace rozhraní API National jazykové podpory (NLS)](https://www.microsoft.com/resources/msdn/goglobal/default.mspx). Řetězec jazyka může být některá z hodnot v **jazyk** a **zkratka jazyka** sloupce seznam podporovaných jazyků. Další informace o podpoře jazyka podle verze operačního systému najdete v tématu [příloha A: produktu chování](http://msdn.microsoft.com/goglobal/bb896001.aspx) v [MS-LCID]: odkaz na Windows jazyk kódu identifikátor (LCID).   
  
Implementace běhové knihovny jazyka C také podporuje tyto řetězce jazyků:  
  
|Řetězec jazyka|Název ekvivalentní národní prostředí|  
|---------------------|----------------------------|  
|American|en US|  
|americká angličtina|en US|  
|americká angličtina|en US|  
|australské|en-AU|  
|Belgické|NL-být|  
|Kanadští|en-CA|  
|CHH|zh-HK|  
|-či-|zh-SG|  
|Čínština|zh|  
|hongkong čínština|zh-HK|  
|čínština (zjednodušená)|zh-CN|  
|Čínština Singapur|zh-SG|  
|tradiční čínština|zh-TW.|  
|Holandština Belgické|NL-být|  
|americká angličtina|en US|  
|Austrálie angličtina|en-AU|  
|Angličtina belize|en-BZ|  
|Angličtina může|en-CA|  
|Angličtina karibskými|en-029|  
|Angličtina ire|en-IE|  
|Angličtina Jamajka|en-JM|  
|nz angličtina|en-NZ|  
|Angličtina Jihoafrická republika|en-ZA|  
|Angličtina trinidad a tobago|en-TT|  
|Angličtina-Spojené království|en-GB|  
|Angličtina-nám|en US|  
|Angličtina usa|en US|  
|Francouzština Belgické|FR-být|  
|French-Canadian|fr-CA|  
|Francouzština Lucembursko|FR-LU|  
|Francouzština mezi|FR-CH|  
|Němčina rakouském|de-AT|  
|Němčina lichtenstein|de-LI|  
|Němčina Lucembursko|de-LU|  
|mezi němčina|de-CH|  
|irskou angličtina|en-IE|  
|Italština mezi|IT-CH|  
|Norština|Ne|  
|Norština Bokmål|nb-NO|  
|norština nynorsk|nn ne|  
|portugalština – Brazílie|pt-BR|  
|Španělština argentina|ES-AR|  
|Španělština Bolívie|ES provést|  
|Španělština základě|ES-CL|  
|Španělština Kolumbie|ES-CO|  
|Španělština Kostarika|ES-CR|  
|Španělština Dominikánská republika|Proveďte ES|  
|Španělština Ekvádor|ES ES|  
|Španělština el salvador|ES SV|  
|Španělština Kostarika|ES-GT|  
|Španělština honduras|ES-HN|  
|Španělština mexickými|ES-MX|  
|Španělština moderních|ES-ES|  
|Španělština Nikaragua|ES-NI|  
|Španělština panama|ES-PA|  
|Španělština paraguay|ES-PY|  
|Španělština peru|ES-PE|  
|Španělština Portoriko|ES-PR|  
|Španělština Uruguayského|ES-UY|  
|Španělština venezuela|ES Sunout|  
|Švédština Finsko|sv-FI|  
|mezi|de-CH|  
|Spojené království|en-GB|  
|nám|en US|  
|USA|en US|  
  
## <a name="see-also"></a>Viz také  
 [Názvy národních prostředí, jazyků a řetězce zemí/oblastí](../c-runtime-library/locale-names-languages-and-country-region-strings.md)   
 [Řetězce zemí/oblastí](../c-runtime-library/country-region-strings.md)   
 [setlocale –, _wsetlocale –](../c-runtime-library/reference/setlocale-wsetlocale.md)   
 [_create_locale, _wcreate_locale](../c-runtime-library/reference/create-locale-wcreate-locale.md)