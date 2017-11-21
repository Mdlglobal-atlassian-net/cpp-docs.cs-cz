---
title: "-TSAWARE (vytvořit aplikace podporující terminálového serveru) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /tsaware
- VC.Project.VCLinkerTool.TerminalServerAware
dev_langs: C++
helpviewer_keywords:
- Terminal Server
- /TSAWARE linker option
- Terminal Server, Terminal Server-aware applications
- -TSAWARE linker option
- TSAWARE linker option
ms.assetid: fe1c1846-de5b-4839-b562-93fbfe36cd29
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: da606dfd1dd486b952d2181d196d5668a6198d69
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="tsaware-create-terminal-server-aware-application"></a>/TSAWARE (Vytvořit aplikace s detekcí terminálového serveru)
```  
/TSAWARE[:NO]  
```  
  
## <a name="remarks"></a>Poznámky  
 Možnost/TSAWARE nastaví příznak v poli IMAGE_OPTIONAL_HEADER DllCharacteristics v nepovinné hlavičkové bitové kopie programu. Pokud je nastavený tento příznak, nebude terminálového serveru provádět určité změny aplikace.  
  
 Pokud aplikace není Terminálový Server využívající (také označované jako starší verze aplikace), provede terminálového serveru určité změny starší verze aplikace, aby byla správně fungovat v prostředí s více uživateli. Terminálový Server například vytvoří virtuální složka systému Windows, tak, aby každý uživatel získá složka systému Windows místo získávání adresáře systému Windows. To umožňuje uživatelům přístup k vlastní soubory INI. Kromě toho terminálového serveru provádí některé úpravy registru pro starší verze aplikace. Tyto úpravy pomalé načítání starší verze aplikace na terminálového serveru.  
  
 Pokud aplikace využívající terminálového serveru, musí, ani spoléhají na soubory INI ani zapisovat **HKEY_CURRENT_USER** registru během instalace.  
  
 Pokud používáte/TSAWARE a aplikace bude používat soubory INI, soubory budou sdílet všechny uživatele systému. Pokud tak je přijatelné, stále můžete propojit vaší aplikace pomocí/TSAWARE; v opačném případě budete muset použít /TSAWARE:NO.  
  
 Možnost/TSAWARE je povolená ve výchozím nastavení pro systém Windows 2000 nebo novější, Windows a konzolové aplikace. V tématu [/SUBSYSTEM](../../build/reference/subsystem-specify-subsystem.md) a [/VERSION](../../build/reference/version-version-information.md) informace.  
  
 / TSAWARE není platný pro ovladače, ovladače VxD a knihovny DLL.  
  
 Pokud aplikace bylo propojeno s/TSAWARE, DUMPBIN [/HEADERS](../../build/reference/headers.md) se zobrazí informace o tom.  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Nastavení tohoto parametru linkeru ve vývojovém prostředí sady Visual Studio  
  
1.  Otevření projektu **stránky vlastností** dialogové okno. Podrobnosti najdete v tématu [nastavení vlastností projektu Visual C++](../../ide/working-with-project-properties.md).  
  
2.  Klikněte **Linkeru** složky.  
  
3.  Klikněte **systému** stránku vlastností.  
  
4.  Změnit **terminálového serveru** vlastnost.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Programové nastavení tohoto parametru linkeru  
  
-   V tématu <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.TerminalServerAware%2A>.  
  
## <a name="see-also"></a>Viz také  
 [Nastavení možností Linkeru](../../build/reference/setting-linker-options.md)   
 [Možnosti linkeru](../../build/reference/linker-options.md)   
 [Ukládání informace o uživateli](http://msdn.microsoft.com/library/aa383452)   
 [Starší verze aplikace v prostředí Terminálové služby](https://msdn.microsoft.com/en-us/library/aa382957.aspx)