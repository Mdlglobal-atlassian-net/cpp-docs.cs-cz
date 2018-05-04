---
title: -DEBUGTYPE (Možnosti ladicích informací) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /debugtype
dev_langs:
- C++
helpviewer_keywords:
- /DEBUGTYPE linker option
- DEBUGTYPE linker option
- -DEBUGTYPE linker option
ms.assetid: 1ddcb718-7fec-4f92-a319-3f70f04fe742
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 66868f7648d20b890f3c1e8c40802d77e3af4544
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="debugtype-debug-info-options"></a>/DEBUGTYPE (možnosti ladicích informací)
Možnost /DEBUGTYPE Určuje typy ladicí informace generované možnost/Debug.  
  
```  
/DEBUGTYPE:[CV | PDATA | FIXUP]  
```  
  
## <a name="arguments"></a>Arguments  
 ODCHYLKA NÁKLADŮ  
 Informuje linkeru pro vydávání informace o ladění pro symboly, čísla řádků a další informace o kompilace objektu v souboru PDB. Ve výchozím nastavení, tato možnost je povolená při **/DEBUG** je zadán a **/DEBUGTYPE** není zadán.  
  
 PDATA  
 Informuje linkeru pro přidání položek .pdata a .xdata na informace o datový proud ladění do souboru PDB. Ve výchozím nastavení, tato možnost je povolená při jak **/DEBUG** a **/Driver** možnosti nejsou zadány. Pokud **/DEBUGTYPE:PDATA** je zadán samostatně, linkeru automaticky zahrne symboly v souboru PDB ladění. Pokud **/DEBUGTYPE:PDATA oprava** není zadaný, linkeru nezahrnuje symboly v souboru PDB ladění.  
  
 OPRAVA  
 Informuje linkeru pro přidání položky tabulky přemístění do informace o datový proud ladění do souboru PDB. Ve výchozím nastavení, tato možnost je povolená při jak **/DEBUG** a **/PROFILE** možnosti nejsou zadány. Pokud **/DEBUGTYPE:FIXUP** nebo **/DEBUGTYPE:FIXUP PDATA** není zadaný, linkeru nezahrnuje symboly v souboru PDB ladění.  
  
 Argumenty pro **/DEBUGTYPE** mohou být kombinovány v libovolném pořadí, oddělte je čárkami. **/DEBUGTYPE** možnost a její argumenty nejsou velká a malá písmena.  
  
## <a name="remarks"></a>Poznámky  
 Použití **/DEBUGTYPE** možnost zadat zahrnutí přemístění dat nebo .pdata a .xdata záhlaví informace o tabulce v datovém proudu ladění. To způsobí, že linkeru informace o uživatelském režimu kód, který se zobrazí v ladicí program jádra po pozastavení v režimu jádra kódu. Chcete zpřístupnit symboly pro ladění při **oprava** je zadán, zahrnují **odchylka nákladů** argument.  
  
 Ladění kódu v uživatelském režimu, což je typické pro aplikace, **/DEBUGTYPE** není vyžadována možnost. Ve výchozím nastavení, přepínače kompilátoru, které určují ladění výstupu ([/Z7, / zi, /ZI](../../build/reference/z7-zi-zi-debug-information-format.md)) emitování všechny informace potřebné pomocí sady Visual Studio ladicího programu. Použití **/DEBUGTYPE:PDATA** nebo **/DEBUGTYPE:CV, PDATA, oprava** ladit kód, který kombinuje uživatelského režimu a režimu jádra součásti, jako je například konfigurace aplikace pro ovladač zařízení. Další informace o ladicí programy režimu jádra najdete v tématu [ladicích nástrojů pro systém Windows (WinDbg, KD, CDB, NTSD)](http://go.microsoft.com/fwlink/p?LinkID=285651)  
  
## <a name="see-also"></a>Viz také  
 [/ DEBUG (Generovat ladicí informace)](../../build/reference/debug-generate-debug-info.md)   
 [/ DRIVER (ovladač režimu jádra systému Windows NT)](../../build/reference/driver-windows-nt-kernel-mode-driver.md)   
 [/ PROFILE (Profiler nástrojů výkonu)](../../build/reference/profile-performance-tools-profiler.md)   
 [Nástroje pro ladění pro Windows (WinDbg, KD, CDB, NTSD)](http://go.microsoft.com/fwlink/p?LinkID=285651)