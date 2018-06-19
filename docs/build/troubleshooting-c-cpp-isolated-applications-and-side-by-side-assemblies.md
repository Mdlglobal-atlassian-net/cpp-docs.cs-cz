---
title: Řešení potíží s C/C++ izolované aplikace a souběžně sdílená sestavení | Microsoft Docs
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
ms.openlocfilehash: 6f5645270cbc8fbb71dd841cb4f1affa6bef1295
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32390688"
---
# <a name="troubleshooting-cc-isolated-applications-and-side-by-side-assemblies"></a>Řešení potíží s izolovanými aplikacemi C/C++ a souběžnými sestaveními
Načítání aplikace C/C++ může selhat, pokud nelze nalézt závislé knihovny. Tento článek popisuje některé běžné příčiny, proč aplikace C/C++ nepodaří načíst, a navrhne postup řešení problémů.  
  
 Pokud se nepodaří načíst, protože má manifestu, který určuje závislost na souběžně sdílená sestavení aplikace a sestavení není nainstalována jako privátní sestavení ve stejné složce jako spustitelný soubor ani v mezipaměti nativní sestavení ve složce %WINDIR%\WinSxS\ , jednu z následujících chybových zpráv mohou být zobrazeny, v závislosti na verzi Windows, na kterém pokusu o spuštění aplikace.  
  
-   Aplikace se nepodařilo správně inicializovat (0xc0000135).  
  
-   Tuto aplikaci se nepodařilo spustit, protože konfigurace aplikace je nesprávný. Opětovné instalaci aplikace, může tento problém vyřešit.  
  
-   Systém nemůže zadaný program spustit.  
  
 Pokud aplikace nemá žádné manifest a závisí na knihovnu DLL, kterou systém Windows nemůže najít v typické vyhledávací umístěních, může zobrazit chybová zpráva, která se podobá následujícímu:  
  
-   Tuto aplikaci se nepodařilo spustit, protože *požadované knihovny DLL* nebyl nalezen. Opětovné instalaci aplikace, může tento problém vyřešit.  
  
 Pokud vaše aplikace je nasazená na počítači, který nemá Visual Studio a dojde k chybě, a s chybové zprávy, které se podobají předchozím, zkontrolujte tyto věci:  
  
1.  Postupujte podle kroků popsaných v [Principy závislostí aplikace Visual C++](../ide/understanding-the-dependencies-of-a-visual-cpp-application.md). Walkera závislostí můžete zobrazit většinu závislosti pro aplikaci nebo DLL. Pokud zjistíte, že chybí některé knihovny DLL, nainstalujte je v počítači, na který se pokoušíte spustit svoji aplikaci.  
  
2.  Zavaděč operačního systému používá k načtení sestavení, které závisí aplikace na manifest aplikace. Manifest můžete být vložené do binárního souboru jako prostředek, nebo nainstalovat jako samostatný soubor ve složce aplikace. Chcete-li zkontrolovat, zda manifest vložené do binárního souboru, otevřete binárního souboru v [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] a vyhledejte RT_MANIFEST ve svém seznamu prostředků. Pokud nemůžete najít vložený manifest, vyhledejte ve složce aplikace pro soubor, který má název něco podobného jako < binary_name >. \<rozšíření > manifest.  
  
3.  Pokud vaše aplikace závisí na souběžně sdílená sestavení a manifestu není k dispozici, budete muset zajistit, že linkeru generuje manifest pro váš projekt. Zkontrolujte možnosti linkeru **generování manifestu** v **vlastnosti projektu** dialogové okno pro projekt.  
  
4.  Pokud v manifestu je vložen do binárního souboru, zkontrolujte správnost ID RT_MANIFEST pro tento typ binárního souboru. Další informace o které ID prostředku použít, najdete v části [pomocí souběžně sdílená sestavení jako prostředek (Windows)](http://msdn.microsoft.com/library/windows/desktop/aa376617.aspx). Manifest je v samostatném souboru, otevřete ho v editoru XML nebo textovém editoru. Další informace o manifesty a pravidla pro nasazení najdete v tématu [manifesty](http://msdn.microsoft.com/library/aa375365).  
  
    > [!NOTE]
    >  Pokud je přítomen vložený manifest i samostatný soubor manifestu, zavaděč operačního systému používá vložený manifest a ignoruje samostatný soubor. V systému Windows XP, je však jako opak true – samostatný soubor manifestu se používá a vložený manifest je ignorována.  
  
5.  Doporučujeme, abyste vložení manifestu v každou knihovnu DLL, protože externí manifesty ignorují při ale načtení knihovny DLL `LoadLibrary` volání. Další informace najdete v tématu [manifesty sestavení](http://msdn.microsoft.com/library/aa374219).  
  
6.  Zkontrolujte, zda jsou všechny sestavení, které jsou uvedené v manifestu správně nainstalován v počítači. Každé sestavení je zadána v manifestu jeho název, číslo verze a architekturu procesoru. Pokud je aplikace závislá na souběžně sdílená sestavení, zkontrolujte, že tyto sestavení správně nainstalovaná na počítači, aby mohli najít zavaděč operačního systému, je, jak je popsáno v [pořadí hledání sestavení](http://msdn.microsoft.com/library/aa374224). Mějte na paměti, že 64-bit sestavení nelze načíst v 32bitovými procesy a se nedá spustit na 32bitové operační systémy.  
  
## <a name="example"></a>Příklad  
 Předpokládejme, že jsme aplikaci, appl.exe, vytvořené pomocí aplikace Visual C++. Manifest aplikace buď vložené do appl.exe jako binárního prostředku RT_MANIFEST má ID rovnající se 1, který je uložený jako samostatný soubor appl.exe.manifest. Obsah této manifest vypadá takto:  
  
```  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
  <dependency>  
    <dependentAssembly>  
      <assemblyIdentity type="win32" name="Fabrikam.SxS.Library" version="2.0.20121.0" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"></assemblyIdentity>  
    </dependentAssembly>  
  </dependency>  
</assembly>  
```  
  
 K zavaděč operačního systému, tento manifest říká, že appl.exe závisí na sestavení s názvem Fabrikam.SxS.Library, verze 2.0.20121.0, vytvořené pro 32-bit x86 architekturu procesoru. Závislé souběžně sdílená sestavení lze nainstalovat jako sdílené sestavení nebo jako privátní sestavení.  
  
 Manifest sestavení pro sdílené sestavení je nainstalován ve složce %WINDIR%\WinSxS\Manifests\. Identifikuje sestavení a uvádí obsah – to znamená, knihovny DLL, které jsou součástí sestavení:  
  
```  
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>  
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">  
   <noInheritable/>  
   <assemblyIdentity type="win32" name="Fabrikam.SxS.Library" version="2.0.20121.0" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"/>  
   <file name="Fabrikam.Main.dll" hash="3ca5156e8212449db6c622c3d10f37d9adb1ab12" hashalg="SHA1"/>  
   <file name="Fabrikam.Helper.dll" hash="92cf8a9bb066aea821d324ca4695c69e55b2d1c2" hashalg="SHA1"/>  
</assembly>  
```  
  
 Souběžně sdílená sestavení můžete také použít [vydavatele konfigurační soubory](http://msdn.microsoft.com/library/aa375682)– taky známé jako soubory zásad – globálně přesměrovat na použití jedné verze souběžně sdílená sestavení místo jinou verzi aplikace stejná aplikace a sestavení sestavení. Zásady můžete zkontrolovat pro sdílené sestavení ve složce %WINDIR%\WinSxS\Policies\. Tady je příklad souboru zásad:  
  
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
  
 Tento soubor zásad určuje, že všechny aplikace nebo sestavení, která požaduje zadání 2.0.10000.0 verzi toto sestavení místo toho použijte verzi 2.0.20121.0, která je aktuální verze, která je nainstalovaná v systému. Pokud je verze sestavení, které je uvedené v manifestu aplikace zadané v souboru zásad, zavaděč hledá verzi toto sestavení, který je uveden v manifestu ve složce %WINDIR%\WinSxS\ a pokud tato verze není nainstalovaná, zatížení selže. A pokud není nainstalovaná verze sestavení 2.0.20121.0, pro aplikace, které požádat o verzi sestavení 2.0.10000.0 selže zatížení.  
  
 Jako privátní souběžně sdílená sestavení ve složce nainstalované aplikace však lze také nainstalovat sestavení. Pokud se operační systém se nepodaří najít sestavení jako sdílené sestavení, hledá se pro něj jako privátní sestavení, v uvedeném pořadí:  
  
1.  Zkontrolujte ve složce aplikace pro soubor manifestu, který má název \<assemblyName > manifest. V tomto příkladu se pokusí najít Fabrikam.SxS.Library.manifest ve složce, která obsahuje appl.exe zavaděč. Pokud najde manifest, načte sestavení ve složce aplikace. Pokud není nalezen sestavení, zatížení se nezdaří.  
  
2.  Pokusí otevřít \\< assemblyName\>\ složky ve složce, která obsahuje appl.exe, a pokud \\< assemblyName\>\ existuje, pokusí se načíst soubor manifestu, který má název \<assemblyName >. manifest z této složky. Pokud je nalezen manifest, načte sestavení z \\< assemblyName\>\ složky. Pokud není nalezen sestavení, zatížení se nezdaří.  
  
 Další informace o způsobu zavaděč vyhledává závislé sestavení najdete v tématu [pořadí hledání sestavení](http://msdn.microsoft.com/library/aa374224). Pokud zavaděč nepodaří najít závislé sestavení jako privátní sestavení, zatížení nezdaří a zobrazí se zpráva "systém nemůže spustit zadaný program". Pokud chcete tuto chybu vyřešit, ujistěte se, že závislé sestavení – a knihovny DLL, které jsou součástí je – jsou nainstalovány v počítači jako privátní nebo sdílená sestavení.  
  
## <a name="see-also"></a>Viz také  
 [Koncepty izolovaných aplikací a souběžně sdílená sestavení](../build/concepts-of-isolated-applications-and-side-by-side-assemblies.md)   
 [Sestavení izolovaných aplikací C/C++ a souběžných sestavení](../build/building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)