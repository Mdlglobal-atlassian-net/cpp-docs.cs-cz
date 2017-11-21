---
title: "Postupy: použití existujícího kódu C++ v aplikaci pro platformu Universal Windows | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 87e5818c-3081-42f3-a30d-3dca2cf0645c
caps.latest.revision: "5"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 10b63f8e7bd7d23e75417e28b45d533832c8426e
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="how-to-use-existing-c-code-in-a-universal-windows-platform-app"></a>Návody: Použití existujícího kódu C++ v aplikaci pro univerzální platformu pro Windows
Nejjednodušší způsob, jak získat vaše desktopovému programu spuštěným v prostředí UWP je možná použití technologie most plochy. Patří mezi ně aplikace převaděč plochy, která bude balíček aplikace pro UPW aplikaci bez kódu na změny. Další informace najdete v tématu [přineste vaší aplikace na ploše do univerzální platformu Windows (UWP) s most plochy](https://msdn.microsoft.com/windows/uwp/porting/desktop-to-uwp-root).

Zbývající část tohoto tématu popisuje, jak k portu knihovny jazyka C++ (knihovny DLL a statických knihoven) pro univerzální platformu Windows (UWP). Můžete k tomu, aby vaše základní C++ logiky můžete použít s více aplikacemi UWP. 
  
 Aplikace UWP spustit v prostředí chráněném v důsledku toho nejsou povoleny mnoha Win32 a COM, rozhraní API CRT volání, které může dojít k ohrožení zabezpečení platformy. Kompilátor zjistit těchto volání a generovat chybu, pokud je použita možnost /ZW. Certification Kit aplikace ve vaší aplikaci můžete použít k detekci kód, který volá rozhraní API pro zakázané. V tématu [pomocí App Certification Kit](https://msdn.microsoft.com/library/windows/apps/hh694081.aspx).  
  
 Pokud zdrojový kód je k dispozici pro knihovny, je možné omezit zakázané volání rozhraní API. Podrobnosti, včetně seznamu rozhraní API, které jsou povoleno nebo zakázáno najdete v tématu [Win32 a COM aplikace Runtime pro Windows a Universal Windows platform (UWP) aplikace](https://msdn.microsoft.com/library/windows/apps/br205762.aspx) a [CRT funkce není podporována s /ZW](https://msdn.microsoft.com/library/windows/apps/jj606124.aspx). Některé alternativy naleznete na adrese [alternativy k rozhraní API systému Windows v prostředí Windows Runtime aplikace a aplikace pro univerzální platformu Windows (UWP)](https://msdn.microsoft.com/library/windows/apps/hh464945.aspx).  
  
 Pokud se pokusíte přidat odkaz z Universal Windows Project do knihovny klasické pracovní plochy, zobrazí se chybová zpráva s upozorněním, že knihovna není kompatibilní. V případě statické knihovny můžete se propojit k knihovnu jednoduše přidáním knihovny (.lib soubor) do váš vstup linkeru stejně jako v klasické aplikace typu Win32. Pro knihovny, kde je k dispozici pouze binární to je jedinou možností. Statické knihovny je propojený do vaší aplikace spustitelný soubor, ale Win32 knihovnu DLL, kterou můžete používat v aplikaci UWP musí být zabalené do aplikace včetně v projektu a označit ji jako obsah. Načtení knihovny DLL Win32 v aplikaci pro univerzální platformu Windows, máte také k volání [LoadPackagedLibrary](https://msdn.microsoft.com/library/windows/desktop/hh447159.aspx) místo LoadLibrary nebo funkce LoadLibraryEx.  
  
 Pokud máte zdrojový kód pro knihovnu DLL nebo statické knihovny, můžete jako projektu UPW překompilovat s /ZW. Pokud tak učiníte, můžete přidat odkaz pomocí Průzkumníka řešení a jeho použití v aplikace C++ UWP. V případě knihovny DLL propojte s knihovnou export.  
  
 Ke zpřístupnění funkcí pro volající v jiných jazycích, můžete převést knihovny komponent prostředí Windows Runtime. Modul Runtime součásti systému Windows se liší od běžné knihovny DLL v tom, že obsahují metadata ve formě .winmd soubory, které popisují obsah způsobem, který vyžadují rozhraní .NET a JavaScript příjemci. Ke zveřejnění prvky rozhraní API pro jiné jazyky, můžete přidat C + +/ CX konstrukce, jako jsou třídy ref a je zveřejnit nebo používat [Windows Runtime C++ šablony knihovny (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).  V systému Windows 10 a novější, můžete použít [C + +/ WinRT knihovny](https://github.com/microsoft/cppwinrt) místo C + +/ CX. 
  
 Výše uvedené informace se nevztahuje na případ součástí modelu COM, které musí být zpracovány jinak. Pokud máte server COM v EXE nebo DLL, můžete ho v Universal Windows Project tak dlouho, dokud ji jako balíček [komponenty modelu COM bez registrace](https://msdn.microsoft.com/library/dd408052.aspx), přidejte do projektu jako soubor obsahu a vytvoří instanci pomocí [ CoCreateInstanceFromApp](https://msdn.microsoft.com/library/windows/apps/hh404137.aspx). V tématu [pomocí knihovny DLL COM bez v projektu C++ Windows Store](http://blogs.msdn.com/b/win8devsupport/archive/2013/05/20/using-free-com-dll-in-windows-store-c-project.aspx).  
  
 Pokud máte existující knihovnu COM, kterou chcete portu do univerzální platformy Windows, je možné převést na komponent prostředí Windows Runtime s použitím [Windows Runtime C++ šablony knihovny (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md). WRL nepodporuje všechny funkce knihovny ATL a OLE, tak, jestli je to vhodné takové port závisí na kolik kódu COM závisí na jaké funkce modelu COM, ATL, a vyžaduje technologie OLE příslušné součásti.  
  
 Toto jsou různé způsoby používané existujícího kódu C++ v projektech pro univerzální platformu Windows. Některé způsoby nevyžadují kódu zopakovat s příponami součást (C + +/ CX) povoleno (to znamená, že se /ZW možnost) a některé provést, takže pokud je potřeba zachovat kódu v jazyce C++ standardní nebo zachovat classic prostředí kompilace Win32 pro určitý kód, můžete tak učinit , s možností příslušnou architekturu. Kód, který obsahuje uživatelské rozhraní pro platformu Universal Windows a typy, které chcete zpřístupnit pro C#, Visual Basic a JavaScript volající by měl být v aplikaci pro Windows projekty a komponenty prostředí Windows Runtime projekty. Kód, který musí využívat pouze v jazyce C++ (včetně C + +/ CX) může být buď kódu v projektu, který se zkompiluje s parametrem wdn nebo standardní projektu jazyka C++. Pouze binární kód můžete použít přes propojení v jako statickou knihovnu, nebo spojených s aplikací jako obsah a načíst v knihovně DLL pouze v případě, že nepoužívá zakázané rozhraní API.  
  
 Bez ohledu na to, které z těchto scénářů vývoj zvolíte byste měli vědět několik definice maker, které můžete použít ve vašem kódu, takže můžete zkompilovat kód podmíněně pod klasický desktopový Win32 a univerzální platformu Windows.  
  
```cpp  
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PC_APP)  
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PHONE_APP)  
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_APP)  
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_DESKTOP)  
```  
  
 Tyto příkazy v uvedeném pořadí platí pro aplikace pro Windows Store, Windows Phone Store aplikace, oba, nebo ani (classic Win32 jenom desktop). Tyto makra jsou k dispozici pouze ve Windows SDK 8.1 a novější, takže pokud váš kód potřebuje ke kompilaci dřívějších verzí sady Windows SDK nebo pro jiné platformy kromě Windows, a měli byste také zvážit případě že žádný z nich jsou definovány.  
  
 Toto téma obsahuje následující postupy.  
  
1.  [Pomocí Win32 knihovny DLL v aplikaci pro platformu Universal Windows](#BK_Win32DLL)  
  
2.  [Použití nativních statické knihovny C++ v aplikaci UWP](#BK_StaticLib)  
  
3.  [Portování C++ knihovnu, kterou chcete komponent prostředí Windows Runtime](#BK_WinRTComponent)  
  
##  <a name="BK_Win32DLL"></a>Pomocí Win32 knihovny DLL v aplikaci pro platformu Universal Windows  
 Pro lepší zabezpečení a spolehlivost spusťte univerzálních aplikací pro Windows v prostředí s omezeným přístupem modulu runtime, nemůžete stačí použít všechny nativní knihovny DLL způsob, jakým byste v klasická desktopová aplikace systému Windows. Pokud máte zdrojový kód pro knihovnu DLL, můžete se tak, aby běžel na UWP portu kód. Spuštění změnou k identifikaci projektu jako projektu UPW několik nastavení projektu a metadata souboru projektu. Budete muset zkompilovat kód knihovny pomocí možnosti /ZW, která umožňuje C + +/ CX. Některé volání rozhraní API nejsou povoleny v aplikacích pro UPW z důvodu přísnější ovládací prvky přidružené k prostředí. V tématu [Win32 a COM pro prostředí Windows Runtime aplikace a Universal Windows Platform (UWP) aplikace](https://msdn.microsoft.com/library/windows/apps/br205757.aspx).  
  
 Následující postup platí pro případ, kdy máte nativní knihovny DLL, která zveřejňuje funkcí pomocí deklarace __declspec(dllexport).  
  
#### <a name="to-port-a-native-dll-to-the-uwp-without-creating-a-new-project"></a>Port nativní knihovny DLL do UWP bez vytvoření nového projektu  
  
1.  Pokud máte nativní knihovny DLL, který exportuje funkce pomocí __declspec(dllexport), můžete tyto funkce volání z aplikace UWP opětovnou kompilací knihovnu DLL jako projektu UPW. Předpokládejme například, že máme knihovny DLL, který exportuje několika třídy a jejich metody s kódem jako následující soubor hlavičky:  
  
    ```  
    // giraffe.h  
    #pragma once  
  
    #ifdef _DLL  
    #define GIRAFFE_API __declspec(dllexport)  
    #else  
    #define GIRAFFE_API   
    #endif  
  
    GIRAFFE_API int giraffeFunction();  
  
    class Giraffe  
    {  
        int id;  
            Giraffe(int id_in);  
        friend class GiraffeFactory;  
  
    public:  
        GIRAFFE_API int GetID();  
    };  
  
    class GiraffeFactory  
    {  
        static int nextID;  
    
    public:  
        GIRAFFE_API GiraffeFactory();  
        GIRAFFE_API static int GetNextID();  
        GIRAFFE_API static Giraffe* Create();  
   };  
    ```  
  
     A soubor následující kód:  
  
    ```  
    // giraffe.cpp  
    #include "stdafx.h"  
    #include "giraffe.h"  
  
    Giraffe::Giraffe(int id_in) : id(id_in)  
    {  
    }  
  
    int Giraffe::GetID()  
    {  
      return id;  
    }  
  
    int GiraffeFactory::nextID = 0;  
  
    GiraffeFactory::GiraffeFactory()  
    {  
        nextID = 0;  
    }  
  
    int GiraffeFactory::GetNextID()  
    {  
        return nextID;  
    }  
  
    Giraffe* GiraffeFactory::Create()  
    {  
        return new Giraffe(nextID++);  
    }  
  
    int giraffeFunction();  
    ```  
  
     Všem ostatním v projektu (stdafx.h, dllmain.cpp) je součástí standardní šablona projektu Win32. Pokud chcete sledovat, ale nechcete použít vlastní knihovny DLL ještě v těchto krocích, zkuste vytvořit projekt Win32, vyberte knihovny DLL v Průvodce projektem a potom přidat záhlaví souboru giraffe.h a kód soubor giraffe.cpp a zkopírujte obsah z kódu v tomto kroku do aplikace ropriate soubory.  
  
     Kód definuje makro GIRAFFE_API, který se přeloží na __declspec(dllexport) při _dll – je definována (při sestavení projektu jako knihovny DLL).  
  
2.  Otevřete vlastnosti projektu projektu knihovny DLL a nastavte konfiguraci na **všechny konfigurace**.  
  
3.  Ve vlastnostech projektu v části **C/C++**, **Obecné** nastavte **využívat Windows Runtime Extension** k **Ano (/ZW)**. To umožňuje rozšíření komponent (C + +/ CX).  
  
4.  V **Průzkumníku řešení**, vyberte uzel projektu, otevřete v místní nabídce a zvolte **uvolnit projekt**. Potom otevřete místní nabídky na uzel odpojen projektu a vyberte, chcete-li upravit soubor projektu. Vyhledejte WindowsTargetPlatformVersion element a nahraďte ji metodou následující prvky.  
  
    ```xml  
    <AppContainerApplication>true</AppContainerApplication>  
    <ApplicationType>Windows Store</ApplicationType>  
    <WindowsTargetPlatformVersion>10.0.10156.0</WindowsTargetPlatformVersion>  
    <WindowsTargetPlatformMinVersion>10.0.10156.0</WindowsTargetPlatformMinVersion>  
    <ApplicationTypeRevision>10.0</ApplicationTypeRevision>  
    ```  
  
     Zavřete soubor VCXPROJ, znovu otevřete místní nabídku a vyberte **znovu načíst projekt**.  
  
     Průzkumník řešení nyní identifikuje projektu jako Universal Windows project.  
  
5.  Zkontrolujte, zda že je správný název souboru předkompilovaných hlaviček. V části předkompilovaných hlaviček změňte z pch.h na stdafx.h předkompilovaný hlavičkový soubor. Pokud to neuděláte, zobrazí se následující chyba.  
  
    ```Output  
    error C2857: '#include' statement specified with the /Ycpch.h command-line option was not found in the source file  
    ```  
  
     Problém je, že projekty pro Universal Windows používat různé zásady vytváření názvů pro předkompilovaný hlavičkový soubor.  
  
6.  Sestavte projekt. Můžete získat několika chybám o možnosti nekompatibilní příkazového řádku. Například často používaných možnost povolit minimální opětovné sestavení (nebo Gm) je nastaven ve výchozím nastavení v mnoha projektů C++ a není kompatibilní s /ZW.  
  
     Některé funkce nejsou k dispozici, při kompilaci pro univerzální platformu Windows. Zobrazí se chyby kompilátoru případné potíže. Adres tyto, dokud nebudete mít čistá sestavení.  
  
7.  Použití knihovny DLL v aplikaci UWP ve stejném řešení, otevřete místní nabídce uzlu projektu UPW a vyberte **přidat, odkazovat**.  
  
     V části **projekty, řešení**, zaškrtněte políčko vedle projektu knihovny DLL a zvolit **OK** tlačítko.  
  
8.  Soubory knihovny v záhlaví zahrňte do vaší aplikace UWP pch.h souboru.  
  
    ```  
    #include "..\MyNativeDLL\giraffe.h"  
    ```  
  
9. Přidejte kód obvyklým v projektu UPW k vyvolání funkce a vytvoří typy z knihovny DLL.  
  
    ```  
    MainPage::MainPage()  
    {  
        InitializeComponent();  
        GiraffeFactory gf;  
        Giraffe* g = gf.Create();  
        int id = g->GetID();  
    }  
  
    ```  
  
##  <a name="BK_StaticLib"></a>Použití nativních statické knihovny C++ v aplikaci UWP  
 Můžete použít nativní statické knihovny C++ v projektu UPW, ale existují určitá omezení a omezení znát. Začněte tím, že to čtení [tématu](https://msdn.microsoft.com/library/hh771041.aspx) o statických knihoven v jazyce C + +/ CX. Nativní kód v statickou knihovnu získáváte přístup z vaší aplikace pro UPW, ale nedoporučujeme vytvoření veřejné ref typů v statické knihovny. Pokud při kompilaci s parametrem /ZW statickou knihovnu, upozorní librarian (ve skutečnosti linker v maskování):  
  
```  
LNK4264: archiving object file compiled with /ZW into a static library; note that when authoring Windows Runtime types it is not recommended to link with a static library that contains Windows Runtime metadata  
```  
  
 Statické knihovny v UWP můžete však použít bez nutnosti znovu kompilovat s /ZW. Nebudete moci deklarovat všechny typy ref nebo použijte C + +/ CX vytvoří, ale pokud vaše účelem je jednoduše používat knihovny nativního kódu, pak můžete tak učinit pomocí následujícího postupu.  
  
#### <a name="to-use-a-native-c-static-library-in-a-uwp-project"></a>Použít nativní statické knihovny C++ v projektu UPW  
  
1.  Ve vlastnostech projektu projektu UPW, v části Linker přidejte cestu ke knihovně ve vlastnosti vstup. Například pro knihovnu v projektu, který umístí její výstup v *SolutionFolder*\Debug\MyNativeLibrary\MyNativeLibrary.lib, přidejte relativní cestu `Debug\MyNativeLibrary\MyNativeLibrary.lib`.  
  
2.  Přidejte příkaz zahrnout soubor hlaviček, aby vaše pch.h v projektu UPW odkazovat a začít přidávat kód, který používá knihovnu.  
  
    ```  
    #include "..\MyNativeLibrary\giraffe.h"  
    ```  
  
     Nepřidávejte odkaz v **odkazy** uzlu v **Průzkumníku řešení**. Tento mechanismus funguje pouze pro součásti režimu Runtime systému Windows.  
  
##  <a name="BK_WinRTComponent"></a>Portování C++ knihovnu, kterou chcete komponent prostředí Windows Runtime  
 Pokud chcete využívat nativní rozhraní API v statické knihovny z aplikace pro UPW, a mít zdrojový kód pro nativní knihovny, můžete portu kód, který komponent prostředí Windows Runtime. Statické knihovny už nebude, bude knihovny DLL. Můžete ji použít v jakékoli aplikaci, C++ UWP, ale na rozdíl od případu statické knihovny, můžete přidat ref typy a dalších C + +/ CX konstrukce, které jsou k dispozici pro klienty v žádný kód aplikace UPW, bez ohledu na jazyk. Tyto typy tedy můžete přistupovat z jazyka C#, Visual Basic nebo JavaScript.  Základní postup se týká vytvoření projektu komponenty prostředí Windows Runtime, zkopírujte do ní kód pro statické knihovny a vyřešte všechny chyby, které jsou vyvolány přesunutí kód ze standardní C++ kompilace /ZW kompilace.  
  
#### <a name="to-port-a-c-library-to-a-windows-runtime-component"></a>K portu C++ knihovnu, kterou chcete komponent prostředí Windows Runtime  
  
1.  Vytvoření projektu komponenty prostředí Windows Runtime.  
  
2.  Zavřete projekt.  
  
3.  V Průzkumníku souborů Windows vyhledejte projektu. Ve výchozím nastavení používá Visual Studio složce 2017\Projects sady Visual Studio ve složce Dokumenty. Vyhledejte projektu knihovny C++, který obsahuje kód, který chcete port. Zkopírujte zdrojové soubory (soubory hlaviček, soubory kódu a žádné další prostředky, včetně v podadresářích) z projektu knihovny jazyka C++ a vložte je do složky, do projektu, a zkontrolujte, zda zachovat stejnou strukturu složek.  
  
4.  Otevřete projekt komponenty prostředí Windows Runtime a otevřete místní nabídce uzlu projektu v **Průzkumníku řešení**a zvolte **přidat, existující položka**.  
  
5.  Vyberte všechny soubory z původního projektu přidat a klikněte na tlačítko OK. Opakujte, pokud je to nutné pro podsložky.  
  
6.  Vám může nyní mají některé duplicitní kódu. Pokud máte více než jeden předkompilovaných hlaviček (například stdafx.h a pch.h), zvolte chcete zachovat. Zkopírujte všechny požadované kód, jako například zahrnout příkazů do je ta, kterou jste uchování. Potom v části odstranit vlastnosti jiných a v projektu **předkompilovaných hlaviček**, ujistěte se, zda je správný název hlavičky souboru.  
  
     Pokud jste změnili soubor, který chcete použít jako předkompilovaných hlaviček, ujistěte se, že jsou správné pro každý soubor možnosti předkompilovaných hlaviček. Vyberte každého souboru zase, otevřete jeho vlastnosti – okno a ujistěte se, že všechny jsou nastaveny na **použití (/Yu)**, s výjimkou požadované předkompilovaných hlaviček, které musí být nastavena na **vytvořit (/Yc)**.  
  
7.  Sestavte projekt a vyřešte případné chyby. Tyto chyby může být způsobeno pomocí možnosti /ZW nebo může být způsobeno novou verzi sady Windows SDK nebo odrážejí může závislosti, jako jsou soubory hlaviček, které vaše knihovna závisí na nebo rozdíly v nastavení projektu mezi projektu staré a nové o Ne.  
  
8.  Do projektu přidejte veřejný ref typy nebo typy ref vystavit vstupní body do funkce, kterou chcete volat z aplikace UWP převést běžné typy.  
  
9. Testování komponentu přidáním odkazu k němu z projekt aplikace UPW a přidat kód pro volání veřejná rozhraní API, které jste vytvořili.  
  
## <a name="see-also"></a>Viz také  
 [Přenos aplikací do univerzální platformy Windows](../porting/porting-to-the-universal-windows-platform-cpp.md)