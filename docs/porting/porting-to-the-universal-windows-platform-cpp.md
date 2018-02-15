---
title: "Přenos aplikací do univerzální platformy Windows (C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
ms.assetid: f662d2e4-8940-418d-8109-cb76cb8f8569
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2ece050614481bdc0adbe417448711376666b2b9
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2018
---
# <a name="porting-to-the-universal-windows-platform-c"></a>Přenos aplikací do Univerzální platformy Windows (C++)
V tomto tématu najdete informace o tom, jak portu existujícího kódu C++ pro aplikace platformy Windows 10, univerzální platformu Windows. Pojmy termín *universal* je, že váš kód můžete spustit u zařízení se systémem Windows 10, včetně stolní počítače, telefon, tablety a budoucí zařízení se systémem Windows 10. Vytvoříte projekt a jeden XAML základní uživatelské rozhraní, které funguje dobře na jakémkoli zařízení se systémem Windows 10. Dynamické rozložení funkce můžete v jazyce XAML umožňující uživatelském rozhraní aplikace se různé velikosti zobrazení přizpůsobit.  
  
 V dokumentaci k centru vývojářů pro Windows obsahuje Průvodce pro přenos aplikace Windows 8.1 pro univerzální platformu Windows. V tématu [přesunout z prostředí Windows Runtime 8 do UWP](https://msdn.microsoft.com/windows/uwp/porting/w8x-to-uwp-root). I když v Průvodci zaměřuje především na kód C#, se vztahuje na C++ většinu pokyny. Následující postupy obsahují podrobnější informace.  
  
 Toto téma obsahuje následující postupy pro přenos kódu UWP.  
  
1.  [Portování aplikací Windows 8.1 Store, aby UWP](#BK_81StoreApp)  
  
2.  [Portování součásti modulu Runtime Windows 8.1 do UWP](#BK_81Component)  
  
 Pokud máte klasické pracovní plochy Win32 knihovny DLL a chcete volat z aplikace UPW, můžete to udělat i. Pomocí těchto postupů, můžete vytvořit vrstvu UWP uživatelské rozhraní pro existující classic Windows desktop aplikace C++ a standardní kódu C++ napříč platformami. V tématu [postupy: použití existujícího kódu C++ v aplikaci pro platformu Universal Windows](../porting/how-to-use-existing-cpp-code-in-a-universal-windows-platform-app.md).  
  
##  <a name="BK_81StoreApp">Portování aplikací Windows 8.1 Store, aby UWP</a>  
 Pokud máte aplikaci ve Windows 8.1 Store, můžete tento postup se dá stáhnout pracující na UWP a z jakéhokoliv zařízení se systémem Windows 10.  Je vhodné první sestavení projektu s Visual Studio 2017 jako projekt Windows 8.1, nejprve odstranit veškeré problémy, které jsou vyvolány změny v kompilátoru a knihovny. Jakmile provedete tento krok, převeďte ho do projektu UPW Windows 10 dvěma způsoby. Nejjednodušším způsobem (jak je popsáno v následujícím postupu) je vytvoření projektu Universal Windows a zkopírujte do něj váš stávající kód. Pokud jste používali univerzální projekt pro stolní počítače s Windows 8.1 a Windows 8.1 Phone, projekt bude začínat dvě různé rozložení v jazyce XAML, ale end s jedno dynamické rozložení, která se přizpůsobí Zobrazovaná velikost.  
  
#### <a name="to-port-a-windows-81-store-app-to-the-uwp"></a>Port aplikaci ve Windows 8.1 Store do UWP  
  
1.  Pokud jste tak již neučinili, otevřete projekt aplikace Windows 8.1 ve Visual Studio 2017 a postupujte podle pokynů k upgradu souboru projektu.  
  
     Je potřeba mít nainstalovány nástroje pro Windows 8.1 v instalačním programu sady Visual Studio. Pokud nemáte nainstalované tyto nástroje, spusťte instalaci sady Visual Studio z okna programy a funkce, zvolte Visual Studio 2017 a v okně Nastavení **upravit**. Vyhledejte nástroje Windows 8.1, ujistěte se, že je vybraná a klepněte na tlačítko OK.  
  
2.  Otevřete okno Vlastnosti projektu a v jazyce C++ obecné, nastavte sada nástrojů platformy na v141, nástroje pro sestavení pro Visual Studio 2017.  
  
3.  Sestavení projektu jako projekt Windows 8.1 a vyřešte všechny chyby sestavení. Všechny chyby v této fázi se pravděpodobně z důvodu nejnovější změny v sestavení nástroje a knihovny. V tématu [historie 2003 2015 změn Visual C++](../porting/visual-cpp-change-history-2003-2015.md) podrobné vysvětlení změny, které mohou ovlivnit váš kód.  
  
     Jakmile projektu sestavení řádně, jste připraveni k portu ke Universal Windows (Windows 10).  
  
4.  Vytvoření nového projektu univerzální aplikace pro Windows pomocí prázdné šablony. Můžete chtít poskytněte stejný název jako existující projekt, i když k tomu projektů musí být v různých adresářích.  
  
5.  Zavřete řešení a potom pomocí Průzkumníka Windows nebo na příkazovém řádku, zkopírujte soubory kódu (s sada rozšíření, .h a XAML) z projektu Windows 8.1 do stejné složky jako soubor projektu (VCXPROJ) pro projekt, který jste vytvořili v kroku 1. Nekopírujte soubor Package.appxmanifest a pokud máte samostatnou kód pro stolní počítače s Windows 8.1 a telefon, vyberte jednu z nich na port první (budete muset nějakou práci později přizpůsobit na druhý). Ujistěte se, kopírování a podsložky a jejich obsah. Pokud se zobrazí výzva, zvolte Nahradit všechny soubory s duplicitními názvy.  
  
6.  Otevřete řešení a zvolte **přidat, existující položka** v místní nabídce uzlu projektu. Vyberte všechny soubory, které jste zkopírovali, s výjimkou těch, které jsou již součástí projektu.  
  
     Zkontrolujte všechny podsložky a nezapomeňte přidat soubory v nich také.  
  
7.  Pokud nepoužíváte stejným názvem jako vaše staré projekt, otevřete soubor Package.appxmanifest a aktualizujte vstupní bod, aby odrážela název oboru názvů pro třídu aplikace.  
  
     **Vstupní bod** pole v souboru Package.appxmanifest obsahuje název oboru pro třídu aplikace, která zahrnuje obor názvů, který obsahuje třídu aplikace. Když vytvoříte projekt Universal Windows, obor názvů se nastaví na název projektu. Pokud se to neliší od co je v souborech, které jste zkopírovali v z původního projektu, je nutné aktualizovat jeden z nich tak, aby byly shodovat.  
  
8.  Sestavte projekt a vyřešte všechny chyby sestavení z důvodu nejnovější změny mezi různými verzemi sady Windows SDK.  
  
9. Spusťte projekt na místní pracovní ploše. Ověřte, zda nejsou žádné chyby nasazení a že rozložení aplikace vypadá přiměřené a zda správně funguje na ploše.  
  
10. Pokud jste měli samostatné soubory kódu a XAML pro jiná zařízení, například Windows Phone 8.1, zkontrolujte tento kód a identifikovat, pokud se liší od standardní zařízení. Pokud je rozdíl pouze v rozložení, je možné používat Visual správce stavu v xaml pro přizpůsobení zobrazení v závislosti na velikosti obrazovky. Pro ostatní rozdílů můžete použít části podmínky v kódu pomocí následující příkazy #if.  
  
    ```  
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PC_APP)  
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PHONE_APP)  
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_APP)  
    #if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_DESKTOP)  
    ```  
  
     Tyto příkazy v uvedeném pořadí platí pro aplikace UWP, Windows Phone Store aplikace, oba, nebo ani (classic Win32 jenom desktop). Tyto makra jsou k dispozici pouze ve Windows SDK 8.1 a novější, takže pokud váš kód potřebuje ke kompilaci dřívějších verzí sady Windows SDK nebo pro jiné platformy kromě Windows, a měli byste také zvážit případě že žádný z nich jsou definovány.  
  
11. Spuštění a ladění aplikace na emulátoru nebo fyzické zařízení, pro každý typ zařízení, které podporuje vaše aplikace. Pokud chcete spustit emulátoru, musíte spustit Visual Studio na fyzickém počítači, není virtuální počítač.  
  
##  <a name="BK_81Component">Portování součásti modulu Runtime Windows 8.1 do UWP</a>  
 Pokud máte knihovny DLL nebo komponent prostředí Windows Runtime, která již pracuje s aplikací pro Windows 8.1 Store, můžete tento postup slouží k získání součásti nebo DLL práce s UWP a Windows 10. Základní postup se týká vytvoření nového projektu a zkopírujte do ní kód.  
  
#### <a name="to-port-a-windows-81-runtime-component-to-the-uwp"></a>Port komponent prostředí Windows 8.1 Runtime do UWP  
  
1.  V **nový projekt** dialogové okno ve Visual Studio 2017, vyhledejte **univerzální pro Windows** uzlu. Pokud nevidíte tento uzel, nainstalujte [nástrojů pro Windows 10](http://go.microsoft.com/fwlink/p/?LinkID=617903) první. Vyberte **komponenty prostředí Windows Runtime** šablony, zadejte název pro příslušné součásti a zvolte **OK** tlačítko. Název součásti se použije jako název oboru názvů, takže můžete chtít použít stejný název jako vaše staré projekty obor názvů. To je potřeba, abyste vytvořili projekt v jiné složce než ten starý. Pokud si zvolíte jiný název, můžete aktualizovat název oboru názvů v souborech generovaného kódu.  
  
2.  Zavřete projekt.  
  
3.  Zkopírujte všechny soubory kódu (sada, .h, XAML atd.) z příslušné součásti Windows 8.1 do nově vytvořený projekt. Nekopírujte soubor Package.appxmanifest.  
  
4.  Sestavení a vyřešte všechny chyby kvůli nejnovější změny mezi různými verzemi sady Windows SDK.  
  
## <a name="troubleshooting"></a>Poradce při potížích  
 Různé chyby může dojít během procesu portování kódu do UWP. Zde jsou některé možné problémy, ke kterým může dojít.  
  
 **Problémy s konfigurací projektu**  
  
 Může dojít k chybě:  
  
```Output  
could not find assembly 'platform.winmd': please specify the assembly search path using /AI or by setting the LIBPATH environment variable  
```  
  
 V takovém případě není jako Windows Universal project vytváření projektu. Zkontrolujte soubor projektu a ujistěte se, že má správné elementů XML, které identifikují projektu jako projektu univerzální pro Windows. Tyto prvky by měl být (číslo verze cílové platformy může být jiné):  
  
```xml  
<AppContainerApplication>true</AppContainerApplication>  
<ApplicationType>Windows Store</ApplicationType>  
<WindowsTargetPlatformVersion>10.0.10156.0</WindowsTargetPlatformVersion>  
<WindowsTargetPlatformMinVersion>10.0.10156.0</WindowsTargetPlatformMinVersion>  
<ApplicationTypeRevision>10.0</ApplicationTypeRevision>  
```  
  
 Pokud jste vytvořili nový projekt UWP pomocí sady Visual Studio, tuto chybu byste neměli vidět.  
  
## <a name="see-also"></a>Viz také  
 [Průvodce přenosem Visual C++](../porting/porting-to-the-universal-windows-platform-cpp.md)   
 [Vývoj aplikací pro Univerzální platformu Windows (UWP)](/visualstudio/cross-platform/develop-apps-for-the-universal-windows-platform-uwp)
