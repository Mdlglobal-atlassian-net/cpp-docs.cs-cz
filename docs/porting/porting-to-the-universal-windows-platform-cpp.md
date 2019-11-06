---
title: Přenos aplikací do Univerzální platformy Windows (C++)
ms.date: 10/23/2019
ms.assetid: f662d2e4-8940-418d-8109-cb76cb8f8569
ms.openlocfilehash: 9314cb564e792a7d4949d422a3942e9d46a23cb2
ms.sourcegitcommit: 0cfc43f90a6cc8b97b24c42efcf5fb9c18762a42
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/05/2019
ms.locfileid: "73627207"
---
# <a name="porting-to-the-universal-windows-platform-c"></a>Přenos aplikací do Univerzální platformy Windows (C++)

V tomto tématu najdete informace o tom, jak portovat existující C++ kód pro platformu aplikace Windows 10, Univerzální platforma Windows. To, co je určeno výrazem *univerzální* , je, že váš kód může běžet na libovolném zařízení s Windows 10. Vytvoříte jeden projekt a jedno uživatelské rozhraní v jazyce XAML, které funguje dobře na jakémkoli zařízení s Windows 10. Funkce dynamického rozložení v jazyce XAML můžete použít k umožnění uživatelského rozhraní aplikace pro přizpůsobení různých velikostí zobrazení.

Dokumentace ke službě Windows Dev Center obsahuje průvodce pro přenos Windows 8.1ch aplikací do Univerzální platforma Windows. Viz [přesunout z prostředí Windows Runtime 8 na UWP](/windows/uwp/porting/w8x-to-uwp-root). I když se příručka zaměřuje hlavně na C# kód, většina pokynů je platná pro C++. Následující postupy obsahují podrobnější informace. Přečtěte si také téma [Přesun z desktopové aplikace do UWP](/windows/uwp/porting/desktop-to-uwp-migrate).

Toto téma obsahuje následující postupy pro přenos kódu do UWP.

- [Přenos aplikace Windows 8.1 Storu do UWP](#BK_81StoreApp)

- [Portování komponenty modulu runtime Windows 8.1 do UWP](#BK_81Component)

Máte-li klasickou knihovnu DLL klasické pracovní plochy a chcete ji volat z aplikace UWP, můžete to provést také. Pomocí těchto postupů můžete vytvořit vrstvu uživatelského rozhraní UWP pro existující klasickou aplikaci klasické pracovní plochy C++ systému Windows nebo standardní C++ kód pro různé platformy. Viz [Postupy: použití existujícího C++ kódu v aplikaci Univerzální platforma Windows](../porting/how-to-use-existing-cpp-code-in-a-universal-windows-platform-app.md). 

## <a name="BK_81StoreApp"></a>Přenos aplikace Windows 8.1 Storu do UWP

Pokud máte aplikaci Windows 8.1 Store, můžete tento postup použít k tomu, abyste mohli pracovat na UWP a na jakémkoli zařízení s Windows 10.  Je vhodné nejdřív sestavit projekt pomocí sady Visual Studio 2019 jako projektu Windows 8.1, abyste nejdřív vyloučili všechny problémy, které vznikají ve změnách kompilátoru a knihoven. Až to uděláte, existují dva způsoby, jak tuto možnost převést na projekt UWP s Windows 10. Nejjednodušší způsob (jak je vysvětleno v následujícím postupu) je vytvoření univerzálního projektu pro Windows a zkopírování existujícího kódu do něj. Pokud jste používali univerzální projekt pro Windows 8.1 Desktop a Windows 8.1 telefon, bude projekt začínat dvěma různými rozloženími v jazyce XAML, ale končit jedním dynamickým rozložením, které se přizpůsobí velikosti zobrazení.

### <a name="to-port-a-windows-81-store-app-to-the-uwp"></a>Postup při portování aplikace Windows 8.1 Storu do UWP

1. Pokud jste tak ještě neučinili, otevřete projekt aplikace Windows 8.1 v aplikaci Visual Studio 2017 a postupujte podle pokynů pro upgrade souboru projektu.

   V instalačním programu sady **Visual Studio** je nutné nainstalovat nástroje pro Windows 8.1. Pokud tyto nástroje nemáte nainstalované, spusťte instalační program sady **Visual Studio** v okně **programy a funkce** , vyberte možnost **Visual Studio 2017**a v okně Nastavení klikněte na tlačítko **změnit**. Najděte **Windows 8.1 nástroje**, ujistěte se, že je vybraná, a klikněte na **OK**.

1. Otevřete okno **Vlastnosti projektu** a v **C++** části > **Obecné**nastavte sadu **nástrojů platformy** na **v141**, sadu nástrojů sady Visual Studio 2017.

1. Sestavte projekt jako projekt Windows 8.1 a vyřešte všechny chyby sestavení. Jakékoli chyby v této fázi jsou pravděpodobně způsobeny zásadními změnami v nástrojích sestavení a knihovnách. Podrobné vysvětlení změn, které by mohly mít vliv na váš kód, naleznete v tématu [vizuální C++ Změna historie 2003 – 2015](../porting/visual-cpp-change-history-2003-2015.md) .

   Po vyčištění sestavení projektu budete připraveni na port pro univerzální Windows (Windows 10).

1. Vytvořte nový projekt univerzální aplikace pro Windows pomocí prázdné šablony. Je možné, že bude mít stejný název jako váš stávající projekt, i když to uděláte, aby projekty byly v různých adresářích.

1. Zavřete řešení a pak pomocí **Průzkumníka Windows** nebo příkazového řádku zkopírujte soubory kódu (s příponami. cpp,. h a. XAML) z vašeho projektu Windows 8.1 do stejné složky jako soubor projektu (. vcxproj) pro projekt, který jste vytvořili v kroku 1. Nekopírujte soubor Package. appxmanifest, a pokud máte samostatný kód pro Windows 8.1 Desktop a telefon, vyberte jeden z nich pro první port (budete muset udělat nějakou práci později, abyste se přizpůsobili k druhému). Nezapomeňte zkopírovat a podsložkách a jejich obsah. Po zobrazení výzvy vyberte nahrazení všech souborů duplicitními názvy.

1. Znovu otevřete řešení a vyberte možnost **přidat** > **existující položku** z místní nabídky uzlu projektu. Vyberte všechny soubory, které jste zkopírovali, s výjimkou těch, které jsou již součástí projektu.

   Zkontrolujte všechny podsložky a nezapomeňte soubory také přidat.

1. Pokud nepoužíváte stejný název projektu jako původní projekt, otevřete soubor Package. appxmanifest a aktualizujte **vstupní bod** tak, aby odrážel název oboru názvů pro třídu `App`.

   Pole **vstupního bodu** v souboru Package. appxmanifest obsahuje název s oborem pro třídu `App`, která zahrnuje obor názvů obsahující `App` třídy. Při vytváření univerzálního projektu pro Windows je obor názvů nastaven na název projektu. Pokud se liší od toho, co se nachází v souborech, které jste zkopírovali z původního projektu, je nutné aktualizovat jeden nebo druhý, aby se shodovaly.

1. Sestavte projekt a vyřešte všechny chyby sestavení z důvodu průlomových změn mezi různými verzemi Windows SDK.

1. Spusťte projekt na místní ploše. Ověřte, že nedošlo k žádným chybám při nasazení a že rozložení aplikace vypadá jako přiměřené a funguje správně na ploše.

1. Pokud jste měli samostatné soubory kódu a. XAML pro jiné zařízení, například Windows Phone 8,1, Projděte si tento kód a určete, kde se liší od standardního zařízení. Pokud je rozdíl pouze v rozložení, je možné v jazyce XAML použít **správce vizuálního stavu** k přizpůsobení zobrazení v závislosti na velikosti obrazovky. Pro jiné rozdíly můžete v kódu použít oddíly podmínek pomocí následujících příkazů #if.

    ```cpp
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PC_APP)
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PHONE_APP)
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_APP)
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_DESKTOP)
    ```

   Tyto příkazy se vztahují na aplikace pro UWP, aplikace Windows Phone Storu, nebo ani žádná (Klasická plocha Win32). Tato makra jsou k dispozici pouze v Windows SDK 8,1 a novějším, takže pokud váš kód potřebuje kompilovat s dřívějšími verzemi Windows SDK nebo pro jiné platformy než Windows, měli byste také vzít v úvahu případ, že není definován žádný z nich.

1. Spusťte a ladit aplikaci na emulátoru nebo fyzickém zařízení pro každý typ zařízení, které vaše aplikace podporuje. Chcete-li spustit emulátor, je nutné spustit aplikaci Visual Studio na fyzickém počítači, nikoli na virtuálním počítači.

## <a name="BK_81Component"></a>Portování komponenty modulu runtime Windows 8.1 do UWP

Máte-li knihovnu DLL nebo komponentu prostředí Windows Runtime, která již spolupracuje s aplikacemi pro Windows 8.1 Store, můžete pomocí tohoto postupu získat součást nebo knihovnu DLL, které pracují s UWP a Windows 10. Základní procedura slouží k vytvoření nového projektu a zkopírování kódu do něj.

### <a name="to-port-a-windows-81-runtime-component-to-the-uwp"></a>Postup při portování komponenty Windows 8.1 runtime na UWP

1. V dialogovém okně **Nový projekt** v aplikaci Visual Studio 2017 vyhledejte uzel **univerzální pro systém Windows** . Pokud tento uzel nevidíte, nainstalujte nejdřív [sadu Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) . Vyberte šablonu **součásti prostředí Windows Runtime** , zadejte název své komponenty a klikněte na tlačítko **OK** . Název komponenty se použije jako název oboru názvů, takže možná budete chtít použít stejný název jako v oboru názvů Old Projects. To vyžaduje, abyste vytvořili projekt v jiné složce než starou. Pokud zvolíte jiný název, můžete aktualizovat název oboru názvů v generovaných souborech kódu.

1. Zavřete projekt.

1. Zkopírujte všechny soubory kódu (. cpp,. h,. XAML atd.) z vaší Windows 8.1 komponenty do svého nově vytvořeného projektu. Nekopírujte soubor Package. appxmanifest.

1. Sestavujte a vyřešte všechny chyby z důvodu zásadních změn mezi různými verzemi Windows SDK.

## <a name="troubleshooting"></a>Poradce při potížích

Během procesu přenosu kódu do UWP může dojít k různým chybám. Zde jsou některé možné problémy, se kterými se můžete setkat.

### <a name="project-configuration-issues"></a>Problémy s konfigurací projektu

Může se zobrazit chyba:

```Output
could not find assembly 'platform.winmd': please specify the assembly search path using /AI or by setting the LIBPATH environment variable
```

Pokud k tomu dojde, projekt se nevytváří jako univerzální projekt pro Windows. Zkontrolujte soubor projektu a ujistěte se, že obsahuje správné elementy XML, které identifikují projekt jako univerzální projekt pro Windows. By měly být k dispozici následující elementy (číslo verze cílové platformy se může lišit):

```xml
<AppContainerApplication>true</AppContainerApplication>
<ApplicationType>Windows Store</ApplicationType>
<WindowsTargetPlatformVersion>10.0.10156.0</WindowsTargetPlatformVersion>
<WindowsTargetPlatformMinVersion>10.0.10156.0</WindowsTargetPlatformMinVersion>
<ApplicationTypeRevision>10.0</ApplicationTypeRevision>
```

Pokud jste vytvořili nový projekt UWP pomocí sady Visual Studio, tuto chybu byste neměli vidět.

## <a name="see-also"></a>Viz také:

[Průvodce C++ přenosem vizuálů](../porting/porting-to-the-universal-windows-platform-cpp.md)<br/>
[Vývoj aplikací pro Univerzální platformu Windows (UWP)](/visualstudio/cross-platform/develop-apps-for-the-universal-windows-platform-uwp)