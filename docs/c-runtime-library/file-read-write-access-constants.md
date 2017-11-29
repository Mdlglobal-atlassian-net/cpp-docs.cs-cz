---
title: "Konstanty přístupu pro čtení a zápis do souboru | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: c.constants.file
dev_langs: C++
helpviewer_keywords:
- read/write access constants
- write access constants
- access constants for file read/write
- constants [C++], file attributes
- file read/write access constants
ms.assetid: 56cd1d22-39a5-4fcf-bea2-7046d249e8ee
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2d32e9da99776bf5e21805ec239c2731cc3d5f21
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="file-readwrite-access-constants"></a>Konstanty přístupu pro čtení a zápis do souboru
## <a name="syntax"></a>Syntaxe  
  
```  
  
#include <stdio.h>  
```  
  
## <a name="remarks"></a>Poznámky  
 Tyto konstanty zadejte požadované pro soubor typ přístupu ("a", "r" nebo "w"). Obě [režim překladu](../c-runtime-library/file-translation-constants.md) ("b" nebo "t") a [potvrzení disku režimu](../c-runtime-library/commit-to-disk-constants.md) ("c" nebo "n") lze určit typ přístupu.  
  
 Typy přístupu jsou popsané níže.  
  
 **"a"**  
 Otevře pro zápis na konec souboru (připojení); nejprve vytvoří soubor, pokud neexistuje. Všechny zápisu operace probíhají na konci souboru. I když ukazatele souboru můžete změnit jejich umístění pomocí `fseek` nebo **rewind**, je vždy přesunuta zpět na konec souboru před všechny zápisu operace provádí.  
  
 **"+"**  
 Stejné jako vyšší, ale také umožňuje čtení.  
  
 **"r"**  
 Otevře pro čtení. Pokud soubor neexistuje nebo nebyl nalezen, volání k otevření souboru se nezdaří.  
  
 **"r +"**  
 Otevře pro čtení i zápis. Pokud soubor neexistuje nebo nebyl nalezen, volání k otevření souboru se nezdaří.  
  
 **"w"**  
 Otevře se prázdný soubor pro zápis. Pokud je daný soubor existuje, její obsah se způsobem zničena.  
  
 **"w +"**  
 Otevře se prázdný soubor pro čtení i zápis. Pokud je daný soubor existuje, její obsah se způsobem zničena.  
  
 Pokud je zadána "r +", "w +" nebo "" typ +, jsou povoleny pro čtení i zápis (soubor říká, že je třeba otevřít pro "update"). Ale při přepínání mezi čtení a zápis, musí být uplynulého `fflush`, `fsetpos`, `fseek`, nebo **rewind** operaci. Aktuální pozice lze `fsetpos` nebo `fseek` operaci.  
  
## <a name="see-also"></a>Viz také  
 [_fdopen –, _wfdopen –](../c-runtime-library/reference/fdopen-wfdopen.md)   
 [fopen –, _wfopen –](../c-runtime-library/reference/fopen-wfopen.md)   
 [freopen –, _wfreopen –](../c-runtime-library/reference/freopen-wfreopen.md)   
 [_fsopen –, _wfsopen –](../c-runtime-library/reference/fsopen-wfsopen.md)   
 [_popen –, _wpopen –](../c-runtime-library/reference/popen-wpopen.md)   
 [Globální konstanty](../c-runtime-library/global-constants.md)