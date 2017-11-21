---
title: "-DELAY (nastavení importu odloženého načtení) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /delay
- VC.Project.VCLinkerTool.DelayNoBind
- VC.Project.VCLinkerTool.SupportUnloadOfDelayLoadedDLL
- VC.Project.VCLinkerTool.DelayUnload
dev_langs: C++
helpviewer_keywords:
- delayed loading of DLLs, /DELAY option
- DELAY linker option
- /DELAY linker option
- -DELAY linker option
ms.assetid: 9334b332-cc58-4dae-b10f-a4c75972d50c
caps.latest.revision: "10"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 86b076b8a3591ef75ad07cd47a525e67576317f6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="delay-delay-load-import-settings"></a>/DELAY (nastavení importu odloženého načtení)
```  
/DELAY:UNLOAD  
/DELAY:NOBIND  
```  
  
## <a name="remarks"></a>Poznámky  
 Ovládací prvky/delay – možnost [odložené načtení](../../build/reference/linker-support-for-delay-loaded-dlls.md) knihoven DLL:  
  
-   Kvalifikátor uvolnění informuje načtení zpoždění pomocné funkce pro podporu explicitní uvolnění knihovny DLL. Import tabulky adres (IAT) je obnovit původní podobě, zneplatnění IAT ukazatele a způsobit tak je možné přepsat.  
  
     Pokud nevyberete uvolnění, žádném volání [FUnloadDelayLoadedDLL](../../build/reference/explicitly-unloading-a-delay-loaded-dll.md) se nezdaří.  
  
-   Kvalifikátor NOBIND informuje linkeru nechcete zahrnout vazbu IAT finální image. Ve výchozím nastavení se vytvořit vazbu IAT pro knihovny DLL s odloženým načtením. Výsledný obraz nemůže být vázán staticky. (Obrázky s vazbu IATs pravděpodobně staticky vázán před spuštění.) V tématu [/BIND](../../build/reference/bind.md).  
  
     Pokud je vázána knihovnu DLL, pomocné funkce se pokusí použít vázané informace namísto volání [GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212.aspx) na každém z odkazovaného importy. Pokud časové razítko nebo upřednostňovanou adresu neodpovídá těch, které načtené knihovny DLL, bude předpokládat pomocné funkce vázané IAT je zastaralá a bude pokračovat, jako kdyby vázané IAT neexistuje.  
  
     Příčiny NOBIND vašeho programu obrázku musí být větší, ale může urychlit načíst čas knihovnu DLL. Pokud chcete nikdy vazby knihovnu DLL, NOBIND zabrání vázané IAT generování.  
  
 Pokud chcete zadat knihovny DLL pro odložené načtení, použijte [/DELAYLOAD](../../build/reference/delayload-delay-load-import.md) možnost.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Informace najdete v tématu [práce s vlastnostmi projektu](../../ide/working-with-project-properties.md).  
  
2.  Rozbalte položku **vlastnosti konfigurace**, **Linkeru**a potom vyberte **Upřesnit**.  
  
3.  Změnit **knihovny DLL načtené se zpožděním** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.DelayLoadDLLs%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)