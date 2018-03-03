---
title: "-WHOLEARCHIVE (zahrnout všechny soubory objekt knihovny) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs:
- C++
ms.assetid: ee92d12f-18af-4602-9683-d6223be62ac9
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3499d6583c7d9801aa4c3b12c66196c975b192ea
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="wholearchive-include-all-library-object-files"></a>/ WHOLEARCHIVE (zahrnout všechny soubory objekt knihovny)
Vynutí linkeru mají být zahrnuty všechny soubory objektu se statickou knihovnou v propojených spustitelný soubor.  
  
## <a name="syntax"></a>Syntaxe  
  
> / WHOLEARCHIVE [:*knihovny*]  
  
## <a name="remarks"></a>Poznámky  
  
Možnost /WHOLEARCHIVE vynutí linkeru pro zahrnutí každý soubor objekt buď z zadané statické knihovny, nebo pokud je zadána žádná knihovna, ze všech statických knihoven zadaný odkaz na příkaz. Pokud chcete zadat možnost /WHOLEARCHIVE pro více knihovny, můžete použít více než jeden /WHOLEARCHIVE přepnout na příkazový řádek linkeru. Ve výchozím nastavení zahrnuje linkeru soubory objektů v propojených výstup, pouze v případě, že exportovat symboly odkazují jiné soubory objekt ve spustitelném souboru. Volba /WHOLEARCHIVE způsobí linkeru považovat všechny soubory objekt archivovány v statickou knihovnu, jako kdyby byly jednotlivě zadány na příkazovém řádku linkeru.  
  
Možnost /WHOLEARCHIVE lze znovu exportovat všechny symboly ze statické knihovny. To umožňuje Ujistěte se, že všechny vaše knihovna kódu, prostředky a metadata jsou zahrnuty při vytvoření komponenty z více než jeden statické knihovny. Pokud se zobrazí upozornění LNK4264 při vytváření statickou knihovnu, která obsahuje komponenty prostředí Windows Runtime pro export, použijte možnost /WHOLEARCHIVE při propojování této knihovny do jiné součást nebo aplikace.  
  
Možnost /WHOLEARCHIVE byla zavedena v sadě Visual Studio 2015 Update 2.  
  
### <a name="to-set-this-linker-option-in-visual-studio"></a>Nastavení této možnosti linkeru v sadě Visual Studio  
  
1.  Otevřete projekt **stránky vlastností** dialogové okno. Další informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
1.  Vyberte **příkazového řádku** stránka vlastností v rámci **vlastnosti konfigurace**, **Linkeru**.  
  
1.  Přidat možnost /WHOLEARCHIVE **další možnosti** textové pole.  
  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)