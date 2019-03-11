---
title: 'Postupy: Použití existujícího kódu C++ v aplikaci Windows Universal Platform'
ms.date: 08/21/2018
ms.assetid: 87e5818c-3081-42f3-a30d-3dca2cf0645c
ms.openlocfilehash: 1a4633b74591e16f22def44ff5875557f2909043
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/11/2019
ms.locfileid: "57745509"
---
# <a name="how-to-use-existing-c-code-in-a-universal-windows-platform-app"></a>Postupy: Použití existujícího kódu C++ v aplikaci Windows Universal Platform

Nejjednodušší způsob, jak získat aplikace klasické pracovní plochy běžící v prostředí UPW je možná použití technologie přemostění na Desktop. Patří mezi ně Desktop App Converter, který vytvoří balíček aplikace jako aplikace pro UPW bez nutných změn kódu. Další informace najdete v tématu [přemostění na Desktop](/windows/uwp/porting/desktop-to-uwp-root).

Zbývající část tohoto tématu popisuje, jak přenést knihoven C++ (knihovny DLL a statických knihoven) pro univerzální platformu Windows (UPW). Můžete to provést tak, aby vaše základní logiku C++ lze použít s více aplikacemi UWP.

Spouštění aplikací pro UWP v chráněném prostředí a v důsledku toho nejsou povoleny mnoho volání Win32 a COM a rozhraní API CRT, které by mohlo ohrozit zabezpečení platformy. Kompilátor může rozpoznat taková volání a vygenerují chybu, pokud `/ZW` možnost se používá. App Certification Kit na svou aplikaci můžete použít ke zjištění kódu, který volá rozhraní API zakázané. Další informace najdete v tématu [sada Windows App Certification Kit](/windows/uwp/debug-test-perf/windows-app-certification-kit).

Pokud zdrojový kód je k dispozici pro knihovny, je možné eliminovat zakázané volání rozhraní API. Podrobnosti, včetně seznamu rozhraní API, které jsou povolené nebo zakázané najdete v tématu [Win32 a COM API pro aplikace pro UPW](/uwp/win32-and-com/win32-and-com-for-uwp-apps) a [CRT funkce nejsou podporovány v aplikacích pro univerzální platformu Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md). Některé alternativy najdete na [alternativy k rozhraní API Windows v aplikacích pro UWP](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).

Pokud se pokusíte přidat odkaz z Universal Windows Project do knihovny klasické plochy, obdržíte chybovou zprávu s upozorněním, že knihovna není kompatibilní. V případě statické knihovny můžete propojit do knihovny jednoduše tak, že přidání knihovny (.lib soubor) do váš vstup linkeru stejně, jako byste to udělali v klasické aplikaci Win32. Pro knihovny, kde je k dispozici pouze do binárního souboru to je jedinou možností. Statická knihovna je propojené s vaší aplikace spustitelný soubor, ale Win32 DLL, které skutečně využijete v aplikaci UWP, musí být zabaleny do aplikace tak, že jejich zahrnování do projektu a jeho označení jako obsah. Načtení knihovny DLL Win32 v aplikaci UWP, budete muset volat [LoadPackagedLibrary](/windows/desktop/api/winbase/nf-winbase-loadpackagedlibrary) místo `LoadLibrary` nebo `LoadLibraryEx`.

Pokud máte zdrojový kód pro knihovnu DLL nebo statické knihovny, můžete znovu zkompilovat s `/ZW` jako projekt UPW. Pokud to uděláte, můžete přidat odkaz pomocí **Průzkumníka řešení**a jeho použití v aplikacích pro C++ UWP. V případě knihovny DLL propojení s knihovnou exportu.

Vystavit funkčnost volajícím v jiných jazycích, můžete převést knihovny do komponenty Windows Runtime. Součástí prostředí Windows Runtime se liší od běžné knihovny DLL, že obsahují metadat ve formě soubory .winmd, které popisují obsah tak, aby vyžadují rozhraní .NET a JavaScript uživatele. Chcete-li zpřístupnit prvky rozhraní API do jiných jazyků, můžete přidat C + +/ CX konstrukce, jako je například referenční třídy a daly veřejné nebo použít [Windows Runtime C++ šablony knihovny (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).  Ve Windows 10 a novější, můžete použít [C + +/ knihoven WinRT](https://github.com/microsoft/cppwinrt) místo C + +/ CX.

Výše uvedené informace neplatí pro případ komponenty modelu COM, které musí být zpracovány jinak. Pokud máte v souboru EXE nebo DLL serveru COM, můžete ho v Universal Windows Project tak dlouho, dokud ji jako balíček [komponenty modelu COM bez registrace](/windows/desktop/sbscs/creating-registration-free-com-objects), přidáte jej do projektu jako soubor s obsahem a vytvořit instanci pomocí [ Funkce CoCreateInstanceFromApp](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstancefromapp). Další informace najdete v tématu [pomocí Free COM DLL v projektu C++ Windows Store](https://blogs.msdn.microsoft.com/win8devsupport/2013/05/19/using-free-com-dll-in-windows-store-c-project/).

Pokud máte existující knihovny modelu COM, které chcete port pro UPW, může být možné převést do komponenty Windows Runtime s použitím [Windows Runtime C++ šablony knihovny (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md). WRL nepodporuje všechny funkce ATL OLE, tak, jestli je možné takové port závisí na tom, kolik váš kód v modelu COM závisí na funkcích modelu COM, ATL, a OLE vaše komponenta vyžaduje.

Toto jsou různé způsoby, může použití existujícího kódu C++ v projektech UPW. Některé způsoby nevyžadují kód třeba znovu zkompilovat pomocí rozšíření komponent (C + +/ CX) povolena (tedy s `/ZW` možnost) a některé proveďte, pokud tedy potřebujete zachovat kódu ve standardním jazyce C++, nebo zachovat klasického prostředí kompilace Win32 pro nějaký kód, můžete Uděláte to tak, možnosti pro příslušnou architekturu. Kód, který obsahuje UPW uživatelského rozhraní a typy, které mají být vystavená pro C#, Visual Basic a JavaScript volající by měl být v aplikaci Windows projekty a projekty součást prostředí Windows Runtime. Kód, který je potřeba využívat pouze v jazyce C++ (včetně C + +/ CX) kód může být buď v projektu, který se zkompiluje `/WX` možnost nebo standardní projekt C++. Pouze pro binární kód lze použít v propojením jako statické knihovny, nebo součástí aplikace jako obsah balíčku a načten v knihovně DLL pouze v případě, že ho nepoužívá zakázané rozhraní API.

Bez ohledu na to, které z těchto scénářů vývoje zvolíte byste měli vědět, počet definicí maker, které můžete použít ve vašem kódu, takže můžete zkompilovat kód podmíněně Win32 klasické plochy a UPW.

```cpp
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PC_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PHONE_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_DESKTOP)
```

Tyto příkazy v uvedeném pořadí se vztahují na aplikacích pro UPW, Windows Phone Store aplikace, obou nebo ani jedna (classic Win32 jenom desktopové verze). Tato makra jsou k dispozici pouze ve Windows SDK 8.1 a novější, takže pokud váš kód musí být možné zkompilovat pomocí předchozích verzí sady Windows SDK nebo pro jiné platformy kromě Windows, pak byste měli také zvážit případě že žádný z nich jsou definovány.

Toto téma obsahuje následující postupy:

- [Použití Win32 DLL v aplikaci UWP](#BK_Win32DLL)

- [Pomocí nativní statickou knihovnu C++ v aplikaci UWP](#BK_StaticLib)

- [Portování knihovnu C++ ke komponentě ve Windows Runtime](#BK_WinRTComponent)

##  <a name="BK_Win32DLL"></a> Použití Win32 DLL v aplikaci UWP

Pro lepší zabezpečení a spolehlivost spusťte univerzálních aplikací pro Windows v prostředí s omezeným přístupem modulu CLR, proto nelze stačí použít všechny nativní knihovnu DLL způsob, jakým byste to udělali v klasické aplikace klasické pracovní plochy Windows. Pokud máte zdrojový kód pro knihovnu DLL, lze přenést kód tak, aby běžel na UPW. Začnete tím, že změna několik nastavení projektu a soubor metadat projektu k identifikaci projekt jako projekt UPW. Budete potřebovat ke kompilaci kódu pomocí knihovny `/ZW` možnost, která povolí C + +/ CX. Volání určitých rozhraní API nejsou povolené v aplikacích pro UWP z důvodu větší ovládací prvky přidružené k příslušné prostředí. Zobrazit [Win32 a COM API pro aplikace pro UPW](/uwp/win32-and-com/win32-and-com-for-uwp-apps).

Následující postup platí pro případ, kdy máte nativní knihovnu DLL, který zveřejňuje funkce pomocí **__declspec(dllexport)**.

### <a name="to-port-a-native-dll-to-the-uwp-without-creating-a-new-project"></a>Port nativní knihovnu DLL pro UPW bez vytvoření nového projektu

1. Pokud máte nativní knihovnu DLL, která se exportuje funkce s použitím **__declspec(dllexport)**, tyto funkce můžete volat z aplikace pro UPW opětovnou kompilací knihovny DLL jako projekt UPW. Předpokládejme například, že máme knihovnu DLL, která se exportuje do ní několik třídy a jejich metod s kódem jako následujícím souboru hlaviček:

    ```cpp
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

   A souboru následující kód:

    ```cpp
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

   Všechno ostatní v projektu (stdafx.h, dllmain.cpp) je součástí standardní šablony projektu Win32. Pokud chcete postup sledovat, ale nechcete použít vlastní knihovnu DLL ještě tímto postupem, zkuste vytvořit projekt Win32, vyberte knihovny DLL v Průvodce projektem a potom přidat hlavičky souboru giraffe.h a kód souboru giraffe.cpp a zkopírujte obsah z kódu v tomto kroku do aplikace ropriate soubory.

   Kód definuje makro `GIRAFFE_API` která se přeloží na **__declspec(dllexport)** při `_DLL` je definován (při sestavení projektu jako knihovny DLL).

2. Otevřít **vlastnosti projektu** pro projekt knihovny DLL a nastavte **konfigurace** k **všechny konfigurace**.

3. V **vlastnosti projektu**v části **C/C++** > **Obecné** kartu, nastavte **využívat rozšíření modulu Runtime Windows** k  **Ano (/ZW)**. To umožňuje rozšíření komponent (C + +/ CX).

4. V **Průzkumníka řešení**, vyberte uzel projektu, otevřete místní nabídku a zvolte **uvolnit projekt**. Pak otevřete místní nabídku uzlu uvolnit projekt a zvolte pro úpravu souboru projektu. Vyhledejte `WindowsTargetPlatformVersion` prvku a nahraďte ji metodou následující prvky.

    ```xml
    <AppContainerApplication>true</AppContainerApplication>
    <ApplicationType>Windows Store</ApplicationType>
    <WindowsTargetPlatformVersion>10.0.10156.0</WindowsTargetPlatformVersion>
    <WindowsTargetPlatformMinVersion>10.0.10156.0</WindowsTargetPlatformMinVersion>
    <ApplicationTypeRevision>10.0</ApplicationTypeRevision>
    ```

   Zavřete soubor .vcxproj, znovu otevřete místní nabídku a zvolte **znovu načíst projekt**.

   **Průzkumník řešení** nyní identifikuje projekt jako projekt Windows Universal.

5. Ujistěte se, že je správný název souboru předkompilované hlavičky. V **předkompilované hlavičky** oddíl, změna **předkompilovaný soubor hlaviček** z soubor pch.h do stdafx.h. Pokud to neuděláte, se zobrazí následující chyba.

   > Chyba C2857: "#include" ve zdrojovém souboru nebyl nalezen zadaný pomocí možnosti příkazového řádku /Ycpch.h – příkaz

   Tento problém je, že projekty pro Universal Windows použít různé zásady vytváření názvů pro soubor předkompilované hlavičky.

6. Sestavte projekt. Může se zobrazit některé chyby týkající se možnosti nekompatibilní příkazového řádku. Například často používané možnosti **povolit minimální opětovné sestavení (/ Gm)** nastavena ve výchozím nastavení v mnoha projektů C++ a není kompatibilní s `/ZW`.

   Některé funkce nebudou k dispozici při kompilaci pro univerzální platformu Windows. Zobrazí se chyby kompilátoru případné potíže. Řeší nezaevidovali čisté sestavení.

7. Použití knihovny DLL v aplikaci UWP ve stejném řešení, otevřete místní nabídku pro uzel projektu UPW a zvolte **přidat** > **odkaz**.

   V části **projekty** > **řešení**, zaškrtněte políčko vedle projektu knihovny DLL a zvolte **OK** tlačítko.

8. Soubory hlaviček knihovny zahrňte soubor pch.h aplikaci UPW.

    ```cpp
    #include "..\MyNativeDLL\giraffe.h"
    ```

9. Přidejte kód jako obvykle v projektu UWP k vyvolání funkce a vytvořit typy z knihovny DLL.

    ```cpp
    MainPage::MainPage()
    {
        InitializeComponent();
        GiraffeFactory gf;
        Giraffe* g = gf.Create();
        int id = g->GetID();
    }
    ```

##  <a name="BK_StaticLib"></a> Pomocí nativní statickou knihovnu C++ v aplikaci UWP

Můžete použít nativní statickou knihovnu C++ v projektu UWP, ale existují některá omezení a omezení je potřeba vědět. Začněte tím, že výklad o [statické knihovny v jazyce C + +/ CX](../cppcx/static-libraries-c-cx.md). Nativní kód se dá dostat do statické knihovny z vaší aplikace pro UPW, ale nedoporučujeme k vytvoření typů public ref ve statické knihovně. Pokud kompilujete s statickou knihovnu `/ZW` možnost, varuje librarian (ve skutečnosti linkeru v maskování):

> LNK4264: archivace objektový soubor zkompiloval s parametrem /ZW do statické knihovny. Všimněte si, že při vytváření typů prostředí Windows Runtime nedoporučuje propojení se statickou knihovnou, která obsahuje metadata prostředí Windows Runtime

Můžete však použít statické knihovny v UPW bez opětovné kompilace s `/ZW`. Není možné deklarovat typy, které ref nebo použít C + +/ CX vytvoří, ale pokud vaše účelem je jednoduše použití knihovny nativního kódu a můžete tak učinit pomocí následujících kroků.

### <a name="to-use-a-native-c-static-library-in-a-uwp-project"></a>Použít nativní statickou knihovnu C++ v projektu UWP

1. Ve vlastnostech projektu pro projekt UPW v **Linkeru** části, přidejte cestu ke knihovně v **vstup** vlastnost. Například pro knihovnu v projektu, který se umístí výstup ve *SolutionFolder*\Debug\MyNativeLibrary\MyNativeLibrary.lib, zadejte relativní cestu `Debug\MyNativeLibrary\MyNativeLibrary.lib`.

2. Přidejte příkaz zahrnutí odkazu na soubor hlaviček pro váš soubor pch.h v projektu UWP a začněte přidávat kód, který používá knihovnu.

   ```cpp
   #include "..\MyNativeLibrary\giraffe.h"
   ```

   Nepřidávejte odkaz **odkazy** uzel v **Průzkumníka řešení**. Tento mechanismus funguje jenom pro komponenty Windows Runtime.

##  <a name="BK_WinRTComponent"></a> Portování knihovnu C++ ke komponentě ve Windows Runtime

Pokud chcete používat nativní rozhraní API ve statické knihovně z aplikace pro UPW, a vy musíte zdrojový kód pro nativní knihovnu, je port kód ke komponentě ve Windows Runtime. Statická knihovna již nebude, bude knihovny DLL. Můžete ji použít v jakékoli aplikaci C++ UWP, ale na rozdíl od případu statická knihovna, můžete přidat typy odkazu a ostatní C + +/ CX konstrukce, které jsou k dispozici pro klienty v žádný kód aplikace UPW, bez ohledu na jazyk. Proto můžete přistupovat těchto typů z jazyka C#, Visual Basic nebo JavaScript.  Základní postup je vytvořit projekt pro součást prostředí Windows Runtime, do něj zkopírovat kód pro statické knihovny a vyřešit všechny chyby, které vznikají v přechod ze standardní kompilace jazyka C++ na kód `/ZW` kompilace.

### <a name="to-port-a-c-library-to-a-windows-runtime-component"></a>K portu knihovny C++ ke komponentě ve Windows Runtime

1. Vytvořte projekt pro součást prostředí Windows Runtime.

2. Zavřete projekt.

3. V **Průzkumníka souborů Windows**, najít projekt. Ve výchozím nastavení používá Visual Studio ve složce Dokumenty 2017\Projects složky sady Visual Studio. Vyhledejte projekt knihovny C++, který obsahuje kód, který chcete port. Zkopírujte zdrojové soubory (hlavičkové soubory, soubory kódu a všechny další prostředky, včetně v podadresářích) z projektu knihovny jazyka C++ a vložte je do složky projektu a ujistěte se, chcete-li zachovat stejné struktury složek.

4. Znovu otevřete projekt pro součást prostředí Windows Runtime a otevřete místní nabídku pro uzel projektu v **Průzkumníka řešení**a zvolte **přidat** > **existující položku**.

5. Vyberte všechny soubory pro přidání z původní projekt a zvolte **OK**. Opakujte, pokud je to nutné pro podsložky.

6. Může být nyní některé duplikovali jste kód. Pokud máte více než jeden předkompilované hlavičky (třeba stdafx.h a soubor pch.h), vyberte z nich se má zachovat. Zkopírujte všechny kódu, jako například zahrnovat příkazy do ta, kterou už vedení. Odstraňte vlastnosti dalších a v projektu v části **předkompilované hlavičky**, ujistěte se, že je správný název souboru hlaviček.

   Pokud jste změnili soubor, který má používat jako předkompilované hlavičky, ujistěte se, že jsou správné pro každý soubor možností předkompilovaných hlaviček. Pak vyberte každý soubor .cpp, otevřete její okno Vlastnosti a ujistěte se, že všechny jsou nastaveny na **použití (/Yu)**, s výjimkou požadované předkompilované hlavičky, které by mělo být nastavené **vytvořit (/Yc)**.

7. Sestavte projekt a vyřešte všechny chyby. Tyto chyby může být způsobena použitím `/ZW` možnost, nebo může být způsobena novou verzi sady Windows SDK nebo se může dojít k tomu závislosti, jako jsou hlavičkové soubory, knihovny, na kterých závisí nebo rozdíly v nastavení projektu mezi tvojí projekt a novým.

8. Do projektu přidejte typy public ref nebo převést běžné typy na typech, ke zveřejnění vstupních bodů do funkce, které chcete volat z aplikací pro UWP.

9. Otestovat součást přidáním na ni odkaz z projektu aplikace UPW a přidejte nějaký kód do volání veřejné rozhraní API služby jste vytvořili.

## <a name="see-also"></a>Viz také:

[Přenos aplikací do platformy Universal Windows](../porting/porting-to-the-universal-windows-platform-cpp.md)
