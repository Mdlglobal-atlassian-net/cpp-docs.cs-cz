---
title: Řešení potíží s izolovanými aplikacemi C/C++ a souběžnými sestaveními
ms.date: 11/04/2016
helpviewer_keywords:
- troubleshooting side-by-side assemblies
- troubleshooting isolated applications
- troubleshooting Visual C++
ms.assetid: 3257257a-1f0b-4ede-8564-9277a7113a35
ms.openlocfilehash: 0dc8488acc90f1a38a4c0de0f052590ef4f398af
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335443"
---
# <a name="troubleshooting-cc-isolated-applications-and-side-by-side-assemblies"></a>Řešení potíží s izolovanými aplikacemi C/C++ a souběžnými sestaveními

Načítání aplikace C/C++ může selhat, pokud nelze najít závislé knihovny. Tento článek popisuje některé běžné důvody, proč se aplikace C/C++ nenačte, a navrhuje kroky k vyřešení problémů.

Pokud se aplikace nenačte, protože má manifest, který určuje závislost na sestavení vedle sebe, a sestavení není nainstalováno jako soukromé sestavení ve stejné složce jako spustitelný soubor ani v nativní mezipaměti sestavení ve složce %WINDIR%\WinSxS\, může se zobrazit jedna z následujících chybových zpráv v závislosti na verzi systému Windows, ve které se pokusíte spustit aplikaci.

- Aplikace se nepodařilo správně inicializovat (0xc0000135).

- Spuštění této aplikace se nezdařilo, protože konfigurace aplikace je nesprávná. Přeinstalování aplikace může tento problém vyřešit.

- Systém nemůže spustit zadaný program.

Pokud vaše aplikace nemá žádný manifest a závisí na dll, že systém Windows nemůže najít v typických umístění vyhledávání, může se zobrazit chybová zpráva, která se podobá této:

- Spuštění této aplikace se nezdařilo, protože *nebyla nalezena požadovaná dll.* Reinstalace aplikace může tento problém vyřešit.

Pokud je vaše aplikace nasazená v počítači, který visual studio nemá, a dojde k chybě s chybovými zprávami, které se podobají předchozím, zkontrolujte tyto věci:

1. Postupujte podle kroků popsaných v [principu závislostí aplikace Visual C++](../windows/understanding-the-dependencies-of-a-visual-cpp-application.md). Objekt pro běhovce závislostí může zobrazit většinu závislostí pro aplikaci nebo dll. Pokud zjistíte, že některé knihovny DLL chybí, nainstalujte je do počítače, ve kterém se pokoušíte spustit aplikaci.

1. Zavaděč operačního systému používá manifest aplikace k načtení sestavení, na kterých aplikace závisí. Manifest může být vložen do binárního souboru jako prostředek nebo nainstalován jako samostatný soubor ve složce aplikace. Chcete-li zkontrolovat, zda je manifest vložen v binárním souboru, otevřete binární soubor v sadě Visual Studio a vyhledejte RT_MANIFEST v seznamu prostředků. Pokud nemůžete najít vložený manifest, vyhledejte ve složce aplikace soubor s názvem něco jako <binary_name>. \<rozšíření>.manifest.

1. Pokud vaše aplikace závisí na sestavení vedle sebe a manifest není k dispozici, je třeba zajistit, že propojovací zařízení generuje manifest pro váš projekt. Zaškrtněte volbu propojovacího zařízení **Generovat manifest** v dialogovém okně **Vlastnosti projektu** pro projekt.

1. Pokud je manifest vložen do binárního souboru, ujistěte se, že ID RT_MANIFEST je správné pro tento typ binárního souboru. Další informace o tom, které ID prostředku použít, naleznete v tématu Použití sestavení vedle [sebe jako prostředku (Windows).](/windows/win32/SbsCs/using-side-by-side-assemblies-as-a-resource) Pokud je manifest v samostatném souboru, otevřete jej v editoru XML nebo textovém editoru. Další informace o manifestech a pravidlech pro nasazení naleznete v [tématu Manifesty](/windows/win32/sbscs/manifests).

   > [!NOTE]
   > Pokud jsou k dispozici vložený manifest i samostatný soubor manifestu, zavaděč operačního systému používá vložený manifest a ignoruje samostatný soubor. V systému Windows XP je však opak pravdou – používá se samostatný soubor manifestu a vložený manifest je ignorován.

1. Doporučujeme vložit manifest do každé dll, protože externí manifesty jsou ignorovány `LoadLibrary` při načtení dll i když volání. Další informace naleznete v tématu [Manifesty sestavení](/windows/win32/SbsCs/assembly-manifests).

1. Zkontrolujte, zda jsou všechna sestavení, která jsou uvedeny v manifestu, správně nainstalována v počítači. Každé sestavení je v manifestu určeno svým názvem, číslem verze a architekturou procesoru. Pokud vaše aplikace závisí na souběžných sestaveních, zkontrolujte, zda jsou tato sestavení správně nainstalována v počítači, aby je zavaděč operačního systému mohl najít, jak je popsáno v [sekvenci hledání sestavení](/windows/win32/SbsCs/assembly-searching-sequence). Mějte na paměti, že 64bitová sestavení nelze načíst v 32bitových procesech a nelze je spustit v 32bitových operačních systémech.

## <a name="example"></a>Příklad

Předpokládejme, že máme aplikaci, appl.exe, která je vytvořena pomocí visual c++. Manifest aplikace je buď vložen do appl.exe jako binární prostředek RT_MANIFEST, který má ID rovnající se 1, nebo je uložen jako samostatný soubor appl.exe.manifest. Obsah tohoto manifestu se podobá toto:

```
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
  <dependency>
    <dependentAssembly>
      <assemblyIdentity type="win32" name="Fabrikam.SxS.Library" version="2.0.20121.0" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"></assemblyIdentity>
    </dependentAssembly>
  </dependency>
</assembly>
```

Pro zavaděč operačního systému tento manifest říká, že appl.exe závisí na sestavení s názvem Fabrikam.SxS.Library, verze 2.0.20121.0, který je vytvořen pro 32bitovou architekturu procesoru x86. Závislé sestavení vedle sebe lze nainstalovat buď jako sdílené sestavení, nebo jako soukromé sestavení.

Manifest sestavení pro sdílené sestavení je nainstalován ve složce %WINDIR%\WinSxS\Manifests\. Identifikuje sestavení a uvádí jeho obsah – to znamená knihovny DLL, které jsou součástí sestavení:

```
<?xml version="1.0" encoding="UTF-8" standalone="yes"?>
<assembly xmlns="urn:schemas-microsoft-com:asm.v1" manifestVersion="1.0">
   <noInheritable/>
   <assemblyIdentity type="win32" name="Fabrikam.SxS.Library" version="2.0.20121.0" processorArchitecture="x86" publicKeyToken="1fc8b3b9a1e18e3e"/>
   <file name="Fabrikam.Main.dll" hash="3ca5156e8212449db6c622c3d10f37d9adb1ab12" hashalg="SHA1"/>
   <file name="Fabrikam.Helper.dll" hash="92cf8a9bb066aea821d324ca4695c69e55b2d1c2" hashalg="SHA1"/>
</assembly>
```

Souběžná sestavení mohou také používat [konfigurační soubory vydavatele](/windows/win32/SbsCs/publisher-configuration-files)– označované také jako soubory zásad – k globálnímu přesměrování aplikací a sestavení tak, aby používaly jednu verzi souběžného sestavení namísto jiné verze stejného sestavení. Zásady sdíleného sestavení můžete zkontrolovat ve složce %WINDIR%\WinSxS\Policies\. Zde je ukázkový soubor zásad:

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

Tento soubor zásad určuje, že všechny aplikace nebo sestavení, které požaduje verzi 2.0.10000.0 tohoto sestavení by měl místo toho použít verzi 2.0.20121.0, což je aktuální verze, která je nainstalována v systému. Pokud je v souboru zásad zadána verze sestavení, která je uvedena v manifestu aplikace, zavaděč hledá verzi tohoto sestavení, která je zadána v manifestu ve složce %WINDIR%\WinSxS\, a pokud tato verze není nainstalována, zatížení se nezdaří. A pokud není nainstalována verze sestavení 2.0.20121.0, zatížení se nezdaří pro aplikace, které žádají o verzi sestavení 2.0.10000.0.

Sestavení však lze také nainstalovat jako soukromé sestavení vedle sebe v nainstalované složce aplikace. Pokud operační systém nenalezne sestavení jako sdílené sestavení, bude ho hledat jako soukromé sestavení v následujícím pořadí:

1. Ve složce aplikace zkontrolujte soubor \<manifestu, který má název assemblyName>.manifest. V tomto příkladu se zavaděč pokusí najít fabrikam.SxS.Library.manifest ve složce, která obsahuje appl.exe. Pokud najde manifest, zavaděč načte sestavení ze složky aplikace. Pokud sestavení není nalezeno, zatížení se nezdaří.

1. Pokuste se \\ otevřít\>složku<assemblyName \ ve složce, \\ která obsahuje\>soubor appl.exe, a pokud \<<assemblyName \ existuje, pokuste se načíst soubor manifestu, který má název assemblyName>.manifest z této složky. Pokud je manifest nalezen, zavaděč \\ načte\>sestavení ze složky<assemblyName \ . Pokud sestavení není nalezeno, zatížení se nezdaří.

Další informace o tom, jak zavaděč vyhledává závislá sestavení, naleznete v [tématu Pořadí hledání sestavení](/windows/win32/SbsCs/assembly-searching-sequence). Pokud zavaděč nenalezne závislé sestavení jako soukromé sestavení, zatížení se nezdaří a zobrazí se zpráva "Systém nemůže spustit zadaný program". Chcete-li tuto chybu vyřešit, ujistěte se, že závislá sestavení a knihovny DLL, které jsou jejich součástí, jsou v počítači nainstalovány jako soukromá nebo sdílená sestavení.

## <a name="see-also"></a>Viz také

[Koncept izolovaných aplikací a souběžných sestavení](concepts-of-isolated-applications-and-side-by-side-assemblies.md)<br/>
[Sestavení izolovaných aplikací C/C++ a souběžných sestavení](building-c-cpp-isolated-applications-and-side-by-side-assemblies.md)
