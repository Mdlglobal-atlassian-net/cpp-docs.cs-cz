---
title: Řešení potíží s izolovanými aplikacemi C/C++ a souběžnými sestaveními
ms.date: 11/04/2016
helpviewer_keywords:
- troubleshooting side-by-side assemblies
- troubleshooting isolated applications
- troubleshooting Visual C++
ms.assetid: 3257257a-1f0b-4ede-8564-9277a7113a35
ms.openlocfilehash: 1bd0d7638a8e7f2e3c671229e1f8d118d681e6f4
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492579"
---
# <a name="troubleshooting-cc-isolated-applications-and-side-by-side-assemblies"></a>Řešení potíží s izolovanými aplikacemi C/C++ a souběžnými sestaveními

Načtení C/C++ aplikace může selhat, pokud nelze najít závislé knihovny. Tento článek popisuje některé běžné důvody, proč se nepodařiloC++ načíst aplikaci C/a navrhuje kroky k vyřešení těchto problémů.

Pokud se aplikace nenačte, protože má manifest, který určuje závislost na souběžném sestavení, a sestavení není nainstalováno jako soukromé sestavení ve stejné složce jako spustitelný soubor, ani v nativní mezipaměti sestavení ve složce%WINDIR%\WinSxS\ , může se zobrazit jedna z následujících chybových zpráv v závislosti na verzi systému Windows, na které se pokoušíte spustit aplikaci.

- Aplikaci se nepovedlo správně inicializovat (0xc0000135).

- Tuto aplikaci se nepovedlo spustit, protože konfigurace aplikace není správná. Tento problém může vyřešit opětovná instalace aplikace.

- Systém nemůže spustit určený program.

Pokud vaše aplikace nemá žádný manifest a závisí na knihovně DLL, kterou systém Windows nemůže najít v typických umístěních hledání, může se zobrazit chybová zpráva, která je podobná této:

- Tuto aplikaci se nepovedlo spustit, protože se nenašla *požadovaná knihovna DLL* . Tento problém může vyřešit Opakovaná instalace aplikace.

Pokud je vaše aplikace nasazená na počítači, který nemá aplikaci Visual Studio, a dojde k jejímu selhání s chybovými zprávami, které se podobají předchozím těm, podívejte se na tyto věci:

1. Postupujte podle kroků popsaných v tématu [Principy závislostí vizuální C++ aplikace](../windows/understanding-the-dependencies-of-a-visual-cpp-application.md). Prohlížeč závislostí může zobrazit většinu závislostí pro aplikaci nebo knihovnu DLL. Pokud zjistíte, že některé knihovny dll chybějí, nainstalujte je do počítače, na kterém se pokoušíte spustit aplikaci.

1. Zavaděč operačního systému používá manifest aplikace k načtení sestavení, na kterých aplikace závisí. Manifest může být buď vložen do binárního souboru jako prostředek, nebo nainstalován jako samostatný soubor ve složce aplikace. Chcete-li zkontrolovat, zda je manifest vložen do binárního souboru, otevřete binární soubor v aplikaci Visual Studio a vyhledejte RT_MANIFEST v seznamu prostředků. Pokud vložený manifest nemůžete najít, vyhledejte ve složce aplikace soubor s názvem něco jako < binary_name >. \<přípona >. manifest.

1. Pokud vaše aplikace závisí na souběžných sestaveních a manifest není k dispozici, je nutné zajistit, aby linker vygeneroval manifest pro váš projekt. Zaškrtněte možnost linkeru **Generovat Manifest** v dialogovém okně **Vlastnosti projektu** projektu.

1. Pokud je manifest vložen do binárního souboru, ujistěte se, že ID RT_MANIFEST je pro tento typ binárního souboru správné. Další informace o tom, jaké ID prostředku použít, naleznete v tématu [použití souběžných sestavení jako prostředku (Windows)](/windows/win32/SbsCs/using-side-by-side-assemblies-as-a-resource). Pokud je manifest v samostatném souboru, otevřete jej v editoru XML nebo textovém editoru. Další informace o manifestech a pravidlech pro nasazení naleznete v tématu [manifesty](/windows/win32/sbscs/manifests).

   > [!NOTE]
   > Pokud je přítomen vložený manifest i samostatný soubor manifestu, zavaděč operačního systému použije vložený manifest a ignoruje samostatný soubor. V systému Windows XP je však opak true – použije se samostatný soubor manifestu a vložený manifest se ignoruje.

1. Doporučujeme, abyste vložili manifest do každé knihovny DLL, protože externí manifesty jsou ignorovány, když je knihovna DLL `LoadLibrary` načtena v případě volání. Další informace naleznete v tématu [manifesty sestavení](/windows/win32/SbsCs/assembly-manifests).

1. Ověřte, zda jsou všechna sestavení výčtu v manifestu správně nainstalována v počítači. Každé sestavení je zadáno v manifestu podle jeho názvu, čísla verze a architektury procesoru. Pokud vaše aplikace závisí na souběžných sestaveních, ověřte, zda jsou tato sestavení správně nainstalována v počítači, aby je mohl zavaděč operačního systému najít, jak je popsáno v tématu [pořadí vyhledávání sestavení](/windows/win32/SbsCs/assembly-searching-sequence). Nezapomeňte, že 64 sestavení nelze načíst v 32ch procesech a nelze je spustit v operačních systémech s 32-bit.

## <a name="example"></a>Příklad

Předpokládejme, že máme aplikaci, soubor. exe, která je sestavená pomocí vizuálu C++. Manifest aplikace buď je vložen do souboru Application. exe jako binární RT_MANIFEST prostředku, který má ID rovnající se 1 nebo je uložen jako samostatný soubor. exe. manifest. Obsah tohoto manifestu se podobá tomuto:

```
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
  <dependency>
    <dependentAssembly>
      <assemblyIdentity type="win32" name="Fabrikam.SxS.Library" version="2.0.20121.0" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"></assemblyIdentity>
    </dependentAssembly>
  </dependency>
</assembly>
```

Do zavaděče operačního systému tento manifest říká, že soubor doplňku. exe závisí na sestavení s názvem Fabrikam. SxS. Library verze 2.0.20121.0, který je sestaven pro architekturu 32 procesorů x86. Závislé souběžné sestavení lze nainstalovat buď jako sdílené sestavení, nebo jako soukromé sestavení.

Manifest sestavení pro sdílené sestavení je nainstalován ve složce%WINDIR%\WinSxS\Manifests\. Identifikuje sestavení a zobrazí jeho obsah, tedy knihovny DLL, které jsou součástí sestavení:

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
   <noInheritable/>
   <assemblyIdentity type="win32" name="Fabrikam.SxS.Library" version="2.0.20121.0" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"/>
   <file name="Fabrikam.Main.dll" hash="3ca5156e8212449db6c622c3d10f37d9adb1ab12" hashalg="SHA1"/>
   <file name="Fabrikam.Helper.dll" hash="92cf8a9bb066aea821d324ca4695c69e55b2d1c2" hashalg="SHA1"/>
</assembly>
```

Souběžná sestavení mohou také používat [konfigurační soubory vydavatele](/windows/win32/SbsCs/publisher-configuration-files)(označované také jako soubory zásad) k globálně přesměrovat aplikace a sestavení tak, aby používaly jednu verzi souběžného sestavení namísto jiné verze stejného sestavení. Zásady sdíleného sestavení můžete vyhledat ve složce%WINDIR%\WinSxS\Policies\. Tady je příklad souboru zásad:

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

Tento soubor zásad určuje, že jakákoli aplikace nebo sestavení požadující 2.0.10000.0 verze tohoto sestavení by měly místo toho používat verzi 2.0.20121.0, což je aktuální verze, která je v systému nainstalovaná. Pokud je verze sestavení, která je uvedena v manifestu aplikace, uvedena v souboru zásad, zavaděč vyhledá verzi tohoto sestavení, která je zadána v manifestu ve složce%WINDIR%\WinSxS\, a pokud není tato verze nainstalovaná, načtení se nepovede. A pokud není nainstalovaná verze sestavení 2.0.20121.0, načítání se u aplikací, které žádají o sestavení verze 2.0.10000.0, nezdařil.

Nicméně sestavení lze také nainstalovat do složky nainstalované aplikace jako soukromé sestavení souběžného sestavení. Pokud operační systém nenajde sestavení jako sdílené sestavení, vyhledá ho jako soukromé sestavení v následujícím pořadí:

1. Ve složce aplikace vyhledejte soubor manifestu s názvem \<AssemblyName >. manifest. V tomto příkladu se zavaděč pokusí najít Fabrikam. SxS. Library. manifest ve složce, která obsahuje soubor. exe. Pokud najde manifest, zavaděč načte sestavení ze složky aplikace. Pokud sestavení není nalezeno, načtení se nepovede.

1. Zkuste \\otevřít složku < AssemblyName \\\>\ ve složce, která obsahuje soubor. exe, a pokud < AssemblyName\>\ existuje, zkuste načíst soubor manifestu s názvem \<AssemblyName >. manifest z této složky. Pokud je manifest nalezen, zavaděč načte sestavení ze \\složky < AssemblyName\>\. Pokud sestavení není nalezeno, načtení se nepovede.

Další informace o tom, jak zavaděč vyhledává závislá sestavení, naleznete v tématu [pořadí vyhledávání sestavení](/windows/win32/SbsCs/assembly-searching-sequence). Pokud zavaděč nenajde závislé sestavení jako soukromé sestavení, načtení se nepodaří a zobrazí se zpráva "systém nemůže spustit zadaný program". Chcete-li tuto chybu vyřešit, zajistěte, aby závislá sestavení – a knihovny DLL, které jsou součástí nich, byly nainstalovány v počítači jako soukromá nebo sdílená sestavení.

## <a name="see-also"></a>Viz také:

[Koncept izolovaných aplikací a souběžných sestavení](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[Sestavení izolovaných aplikací C/C++ a souběžných sestavení](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
