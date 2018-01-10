---
title: Typy SBCS a MBCS dat | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- MBCS
- SBCS
dev_langs: C++
helpviewer_keywords:
- SBCS and MBCS data types
- data types [C], MBCS and SBCS
ms.assetid: 4c3ef9da-e397-48d4-800e-49dba36db171
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c54b6e9716e7f0aee9a0b211148b76804d9520bf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="sbcs-and-mbcs-data-types"></a>Datové typy SBCS a MBCS
Veškeré `MBCS` očekává rutiny běhové knihovny, která zpracovává jenom jeden vícebajtových znaků nebo jeden bajt vícebajtových znaků `unsigned int` argument (kde 0x00 < = hodnota znaku < = 0xFFFF a 0x00 < = hodnota bajtu < = 0xFF). `MBCS` Rutiny, která zpracovává vícebajtové bajtů nebo znaků v kontextu řetězec očekává řetězec vícebajtových znaků tak, aby být reprezentován jako `unsigned char` ukazatel.  
  
> [!CAUTION]
>  Každý bajt vícebajtových znaků, které mohou být v 8-bit reprezentována `char`. Však `SBCS` nebo `MBCS` znakovou typu `char` s hodnotou vyšší než 0x7F je záporná. Když se takový znak přímo na převést `int` nebo `long`, výsledek je rozšířeny kompilátorem a proto přispět neočekávané výsledky.  
  
 Proto je nejlepší představují bajt vícebajtových znaků jako 8-bit `unsigned char`. Nebo, abyste se vyhnuli záporný výsledek, jednoduše převést znakovou typu `char` k `unsigned char` před jeho převodem `int` nebo `long`.  
  
 Protože některé `SBCS` proveďte funkce zpracování řetězců (se znaménkem) `char*` upozornění o neshodě typů parametrů, dojde při `_MBCS` je definována. Abyste tomu předešli, upozornění, uvedené v pořadí podle efektivitu třemi způsoby:  
  
1.  Použijte v Tchar – "bezpečnost typů" vložené funkce. H. Toto je výchozí chování.  
  
2.  Použijte "přímého" makra v Tchar –. H definováním `_MB_MAP_DIRECT` na příkazovém řádku. Pokud to uděláte, musíte ručně spárovat typy. To je nejrychlejší způsob, ale není bezpečnost typů.  
  
3.  Pomocí funkce "bezpečnost typů" staticky propojené knihovny v Tchar –. H. Uděláte to tak, definujte konstantu `_NO_INLINING` na příkazovém řádku. Toto je metoda nejpomalejší, ale nejvíce bezpečnost typů.  
  
## <a name="see-also"></a>Viz také  
 [Internacionalizace](../c-runtime-library/internationalization.md)   
 [Běhové rutiny podle kategorie](../c-runtime-library/run-time-routines-by-category.md)