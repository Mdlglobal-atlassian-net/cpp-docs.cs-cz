---
title: Názvy prostředí | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: 9af409a5-e724-465a-9a21-88d3586c2e92
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 5a1eea91a6955705c062a9c8509cbdeb8dc4598d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="environment-names"></a>Názvy prostředí
**ANSI 4.10.4.4** sadu názvy prostředí a metody pro změnu seznamu prostředí používá [GETENV –](../c-runtime-library/reference/getenv-wgetenv.md) – funkce  
  
 Sada názvů prostředí je neomezená.  
  
 Chcete-li změnit proměnné prostředí z v rámci programu C, zavolejte [_putenv –](../c-runtime-library/reference/putenv-wputenv.md) funkce. Chcete-li změnit proměnné prostředí z příkazového řádku v systému Windows, použijte příkaz SET (například SET LIB = D:\LIBS).  
  
 Proměnné prostředí nastavené v programu jazyka C existují pouze tak dlouho, dokud je spuštěna jejich kopie příkazového prostředí operačního systému (CMD.EXE nebo COMMAND.COM). Například řádek  
  
```  
system( SET LIB = D:\LIBS );  
```  
  
 spustí kopii příkazového prostředí (CMD.EXE), nastaví proměnnou prostředí LIB, vrátí se do programu jazyka C a ukončí sekundární kopii programu CMD.EXE. Ukončení této kopie programu CMD.EXE odebere dočasnou proměnnou prostředí LIB.  
  
 Podobně změny provedené pomocí funkce `_putenv` trvají pouze do ukončení programu.  
  
## <a name="see-also"></a>Viz také  
 [Funkce knihovny](../c-language/library-functions.md)   
 [_putenv, _wputenv](../c-runtime-library/reference/putenv-wputenv.md)   
 [getenv, _wgetenv](../c-runtime-library/reference/getenv-wgetenv.md)