---
title: Řešení potíží s C/C++ izolované aplikace a sestavení vedle sebe | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- troubleshooting side-by-side assemblies
- troubleshooting isolated applications
- troubleshooting Visual C++
ms.assetid: 3257257a-1f0b-4ede-8564-9277a7113a35
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 56fc61fa7dd7973a6ee1cc4c5a20311bf43b056f
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/14/2018
ms.locfileid: "42465592"
---
# <a name="troubleshooting-cc-isolated-applications-and-side-by-side-assemblies"></a>Řešení potíží s izolovanými aplikacemi C/C++ a souběžnými sestaveními
Načítají se aplikace v jazyce C/C++ může selhat, pokud nelze najít závislé knihovny. Tento článek popisuje některé běžné důvody, proč se aplikace v jazyce C/C++ nepodaří načíst, a navrhne kroky k vyřešení problémů.  
  
 Pokud se aplikaci nepodaří načíst, protože obsahuje manifest, který určuje závislost na sestavení vedle sebe a sestavení není nainstalována jako soukromé sestavení do stejné složky jako spustitelný soubor ani v mezipaměti nativních sestavení ve složce %WINDIR%\WinSxS\ , jeden z následujících chybových zpráv může zobrazit, v závislosti na verzi Windows, na kterém pokusu o spuštění aplikace.  
  
-   Aplikaci se nepodařilo správně inicializovat (0xc0000135).  
  
-   Tuto aplikaci se nepodařilo spustit, protože konfigurace aplikace není správná. Tento problém lze pravděpodobně vyřešit opakovanou instalací aplikace.  
  
-   Systém nemůže spustit určený program.  
  
 Pokud vaše aplikace nemá žádný manifest a závisí na knihovnu DLL, která Windows nelze najít v typickém hledání umístění, může zobrazit chybová zpráva, která se podobá následujícímu:  
  
-   Tuto aplikaci se nepodařilo spustit, protože *požadovanou knihovnu DLL* nebyl nalezen. Potíže pravděpodobně odstraníte opětovnou instalací aplikace.  
  
 Pokud vaše aplikace bude nasazena na počítač, který nemá aplikaci Visual Studio a jeho dojde k chybě s chybovými zprávami, které se podobají předchozích balíčcích, zkontrolujte tyto věci:  
  
1.  Postupujte podle kroků, které jsou popsány v [Principy závislostí v aplikacích Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md). Prohlížeč závislostí můžete zobrazit většina závislosti pro aplikaci nebo knihovny DLL. Pokud zjistíte, že chybí některé knihovny DLL, instalaci na počítač, na které se pokoušíte spustit aplikaci.  
  
2.  Zavaděč operačního systému používá manifestu aplikace se načíst sestavení, na kterých aplikace závisí. Manifest můžete být vloženy do binárního souboru jako prostředek, nebo nainstalovat jako samostatný soubor ve složce aplikace. Pokud chcete zkontrolovat, zda je manifest vložený do binárního souboru, otevřete panel binárního souboru v sadě Visual Studio a hledejte RT_MANIFEST ve svém seznamu zdrojů. Pokud nelze nalézt vložený manifest, podívejte se ve složce aplikace soubor s názvem podobným < binary_name >. \<přípona > .manifest.  
  
3.  Pokud vaše aplikace závisí na sestavení vedle sebe a manifest není k dispozici, budete muset zajistit, aby linker generuje manifest pro váš projekt. Zaškrtnutím možnosti linkeru **generovat manifest** v **vlastnosti projektu** dialogové okno pro projekt.  
  
4.  Pokud je manifest vložený do binárního souboru, ujistěte se, že je pro tento typ binárního souboru správné ID RT_MANIFEST. Další informace o jaký Identifikátor prostředku použít, najdete v části [sestavení vedle sebe jako prostředek (Windows)](http://msdn.microsoft.com/library/windows/desktop/aa376617.aspx). Pokud manifest v samostatném souboru, otevřete ho v textovém editoru nebo editoru XML. Další informace o manifestů a pravidla pro nasazení najdete v tématu [manifesty](http://msdn.microsoft.com/library/aa375365).  
  
    > [!NOTE]
    >  Pokud je manifest vložený a samostatný soubor manifestu, zavaděč operačního systému používá vloženého manifestu a ignoruje samostatný soubor. Windows XP, je však opak true – samostatný soubor manifestu se používá a je ignorován vloženého manifestu.  
  
5.  Doporučujeme Vložit manifest v každou knihovnu DLL, protože externí manifestů jsou ignorovány, pokud ale načtení knihovny DLL `LoadLibrary` volání. Další informace najdete v tématu [sestavení manifesty](http://msdn.microsoft.com/library/aa374219).  
  
6.  Zkontrolujte, že všechna sestavení, které jsou uvedené v manifestu jsou správně nainstalovány v počítači. Každé sestavení je určená v manifestu jeho název, číslo verze a architektura procesoru. Pokud vaše aplikace závisí na sestavení vedle sebe, zkontrolujte, že tato sestavení jsou správně nainstalovány v počítači tak, aby na zavaděči operačního systému najdete, jak je popsáno v [pořadí hledání sestavení](http://msdn.microsoft.com/library/aa374224). Mějte na paměti, že 64bitových sestavení nelze načíst v 32bitové procesy a se nedá spustit na 32bitové operační systémy.  
  
## <a name="example"></a>Příklad  
 Předpokládejme, že máme aplikaci appl.exe, která je vytvořená pomocí jazyka Visual C++. Manifest aplikace buď je vložený v appl.exe RT_MANIFEST, která má ID roven 1, nebo se ukládá jako samostatný soubor appl.exe.manifest binární prostředek. Obsah manifestu vypadá takto:  
  
```  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
  <dependency>  
    <dependentAssembly>  
      <assemblyIdentity type="win32" name="Fabrikam.SxS.Library" version="2.0.20121.0" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"></assemblyIdentity>  
    </dependentAssembly>  
  </dependency>  
</assembly>  
```  
  
 Na zavaděči operačního systému, tento manifest říká, že appl.exe závisí na sestavení s názvem Fabrikam.SxS.Library 2.0.20121.0, verzi, která je vytvořená pro 32bitové x86 architekturu procesoru. Závislé sestavení vedle sebe lze nainstalovat jako sdílená sestavení nebo jako soukromé sestavení.  
  
 Manifest sestavení pro sdílené sestavení je nainstalován ve složce %WINDIR%\WinSxS\Manifests\. Určuje sestavení a uvádí jeho obsah – to znamená, knihovny DLL, které jsou součástí sestavení:  
  
```  
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
   <noInheritable/>  
   <assemblyIdentity type="win32" name="Fabrikam.SxS.Library" version="2.0.20121.0" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"/>  
   <file name="Fabrikam.Main.dll" hash="3ca5156e8212449db6c622c3d10f37d9adb1ab12" hashalg="SHA1"/>  
   <file name="Fabrikam.Helper.dll" hash="92cf8a9bb066aea821d324ca4695c69e55b2d1c2" hashalg="SHA1"/>  
</assembly>  
```  
  
 Můžete také použít sestavení vedle sebe [konfiguračních souborů vydavatele](http://msdn.microsoft.com/library/aa375682)– označované také jako zásady souborů – globálně přesměrování aplikace a sestavení místo jiné verze stejného použít jednu verzi sestavení vedle sebe sestavení. Zásady můžete vyhledat ve složce %WINDIR%\WinSxS\Policies\ sdílené sestavení. Tady je příklad souboru zásad:  
  
```  
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
  
   <assemblyIdentity type="win32-policy" name="policy.2.0.Fabrikam.SxS.Library" version="2.0.20121.0" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"/>  
   <dependency>  
      <dependentAssembly>  
         <assemblyIdentity type="win32" name="Fabrikam.SxS.Library" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"/>  
         <bindingRedirect oldVersion="2.0.10000.0-2.0.20120.99" newVersion="2.0.20121.0"/>  
      </dependentAssembly>  
   </dependency>  
</assembly>  
```  
  
 Tento soubor zásad určuje, zda všechny aplikace nebo sestavení, které vyzve k zadání 2.0.10000.0 verzi tohoto sestavení by měl místo toho používat verze 2.0.20121.0, což je aktuální verze nainstalovaná v systému. Pokud v souboru zásad je zadaná verze sestavení, který je uvedený v manifestu aplikace, zavaděč hledá verzi sestavení, která je určená v manifestu ve složce %WINDIR%\WinSxS\, a pokud není nainstalovaná tato verze, se nezdaří načtení. A pokud není nainstalovaná verze sestavení 2.0.20121.0, u aplikace, které požádat o verzi sestavení 2.0.10000.0 selže zatížení.  
  
 Ale sestavení můžete také nainstalovat jako soukromé sestavení vedle sebe ve složce nainstalované aplikace. Pokud nenajde žádné sestavení jako sdílená sestavení operačního systému, bude vypadat, jako soukromé sestavení, v uvedeném pořadí:  
  
1.  Zkontrolujte, jestli složka aplikace, který má název souboru manifestu \<assemblyName > .manifest. V tomto příkladu se pokusí najít Fabrikam.SxS.Library.manifest ve složce, která obsahuje appl.exe zavaděč. Pokud najde manifest, zavaděč načte sestavení ze složky aplikace. Pokud sestavení není nalezen, zatížení se nezdaří.  
  
2.  Zkuste otevřít \\< assemblyName\>\ složky ve složce, která obsahuje appl.exe, a pokud \\< assemblyName\>\ existuje, pokusí načíst soubor manifestu, který má název \<assemblyName >. manifest z této složky. Pokud je manifest nalezen, zavaděč načte sestavení ze \\< assemblyName\>\ složky. Pokud sestavení není nalezen, zatížení se nezdaří.  
  
 Další informace o jak zavaděč hledá závislá sestavení naleznete v tématu [pořadí hledání sestavení](http://msdn.microsoft.com/library/aa374224). Pokud zavaděč nepodaří najít závislé sestavení jako soukromé sestavení, zatížení se nezdaří a zobrazí se zpráva "systém nemůže spustit určený program". Chcete-li vyřešit tuto chybu, ujistěte se, že závislé sestavení – a knihovny DLL, které jsou součástí je – jsou nainstalovány v počítači jako privátní nebo sdílené sestavení.  
  
## <a name="see-also"></a>Viz také  
 [Koncept izolovaných aplikací a sestavení vedle sebe](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)   
 [Sestavení izolovaných aplikací C/C++ a souběžných sestavení](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)