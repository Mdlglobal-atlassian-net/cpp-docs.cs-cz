---
title: Přenos aplikací do Univerzální platformy Windows (C++)
ms.date: 11/04/2016
ms.assetid: f662d2e4-8940-418d-8109-cb76cb8f8569
ms.openlocfilehash: 83af480dc2a2fdd5ccd15de8a9f62aacebcf4558
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50640411"
---
# <a name="porting-to-the-universal-windows-platform-c"></a>Přenos aplikací do Univerzální platformy Windows (C++)

V tomto tématu najdete informace o tom, jak portujete existující kód C++ do aplikace platformy Windows 10 univerzální platformu Windows. Co znamená pojem termín *univerzální* je, že váš kód můžete spustit na zařízeních s Windows 10 desktop, telefon, tablety i budoucí zařízení se systémem Windows 10. Vytvořit jeden projekt a jednu základní třídu XAML uživatelské rozhraní, funguje dobře na libovolném zařízení, na kterém běží Windows 10. Dynamické rozložení funkcí v XAML můžete povolit Uživatelském rozhraní aplikace umožní reagovat na různé velikosti zobrazení.

Dokumentace ke službě Windows Dev Center obsahuje pokyny pro přenesení aplikací Windows 8.1 pro univerzální platformu Windows. Zobrazit [přesunout z modulu Runtime Windows 8 na UPW](/windows/uwp/porting/w8x-to-uwp-root). I když v průvodci, zaměřuje hlavně na kód jazyka C#, většina návod se vztahuje na C++. Následující postupy obsahují podrobnější informace.

Toto téma obsahuje následující postupy pro přenos kódu pro UPW.

- [Přenesení aplikace pro UPW s Windows 8.1 Store](#BK_81StoreApp)

- [Portování součásti modulu Runtime Windows 8.1 na UPW.](#BK_81Component)

Pokud máte knihovnu DLL Win32 klasické plochy a chcete ji volat z aplikace pro UPW, Uděláte to také. Pomocí těchto postupů můžete vytvořit vrstvu UPW uživatelské rozhraní pro existující desktopu klasické Windows C++ aplikace nebo kódu C++ standard pro různé platformy. Zobrazit [postupy: použití existujícího kódu C++ v aplikaci pro Universal Windows Platform](../porting/how-to-use-existing-cpp-code-in-a-universal-windows-platform-app.md).

## <a name="BK_81StoreApp"></a> Přenesení aplikace pro UPW s Windows 8.1 Store

Pokud máte aplikaci Windows 8.1 Store, můžete použít tento postup její práce na UPW a zařízení se systémem Windows 10.  Je vhodné prvním sestavení projektu sady Visual Studio 2017 jako projekt Windows 8.1, nejdřív odstranit všechny problémy, které vznikají ze změn v kompilátoru a knihovny. Po, který jste provedli, existují dva způsoby, jak převést na projekt Windows 10 UPW. Nejjednodušší způsob (jak je popsáno v následujícím postupu) je vytvoření projektu univerzální Windows a do něj zkopírovat existující kód. Pokud jste používali univerzální projekt pro stolní počítače Windows 8.1 a Windows 8.1 telefon, váš projekt bude začínat dvě různá rozložení v XAML, ale koncové pomocí jediného dynamického rozložení, která upraví velikost zobrazení.

### <a name="to-port-a-windows-81-store-app-to-the-uwp"></a>Na port na Windows 8.1 Store aplikaci pro UPW

1. Pokud jste tak již neučinili, otevřete projekt aplikace Windows 8.1 v sadě Visual Studio 2017 a postupujte podle pokynů pro upgrade souboru projektu.

   Potřebujete mít nainstalovaný **Windows 8.1 nástrojů v sadě Visual Studio** instalační program. Pokud nemáte nainstalované tyto nástroje, začněte **sady Visual Studio** nastavení z **programy a funkce** okně zvolte **Visual Studio 2017**a v okně Nastavení vyberte **Upravit**. Vyhledejte **Windows 8.1 nástrojů**, ujistěte se, že je vybraná a zvolte **OK**.

2. Otevřít **vlastnosti projektu** okna a v části **C++** > **Obecné**, nastavte **sada nástrojů platformy** k **v141**, sada nástrojů pro Visual Studio 2017.

3. Sestavit projekt jako projekt Windows 8.1 a vyřešte všechny chyby sestavení. Všechny chyby v této fázi jsou pravděpodobně způsobené rozbíjející změny v knihoven a nástrojů sestavení. Zobrazit [změn Visual C++ 2003 – 2015 historie](../porting/visual-cpp-change-history-2003-2015.md) podrobné vysvětlení změny, které by mohly ovlivnit váš kód.

   Jakmile se váš projekt se sestaví čistě, jste připraveni k portu pro Universal Windows (Windows 10).

4. Vytvořte nový projekt univerzální aplikace pro Windows pomocí prázdné šablony. Můžete chtít poskytnout, je stejný název jako existující projekt, i když k tomu projekty musí být v různých adresářích.

5. Zavřete řešení a následným použitím **Windows Explorer** nebo příkazového řádku, zkopírujte soubory kódu (pomocí rozšíření .cpp, hlaviček a .xaml) z vaší Windows 8.1 projekt do stejné složky jako soubor projektu (.vcxproj) pro projekt vytvořili v kroku 1. Nekopírujte soubor Package.appxmanifest a pokud máte samostatného kódu pro počítače s Windows 8.1 a pro telefony, zvolte jeden z nich k portu první (budete muset provést některé práce později k přizpůsobení do jiné). Nezapomeňte si zkopírujte a podsložky a jejich obsah. Pokud se zobrazí výzva, zvolte Nahradit všechny soubory s duplicitními názvy.

6. Znovu otevřete řešení a zvolte **přidat** > **existující položku** z místní nabídku pro uzel projektu. Vyberte všechny soubory, které jste zkopírovali, s výjimkou těch, které jsou již součástí projektu.

   Zkontrolujte všechny podsložky a ujistěte se, že přidáte soubory v nich také.

7. Pokud nepoužíváte stejného názvu projektu jako původní projekt, otevřete soubor Package.appxmanifest a aktualizace **vstupní bod** tak, aby odrážely název oboru názvů `App` třídy.

   **Vstupní bod** pole v Package.appxmanifest souboru obsahuje název oboru `App` třída, která obsahuje obor názvů obsahující `App` třídy. Při vytváření projektu Universal Windows, obor názvů je nastavena na název projektu. Pokud to není totéž co je v souborech, které jste si zkopírovali v z původního projektu, je nutné aktualizovat jeden z nich, aby odpovídaly.

8. Sestavte projekt a řešení případných chyb sestavení z důvodu rozbíjející změny mezi různými verzemi nástroje sady Windows SDK.

9. Spusťte projekt na místní pracovní plocha. Ověřte, že neexistují žádné chyby během nasazení a že rozložení aplikace vypadá přiměřené a, že funguje správně v klientských počítačích.

10. Pokud máte soubory samostatného kódu a .xaml pro jiné zařízení, jako jsou Windows Phone 8.1, tento kód zkontrolovat a určit, kde se liší od standardní zařízení. Pokud rozdíl je pouze v rozložení, je možné použít **Visual State Managerem** v jazyce xaml pro přizpůsobení zobrazení v závislosti na velikosti obrazovky. Pro další rozdíly můžete použít části podmínky v kódu pomocí následujících příkazů #if.

    ```cpp
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PC_APP)
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PHONE_APP)
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_APP)
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_DESKTOP)
    ```

   Tyto příkazy v uvedeném pořadí se vztahují na aplikacích pro UPW, Windows Phone Store aplikace, obou nebo ani jedna (classic Win32 jenom desktopové verze). Tato makra jsou k dispozici pouze ve Windows SDK 8.1 a novější, takže pokud váš kód musí být možné zkompilovat pomocí předchozích verzí sady Windows SDK nebo pro jiné platformy kromě Windows, pak byste měli také zvážit případě že žádný z nich jsou definovány.

11. Spustit a ladit aplikace na emulátoru nebo fyzické zařízení, pro každý typ zařízení, které vaše aplikace podporuje. Pro spuštění emulátoru, musíte spustit aplikaci Visual Studio na fyzickém počítači, ne virtuální počítač.

## <a name="BK_81Component"></a> Portování součásti modulu Runtime Windows 8.1 na UPW.

Pokud máte knihovnu DLL nebo komponenty Windows Runtime, která už funguje s aplikacemi pro Windows 8.1 Store, můžete tento postup komponenty a knihovny DLL práce s Windows 10 a UPW. Základní postup se týká vytvoření nového projektu a do něj zkopírovat požadovaný kód.

### <a name="to-port-a-windows-81-runtime-component-to-the-uwp"></a>Port součásti modulu Runtime Windows 8.1 na UPW.

1. V **nový projekt** dialogového okna v sadě Visual Studio 2017, vyhledejte **Windows Universal** uzlu. Pokud nevidíte tento uzel, nainstalujte [nástroje pro Windows 10](http://go.microsoft.com/fwlink/p/?LinkID=617903) první. Zvolte **součást prostředí Windows Runtime** šablony, zadejte název pro komponentu a vyberte **OK** tlačítko. Název komponenty se použije jako název oboru názvů, takže můžete chtít použít stejný název jako vaše staré projekty obor názvů. To je potřeba, abyste vytvořili projekt v jiné složce než ten starý. Pokud zvolíte jiný název, můžete aktualizovat název oboru názvů v souboru generovaného kódu.

2. Zavřete projekt.

3. Zkopírujte všechny soubory kódu (.cpp, .h, .xaml atd.) z vaší komponentě Windows 8.1 do nově vytvořeného projektu. Nekopírovat soubor Package.appxmanifest.

4. Sestavení a vyřešte případné chyby z důvodu rozbíjející změny mezi různými verzemi nástroje sady Windows SDK.

## <a name="troubleshooting"></a>Poradce při potížích

Mohou se vyskytnout různé chyby během portování kódu pro UPW. Tady jsou některé z možných problémech, ke kterým může dojít.

### <a name="project-configuration-issues"></a>Problémy s konfigurací projektu

Může dojít k chybě:

```Output
could not find assembly 'platform.winmd': please specify the assembly search path using /AI or by setting the LIBPATH environment variable
```

V takovém případě není jako Windows Universal project vytváření projektu. Zkontrolujte soubor projektu a ujistěte se, že má správné elementy XML, které určují projekt jako projekt Windows Universal. Následující elementy musí být k dispozici (číslo verze cílové platformy může lišit):

```xml
<AppContainerApplication>true</AppContainerApplication>
<ApplicationType>Windows Store</ApplicationType>
<WindowsTargetPlatformVersion>10.0.10156.0</WindowsTargetPlatformVersion>
<WindowsTargetPlatformMinVersion>10.0.10156.0</WindowsTargetPlatformMinVersion>
<ApplicationTypeRevision>10.0</ApplicationTypeRevision>
```

Pokud jste vytvořili nový projekt UPW pomocí sady Visual Studio, byste neměli vidět tuto chybu.

## <a name="see-also"></a>Viz také:

[Portování průvodce Visual C++](../porting/porting-to-the-universal-windows-platform-cpp.md)<br/>
[Vývoj aplikací pro Univerzální platformu Windows (UWP)](/visualstudio/cross-platform/develop-apps-for-the-universal-windows-platform-uwp)