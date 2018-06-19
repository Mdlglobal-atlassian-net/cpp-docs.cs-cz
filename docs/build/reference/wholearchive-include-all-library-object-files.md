---
title: -WHOLEARCHIVE (zahrnout všechny soubory objekt knihovny) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.topic: reference
dev_langs:
- C++
ms.assetid: ee92d12f-18af-4602-9683-d6223be62ac9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c6de1aa92938a1523b86a90c58cc2d27f1181bfc
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376866"
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