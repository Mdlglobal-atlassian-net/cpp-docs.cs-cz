---
title: "Změny systému sestavení | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.msbuild.changes
dev_langs: C++
helpviewer_keywords:
- Build system changes, project file (.vcxprog)
- Build system changes, custom build rules
- Build system changes, MSBuild
- MSBuild, build system changes
- Build system changes, .vsprops
- Build system changes, $(Inherit)
- Build system changes, $(NoInherit)
ms.assetid: e564d95f-a6cc-4d97-b57e-1a71daf66f4a
caps.latest.revision: "13"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 90266f54dd6972e68abe770bad4ee323eebf46b7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="build-system-changes"></a>Změny systému sestavení
MSBuild systému se používá k sestavení projektů Visual C++. V sadě Visual Studio 2008 a starších verzích, ale byl použit VCBuild systému. Některé typy souborů a koncepty, které závisí na VCBuild neexistují nebo jsou v aktuálním systému zobrazovat jinak. Tento dokument popisuje rozdíly v aktuální systém sestavení.  
  
## <a name="vcproj-is-now-vcxproj"></a>.vcproj je nyní VCXPROJ  
 Soubory projektu již používat příponu názvu souboru .vcproj. Visual Studio automaticky převádí soubory projektu, které byly vytvořené pomocí dřívější verze Visual C++ do formátu, který je používán v aktuálním systému. Další informace o tom, jak ručně aktualizovat projekt najdete v tématu [spínače/upgradu (devenv.exe)](/visualstudio/ide/reference/upgrade-devenv-exe).  
  
 V aktuální verzi je přípona názvu souboru pro soubor projektu VCXPROJ.  
  
## <a name="vsprops-is-now-props"></a>.vsprops je nyní props  
 V dřívějších verzích *seznam vlastností projektu* je soubor formátu XML, který má příponu názvu souboru .vsprops. Seznam vlastností projektu umožňuje zadat přepínačů pro sestavení nástroje, například kompilátoru nebo linkeru a vytvořit uživatelská makra.  
  
 V aktuální verzi je přípona názvu souboru pro seznam vlastností projektu props.  
  
## <a name="custom-build-rules-and-rules-files"></a>Vytvořit vlastní pravidla a .rules soubory  
 V dřívějších verzích *v souboru pravidel* je soubor formátu XML, který má příponu názvu souboru .rules. Soubor pravidlo umožňuje definovat vlastní pravidla sestavení a zahrnout je do procesu sestavení projektu Visual C++. Vlastní sestavovací pravidlo, které může být přidružený jeden nebo více přípon souborů, umožňuje předat vstupní soubory nástroj, který vytvoří jednu nebo více výstupních souborů.  
  
 V této verzi jsou vlastní pravidla sestavení reprezentována tři typy souborů, XML, props a .targets místo .rules souboru. Při migraci .rules soubor, který byl vytvořen pomocí dřívější verze Visual C++ pro aktuální verzi ekvivalentní soubory .xml, props a .targets vytvářejí a ukládají ve vašem projektu společně s původní soubor .rules.  
  
> [!IMPORTANT]
>  V aktuální verzi [!INCLUDE[TLA2#tla_ide](../build/includes/tla2sharptla_ide_md.md)] nepodporuje vytváření nové pravidel. Z tohoto důvodu je nejjednodušší způsob, jak použít soubor pravidlo z projektu, který byl vytvořen pomocí dřívější verze Visual C++ migrace projektu na aktuální verzi.  
  
## <a name="inheritance-macros"></a>Makra dědičnosti  
 V dřívějších verzích **$(Inherit)** makro určuje pořadí, ve kterém se zobrazují zděděné vlastnosti na příkazovém řádku, které tvoří systém sestavení projektu. **$(NoInherit)** makro způsobí, že všechny výskyty $(Inherit) ignorovat a způsobí, že všechny vlastnosti, které by jinak byly děděny, není byla zděděna. Například ve výchozím nastavení $(Inherit) – makro způsobí, že soubory zadané pomocí [/I (Další adresáře Include)](../build/reference/i-additional-include-directories.md) – možnost kompilátoru který bude přidán do příkazového řádku.  
  
 V aktuální verzi je podporována dědičnost zadáním hodnoty vlastnosti jako zřetězení jednu nebo více literálových hodnot a makra vlastností. **$(Inherit)** a **$(NoInherit)** makra nejsou podporovány.  
  
 V následujícím příkladu je seznam oddělený středníkem přiřadit k vlastnosti na stránce vlastností. V seznamu se skládá z zřetězení  *\<hodnota >* literál a hodnota `MyProperty` vlastnosti, které je přístupné pomocí notace makro, **$(**  *MyProperty***)**.  
  
```  
Property=<value>;$(MyProperty)  
```  
  
## <a name="vcxprojuser-files"></a>. vcxproj.user soubory  
 Soubor uživatele (. vcxproj.user) ukládá vlastnosti specifické pro uživatele, pro příklad, ladění a nasazení nastavení. Soubor vcxproj.user se vztahují na všechny projekty pro určitého uživatele.  
  
## <a name="vcxprojfilters-file"></a>. vcxproj.filters souboru  
 Když **Průzkumníku řešení** se používá k přidání souboru do projektu, soubor filtry (. vcxproj.filters) definuje where v **Průzkumníku řešení** stromové zobrazení, se přidá soubor, na základě jeho přípony názvu souboru.  
  
## <a name="vc-directories-settings"></a>Nastavení adresáře VC ++  
 Nastavení adresáře Visual C++ zadávají se na [stránka vlastností adresářů VC ++](../ide/vcpp-directories-property-page.md). V dřívějších verzích sady Visual Studio adresáře nastavení se vztahuje na uživatele a seznamu vyloučených adresářů je uveden v souboru sysincl.dat.  
  
 Nastavení adresáře VC ++ nelze změnit, pokud spustíte [devenv /resetsettings](/visualstudio/ide/reference/resetsettings-devenv-exe) na příkazovém řádku. Můžete také nelze změnit nastavení, pokud spustíte **nástroje** nabídky, klikněte na tlačítko **nastavení importu a exportu**a pak vyberte **obnovit nastavení** možnost.  
  
 Ze souboru .vssettings, který je vytvořen pomocí dřívější verze Visual C++ při migraci nastavení adresáře VC ++. Otevřete **nástroje** nabídky, klikněte na tlačítko **nastavení importu a exportu**, vyberte **importovat vybrané nastavení prostředí**a pak postupujte podle pokynů v průvodci. Nebo při spuštění sady Visual Studio poprvé, na **zvolte výchozí nastavení prostředí** dialogové okno, vyberte **migraci vhodné nastavení z předchozí verze a použít je kromě výchozí nastavení vybraný níže**.  
  
## <a name="see-also"></a>Viz také  
 [MSBuild (Visual C++)](../build/msbuild-visual-cpp.md)