---
title: 'Návody: Použití existujícího kódu C++ v aplikaci pro univerzální platformu pro Windows'
ms.date: 04/08/2019
ms.assetid: 87e5818c-3081-42f3-a30d-3dca2cf0645c
ms.openlocfilehash: b1351a1c7858b00cffc454fa66831b3995aea804
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81366433"
---
# <a name="how-to-use-existing-c-code-in-a-universal-windows-platform-app"></a>Návody: Použití existujícího kódu C++ v aplikaci pro univerzální platformu pro Windows

Snad nejjednodušší způsob, jak získat váš desktopový program běží v prostředí Univerzální platforma Windows (UPW) je použití technologie Desktop Bridge. Patří mezi ně Převaděč desktopových aplikací, který zabalí stávající aplikaci jako aplikaci UPW bez nutnosti změn kódu. Další informace naleznete [v tématu Desktop Bridge](/windows/uwp/porting/desktop-to-uwp-root).

Zbývající část tohoto tématu popisuje, jak portovat knihovny Jazyka C++ (Knihovny DLL a statické knihovny) na univerzální platformu Windows. Můžete to chtít provést tak, aby vaše základní logika Jazyka C++ lze použít s více aplikacemi UPW.

Aplikace UPW se spouštějí v chráněném prostředí a v důsledku toho není povoleno mnoho volání rozhraní API Win32, COM a CRT, která by mohla ohrozit zabezpečení platformy. Kompilátor může rozpoznat taková volání a `/ZW` generovat chybu, pokud je použita možnost. Pomocí certifikační sady aplikací v aplikaci můžete zjistit kód, který volá zakázaná pravidla API. Další informace naleznete v [tématu Windows App Certification Kit](/windows/uwp/debug-test-perf/windows-app-certification-kit).

Pokud zdrojový kód je k dispozici pro knihovnu, může být možné eliminovat zakázaná volání rozhraní API. Podrobnosti včetně seznamu povolených nebo zakázaných polí API naleznete v tématu [Win32 a COM API pro aplikace UPW](/uwp/win32-and-com/win32-and-com-for-uwp-apps) a [funkce CRT, které nejsou podporovány v aplikacích univerzální platformy Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md). Některé alternativy lze nalézt na [alternativy k Windows API v aplikacích UPW](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).

Pokud se pokusíte přidat odkaz z univerzálního projektu Windows do klasické knihovny plochy, zobrazí se chybová zpráva, že knihovna není kompatibilní. V případě statické knihovny můžete odkazovat na knihovnu jednoduše přidáním knihovny (.lib soubor) do propojovacího zařízení vstup, stejně jako v klasické aplikaci Win32. Pro knihovny, kde je k dispozici pouze binární soubor, je to jediná možnost. Statická knihovna je propojená s spustitelným souborem vaší aplikace, ale knihovna DLL Win32, kterou využíváte v aplikaci UPW, musí být zabalena do aplikace tak, že ji zahrajete do projektu a označíte ji jako obsah. Chcete-li načíst knihovnu DLL win32 v aplikaci UPW, `LoadLibrary` `LoadLibraryEx`musíte také volat [LoadPackagedLibrary](/windows/win32/api/winbase/nf-winbase-loadpackagedlibrary) namísto nebo .

Pokud máte zdrojový kód pro knihovnu DLL nebo `/ZW` statickou knihovnu, můžete znovu zkompilovat jako projekt UPW. Pokud tak učiníte, můžete přidat odkaz pomocí **Průzkumníka řešení**a použít jej v aplikacích C++ UPW. V případě knihovny DLL propojíte knihovnu exportu.

Chcete-li zpřístupnit funkce volajícím v jiných jazycích, můžete knihovnu převést na součást prostředí Windows Runtime. Součásti prostředí Windows Runtime se liší od běžných knihoven DLL v tom, že obsahují metadata ve formě souborů .winmd, které popisují obsah způsobem, který potřebují spotřebitelé rozhraní .NET a JavaScript. Chcete-li zpřístupnit prvky rozhraní API do jiných jazyků, můžete přidat konstrukce jazyka C++/CX, například třídy ref, a zveřejnit je nebo použít [knihovnu šablon prostředí Windows Runtime C++ (WRL).](../windows/windows-runtime-cpp-template-library-wrl.md)  Ve Windows 10 a novějších můžete místo C++/CX použít [knihovnu C++/WinRT.](https://github.com/microsoft/cppwinrt)

Předchozí diskuse se nevztahuje na případ komponent modelu COM, které musí být zpracovány odlišně. Pokud máte server COM v exe nebo DLL, můžete jej použít v projektu Universal Windows, pokud jej zabalíte jako [komponentu COM bez registrace](/windows/win32/sbscs/creating-registration-free-com-objects), přidejte jej do projektu jako soubor obsahu a vytvořte jeho instanci pomocí [aplikace CoCreateInstanceFromApp](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstancefromapp). Další informace najdete [v tématu Použití volné služby DLL ve Windows Storu C++ Project .](https://blogs.msdn.microsoft.com/win8devsupport/2013/05/19/using-free-com-dll-in-windows-store-c-project/)

Pokud máte existující knihovnu modelu COM, kterou chcete přenést do ups, je možné ji převést na součást prostředí Windows Runtime pomocí [knihovny šablon prostředí Windows Runtime C++ (WRL).](../windows/windows-runtime-cpp-template-library-wrl.md) Wrl nepodporuje všechny funkce knihovny ATL a OLE, takže zda takový port je proveditelné závisí na tom, jak moc kód COM závisí na jaké funkce COM, ATL a OLE komponenty vyžaduje.

Jedná se o různé způsoby, které můžete použít existující kód Jazyka C++ v projektech UPW. Některé způsoby nevyžadují kód, který má být znovu zkompilován s povolenými rozšířeními `/ZW` komponent (C++/CX) (tj. s možností) a některé ano, takže pokud potřebujete zachovat kód ve standardním jazyce C++, nebo zachovat klasické prostředí kompilace Win32 pro nějaký kód, můžete tak učinit s příslušnými volbami architektury. Například veškerý kód, který obsahuje uzly AWW a typy, které mají být vystaveny volajícím jazyka C#, Visual Basic a JavaScript, by měl být v projektech aplikací pro Windows a v projektech komponent windows runtime. Kód, který musí být spotřebována pouze v kódu Jazyka C++ (včetně Jazyka C++/CX), může být buď v projektu, který se zkompiluje s `/WX` možností, nebo standardním projektem Jazyka C++. Kód pouze pro binární soubory lze použít propojením jako statické knihovny nebo zabaleno s aplikací jako obsah a načteno do knihovny DLL pouze v případě, že nepoužívá zakázaná řešení API.

Bez ohledu na to, který z těchto scénářů vývoje zvolíte, měli byste si být vědomi počtu definic maker, které můžete použít v kódu, takže můžete zkompilovat kód podmíněně pod klasickou plochu Win32 a UPW.

```cpp
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PC_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PHONE_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_DESKTOP)
```

Tyto příkazy se vztahují na aplikace UPW, aplikace pro Windows Phone Store, obojí nebo ani jedno (pouze klasické stolní počítače Win32). Tato makra jsou k dispozici pouze v systému Windows SDK 8.1 a novější, takže pokud váš kód potřebuje kompilovat s dřívějšími verzemi sady Windows SDK nebo pro jiné platformy kromě systému Windows, měli byste také zvážit případ, že žádný z nich nejsou definovány.

V tomto tématu najdete následující postupy:

- [Použití dll Win32 v aplikaci UPW](#BK_Win32DLL)

- [Použití nativní statické knihovny C++ v aplikaci UPW](#BK_StaticLib)

- [Přenesení knihovny jazyka C++ do součásti prostředí Windows Runtime](#BK_WinRTComponent)

## <a name="using-a-win32-dll-in-a-uwp-app"></a><a name="BK_Win32DLL"></a>Použití dll Win32 v aplikaci UPW

Pro lepší zabezpečení a spolehlivost běží univerzální aplikace windows v omezeném prostředí runtime, takže nemůžete používat pouze nativní dll tak, jak byste to udělali v klasické desktopové aplikaci pro Windows. Pokud máte zdrojový kód pro DLL, můžete port kód tak, aby jej běží na UPW. Můžete začít změnou několik nastavení projektu a metadat souboru projektu k identifikaci projektu jako projektu UPW. Kód knihovny je třeba `/ZW` zkompilovat pomocí možnosti, která umožňuje C++/CX. Některá volání rozhraní API nejsou povolena v aplikacích UPW z důvodu přísnějších ovládacích prvků přidružených k tomuto prostředí. Viz [Win32 a COM API pro aplikace UPW](/uwp/win32-and-com/win32-and-com-for-uwp-apps).

Následující postup platí pro případ, kdy máte nativní knihovnu `__declspec(dllexport)`DLL, která zveřejňuje funkce pomocí .

### <a name="to-port-a-native-dll-to-the-uwp-without-creating-a-new-project"></a>Portovat nativní dll do UPW bez vytvoření nového projektu

1. Pokud máte nativní dll, která `__declspec(dllexport)`exportuje funkce pomocí , můžete volat tyto funkce z aplikace UPW rekompilací DLL jako projektu UPW. Předpokládejme například, že máme dll, která exportuje několik tříd a jejich metody, s kódem, jako je následující soubor záhlaví:

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

   A následující soubor kódu:

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

   Vše ostatní v projektu (stdafx.h, dllmain.cpp) je součástí standardní šablony projektu Win32. Pokud chcete postupovat podle následujících kroků, ale nechcete používat vlastní dll ještě s těmito kroky, zkuste vytvořit projekt Win32, vyberte DLL v průvodci projektu a pak přidejte hlavičkový soubor giraffe.h a soubor kódu giraffe.cpp a zkopírujte obsah z kódu v tomto kroku do příslušných souborů.

   Kód definuje makro, `GIRAFFE_API` které se `__declspec(dllexport)` `_DLL` překládá na when is defined (to znamená, když je projekt sestaven jako DLL).

2. Otevřete **vlastnosti projektu DLL** a nastavte **konfiguraci** na **všechny konfigurace**.

3. V části **Vlastnosti projektu**v části **Obecné karty C/C++** > **General** nastavte **položku Consume Windows Runtime Extension** na **Yes (/ZW)**. To umožňuje rozšíření komponent (C++/CX).

4. V **Průzkumníku řešení**vyberte uzel projektu, otevřete místní nabídku a zvolte **Uvolnit project**. Potom otevřete místní nabídku v uvolněném uzlu projektu a zvolte úpravu souboru projektu. Vyhledejte `WindowsTargetPlatformVersion` prvek a nahraďte jej následujícími prvky.

    ```xml
    <AppContainerApplication>true</AppContainerApplication>
    <ApplicationType>Windows Store</ApplicationType>
    <WindowsTargetPlatformVersion>10.0.10156.0</WindowsTargetPlatformVersion>
    <WindowsTargetPlatformMinVersion>10.0.10156.0</WindowsTargetPlatformMinVersion>
    <ApplicationTypeRevision>10.0</ApplicationTypeRevision>
    ```

   Zavřete soubor .vcxproj, znovu otevřete místní nabídku a zvolte **Znovu načíst Project**.

   **Průzkumník řešení** nyní identifikuje projekt jako projekt univerzálního systému Windows.

5. Zkontrolujte, zda je název předkompilovaného souboru záhlaví správný. V části **Předkompilované hlavičky** změňte **předkompilovaný soubor hlaviček** z *pch.h* na *stdafx.h*. Pokud tak neučiníte, zobrazí se následující chyba.

   > Chyba C2857: Příkaz #include zadaný s možností příkazového řádku /Ycpch.h nebyl ve zdrojovém souboru nalezen.

   Problém je, že projekty univerzální windows použít jinou konvenci pojmenování pro předkompilovaný soubor záhlaví.

6. Sestavte projekt. Může se stát, že se u nekompatibilních možností příkazového řádku zobrazí některé chyby. Například nyní zastaralé, ale často používané **možnosti Povolit minimální znovusestavit (/Gm)** je nastavena ve výchozím `/ZW`nastavení v mnoha starších projektech Jazyka C++ a není kompatibilní s .

   Některé funkce nejsou k dispozici při kompilaci pro univerzální platformu Windows. Zobrazí se chyby kompilátoru o všech problémech. Oslovte je, dokud nebudete mít čisté sestavení.

7. Chcete-li použít dll v aplikaci UPW ve stejném řešení, otevřete místní nabídku pro uzel projektu UPW a zvolte **Přidat** > **odkaz**.

   V části **Projekty** > **řešení**zaškrtněte políčko vedle projektu DLL a zvolte tlačítko **OK.**

8. Zahrňte soubory záhlaví knihovny do souboru *pch.h* aplikace UPW.

    ```cpp
    #include "..\MyNativeDLL\giraffe.h"
    ```

9. Přidejte kód jako obvykle v projektu UPW k vyvolání funkcí a vytvoření typů z dll.

    ```cpp
    MainPage::MainPage()
    {
        InitializeComponent();
        GiraffeFactory gf;
        Giraffe* g = gf.Create();
        int id = g->GetID();
    }
    ```

## <a name="using-a-native-c-static-library-in-a-uwp-app"></a><a name="BK_StaticLib"></a>Použití nativní statické knihovny C++ v aplikaci UPW

Můžete použít nativní c++ statické knihovny v projektu UPW, ale existují určitá omezení a omezení být vědomi. Začněte čtením o [statických knihovnách v jazyce C++/CX](../cppcx/static-libraries-c-cx.md). Nativní kód ve statické knihovně můžete přistupovat z aplikace UPW, ale nedoporučuje se vytvářet veřejné typy odkazů v takové statické knihovně. Pokud zkompilujete `/ZW` statickou knihovnu s možností, knihovník (ve skutečnosti linker v přestrojení) varuje:

> LNK4264: archivace souboru objektu zkompilovaného pomocí /ZW do statické knihovny; Všimněte si, že při vytváření typů prostředí Windows Runtime se nedoporučuje propojovat se statickou knihovnou, která obsahuje metadata prostředí Windows Runtime

Statickou knihovnu však můžete použít v upanovém `/ZW`programu BEZ nutnosti její opětovné kompilace pomocí aplikace . Nebudete moci deklarovat žádné typy odkazů nebo používat konstrukce Jazyka C++/CX, ale pokud je vaším účelem jednoduše použít knihovnu nativního kódu, můžete tak učinit pomocí následujících kroků.

### <a name="to-use-a-native-c-static-library-in-a-uwp-project"></a>Použití nativní statické knihovny jazyka C++ v projektu UPW

1. Ve vlastnostech projektu projektu UPW zvolte**vstup**  > **linkeru** >  **vlastností konfigurace**v levém podokně. V pravém podokně přidejte cestu do knihovny ve vlastnosti **Další závislosti.** Například pro knihovnu v projektu, která umístí svůj výstup do *složky SolutionFolder*\Debug\MyNativeLibrary\MyNativeLibrary.lib, přidejte relativní cestu `Debug\MyNativeLibrary\MyNativeLibrary.lib`.

2. Přidejte příkaz include, který odkazuje na soubor záhlaví do souboru *pch.h* (pokud je k dispozici) nebo do libovolného souboru CPP podle potřeby a začněte přidávat kód, který používá knihovnu.

   ```cpp
   #include "..\MyNativeLibrary\giraffe.h"
   ```

   Nepřidávejte odkaz v uzlu **Odkazy** v **Průzkumníku řešení**. Tento mechanismus funguje pouze pro součásti prostředí Windows Runtime Components.

## <a name="porting-a-c-library-to-a-windows-runtime-component"></a><a name="BK_WinRTComponent"></a>Přenesení knihovny jazyka C++ do součásti prostředí Windows Runtime

Pokud chcete využívat nativní api ve statické knihovně z aplikace UPW a máte zdrojový kód pro nativní knihovnu, můžete přenést kód do součásti prostředí Windows Runtime. Už to nebude statická knihovna, bude to Knihovna DLL. Můžete jej použít v libovolné aplikaci C++ Upw, ale na rozdíl od statické knihovny můžete přidat typy odkazů a další konstrukce Jazyka C++/CX, které jsou klientům k dispozici v libovolném kódu aplikace UPW, bez ohledu na jazyk. Proto můžete přistupovat k těmto typům z jazyka C#, Visual Basic nebo JavaScript.  Základním postupem je vytvoření projektu součásti prostředí Windows Runtime, zkopírování kódu pro statickou knihovnu a řešení všech chyb, `/ZW` které vznikají přesunutím kódu ze standardní kompilace jazyka C++ do kompilace.

### <a name="to-port-a-c-library-to-a-windows-runtime-component"></a>Port knihovny Jazyka C++ do součásti prostředí Windows Runtime

1. Vytvořte projekt součásti prostředí Windows Runtime.

2. Zavřete projekt.

3. V **Průzkumníkovi souborů windows**vyhledejte projekt. Ve výchozím nastavení používá Visual Studio složku Visual Studio 2017\Projekty ve složce Dokumenty. Vyhledejte projekt knihovny C++, který obsahuje kód, který chcete portovat. Zkopírujte zdrojové soubory (soubory hlaviček, soubory kódu a další prostředky, včetně podadresářů) z projektu knihovny jazyka C++ a vložte je do složky projektu a zachovejte stejnou strukturu složek.

4. Znovu otevřete projekt součásti prostředí Windows Runtime a otevřete místní nabídku uzlu projektu v **Průzkumníku řešení**a zvolte **Přidat** > **existující položku**.

5. Vyberte všechny soubory, které chcete přidat z původního projektu, a zvolte **OK**. V případě potřeby opakujte pro podsložky.

6. Nyní můžete mít nějaký duplicitní kód. Pokud máte více než jednu předkompilovanou hlavičku (řekněme *stdafx.h* a *pch.h*), zvolte jednu, kterou chcete zachovat. Zkopírujte všechny požadované kódy, například zahrnout příkazy, do kódu, který zachováte. Potom odstraňte ostatní a ve vlastnostech projektu v části **Předkompilované záhlaví**, ujistěte se, že název souboru záhlaví je správný.

   Pokud jste změnili soubor, který chcete použít jako předkompilované záhlaví, ujistěte se, že předkompilované možnosti záhlaví jsou správné pro každý soubor. Vyberte každý soubor CPP podle pořadí, otevřete jeho vlastnosti okna a ujistěte se, že všechny jsou nastaveny na **Použití (/Yu)**, s výjimkou požadované předkompilované záhlaví, které by měly být nastaveny na **Vytvořit (/Yc)**.

7. Sestavte projekt a vyřešte všechny chyby. Tyto chyby mohou být `/ZW` způsobeny použitím této možnosti nebo mohou být způsobeny novou verzí sady Windows SDK nebo mohou odrážet závislosti, jako jsou soubory hlaviček, na kterých závisí vaše knihovna, nebo rozdíly v nastavení projektu mezi starým projektem a novým projektem.

8. Přidejte veřejné typy ref do projektu nebo převeďte běžné typy na typy ref, abyste odhalili vstupní body do funkcí, které chcete volat z aplikací UPW.

9. Otestujte komponentu přidáním odkazu z projektu aplikace UPW a přidejte nějaký kód pro volání veřejných api, která jste vytvořili.

## <a name="see-also"></a>Viz také

[Přenos na univerzální platformu Windows](../porting/porting-to-the-universal-windows-platform-cpp.md)
