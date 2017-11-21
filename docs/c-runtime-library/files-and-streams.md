---
title: Soubory a proudy | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- files [C++]
- streams
ms.assetid: f61e712b-eac9-4c28-bb18-97c3786ef387
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 42237a142226d70b3cff0c07de5ed3daaeda8682
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="files-and-streams"></a>Soubory a proudy
Program komunikuje s cílové prostředí pomocí čtení a zápis souborů. Soubor může být:  
  
-   Datové sady, který lze číst a zapisovat opakovaně.  
  
-   Datový proud bajtů generovaných program (například kanál).  
  
-   Datového proudu bajtů přijatých z nebo na periferní zařízení.  
  
 Posledních dvou položek jsou interaktivní soubory. Soubory jsou obvykle hlavní prostředky k interakci s program. Upravit tyto typy souborů prakticky stejně – voláním funkce knihovny. Můžete zahrnout standardní hlavičku STDIO. H deklarovat většina těchto funkcí.  
  
 Před provedením mnoho operací na soubor, musí být soubor otevřít. Otevřením souboru přidruží k němu datového proudu, struktura dat v rámci standardní knihovny jazyka C, která glosses přes mnoho rozdíly mezi soubory různé typy. Knihovny udržuje stav jednotlivých datových proudech v objektu typu souboru.  
  
 Cílové prostředí otevře tři soubory před spuštění programu. Můžete otevřít soubor voláním funkce knihovny [fopen –, _wfopen –](../c-runtime-library/reference/fopen-wfopen.md) s dva argumenty. ( `fopen` Funkce se už nepoužívá, použijte [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md) místo.) První argument je název souboru. Druhý argument je C řetězec, který určuje:  
  
-   Jestli chcete načíst data ze souboru nebo zapisovat data do ho nebo do obou.  
  
-   Jestli chcete vygenerovat nový obsah souboru (nebo vytvořte soubor neexistovala dříve) nebo ponechejte stávajícího obsahu na místě.  
  
-   Jestli zápisy do souboru můžete měnit existující obsah nebo by měla pouze připojit bajtů na konci souboru.  
  
-   Jestli chcete upravit text datový proud nebo binární datový proud.  
  
 Jakmile úspěšně otevření souboru, můžete pak určit, zda je datový proud zaměřené na konkrétní bajtů (datového proudu bajtů) nebo celý zaměřené na konkrétní (wide datový proud). Datový proud je původně nevázaný. Volání metody určité funkce pracovat v datovém proudu je bajtů zaměřené na konkrétní, zatímco některých dalších funkcí ověření konzistence zaměřené na konkrétní. Po vytvoření datového proudu udržuje její orientace, dokud je uzavřený voláním [fclose –](../c-runtime-library/reference/fclose-fcloseall.md) nebo [freopen –](../c-runtime-library/reference/freopen-wfreopen.md).  
  
 © 2001 1989 podle P.J. Plauger a Jima Brodie. Všechna práva vyhrazena.  
  
## <a name="see-also"></a>Viz také  
 [Textové a binární proudy](../c-runtime-library/text-and-binary-streams.md)   
 [Bajtové a široké proudy](../c-runtime-library/byte-and-wide-streams.md)   
 [Řídicí proudy](../c-runtime-library/controlling-streams.md)   
 [Stavy proudu](../c-runtime-library/stream-states.md)