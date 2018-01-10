---
title: "Textové a binární proudy | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- binary streams
- text streams
ms.assetid: 57035e4a-955d-4e04-a560-fcf67ce68b4e
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 1665ff1551ffe94b475c463d8f93eba2184eaa27
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="text-and-binary-streams"></a>Textové a binární proudy
Datový proud s text se skládá z jednoho nebo více řádků textu, které je možné zapsat do zobrazení se text orientované tak, aby mohly být čteny. Při čtení z datového proudu textu, program přečte `NL` (každý na jednom řádku) na konci každého řádku. Při zápisu do proudu textu, zapíše program `NL` signál konec řádku. Tak, aby odpovídaly odlišné konvence mezi cílové prostředí pro představující text v souborech, můžete změnit funkce knihovny počet a reprezentace znaků přenesené mezi program a text datového proudu.  
  
 Proto umístění v rámci datového proudu text je omezený. Můžete získat aktuální indikátoru pozice souboru voláním [fgetpos –](../c-runtime-library/reference/fgetpos.md) nebo [ftell –](../c-runtime-library/reference/ftell-ftelli64.md). Datový proud s text můžete umístit na pozici získat tímto způsobem, nebo na začátku nebo na konec datového proudu, voláním [fsetpos –](../c-runtime-library/reference/fsetpos.md) nebo [fseek](../c-runtime-library/reference/fseek-fseeki64.md). Všechny ostatní změny pozice nemusí být kvalitně podporována.  
  
 Pro maximální přenositelnost nesmí program zápisu:  
  
-   Prázdné soubory.  
  
-   Mezery na konci řádku.  
  
-   Částečné řádky (Díky vynechání `NL` na konci souboru).  
  
-   jiné znaky než tisknutelná znaky, NL, a `HT` (vodorovné karta).  
  
 Pokud budete postupovat podle těchto pravidel, posloupnost znaků, které číst z datového proudu text (buď jako bajt nebo vícebajtové znaky) bude odpovídat posloupnost znaků, který jste napsali do proudu textu, když vytvoříte soubor. Funkce knihovny, jinak můžete odebrat soubor, který vytvoříte, pokud je soubor prázdný, když zavřete ho. Nebo můžete změnit ani odstranit znaky, které zapisovat do souboru.  
  
 Binární datový proud se skládá z jedné nebo více bajtů libovolné informace. Můžete napsat s hodnotou uloženou v libovolný objekt k binárnímu proudu (orientované bajtů) a čtení přesně co byla uložená v objektu, když ho napsal. Funkce knihovny nijak nemění bajtů, které můžete přenést mezi program a binárního datového proudu. Libovolný počet null bajtů se však můžete připojit k souboru, který můžete psát pomocí binárního datového proudu. Program musí řešit tyto další null bajtů na konci všechny binární datový proud.  
  
 Umístění v rámci binární datový proud je proto dobře definované, s výjimkou umístění relativně k konec datového proudu. Můžete získat a změnit aktuální indikátoru pozice souboru je stejný jako u datového proudu textu. Kromě toho používá posunutí [ftell –](../c-runtime-library/reference/ftell-ftelli64.md) a [fseek](../c-runtime-library/reference/fseek-fseeki64.md) počet bajtů od začátku datového proudu (což je nula bajtů), takže celé číslo aritmetické na tyto posuny poskytuje předvídatelný výsledky.  
  
 Tok bajtů zpracovává soubor jako pořadí bajtů. V rámci programu do datového proudu vypadá jako stejnou sekvenci bajtů, s výjimkou případné změny popsané výše.  
  
## <a name="see-also"></a>Viz také  
 [Soubory a proudy](../c-runtime-library/files-and-streams.md)