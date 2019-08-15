---
title: 'Postupy: Použití existujícího C++ kódu v aplikaci Univerzální platforma Windows'
ms.date: 04/08/2019
ms.assetid: 87e5818c-3081-42f3-a30d-3dca2cf0645c
ms.openlocfilehash: e587ae88fe8d38a22b351d87ae585efe82acf091
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69510384"
---
# <a name="how-to-use-existing-c-code-in-a-universal-windows-platform-app"></a>Postupy: Použití existujícího C++ kódu v aplikaci Univerzální platforma Windows

Možná nejjednodušší způsob, jak si desktopový program běžící v prostředí Univerzální platforma Windows (UWP) použít k používání technologií pro stolní mosty. Patří sem převaděč desktopových aplikací, který zabalí existující aplikaci jako aplikaci UWP bez nutnosti změn kódu. Další informace najdete v tématu [most pro stolní počítače](/windows/uwp/porting/desktop-to-uwp-root).

Zbývající část tohoto tématu popisuje, jak portovat C++ knihovny (knihovny DLL a statické knihovny) do Univerzální platforma Windows. To můžete chtít udělat, aby se základní C++ logika mohla používat s více aplikacemi UWP.

Aplikace UWP běží v chráněném prostředí. v důsledku toho není možné narušit mnoho volání rozhraní API pro Win32, COM a CRT, která by mohla ohrozit zabezpečení platformy. Kompilátor může rozpoznat taková volání a generovat chybu, pokud `/ZW` je použita možnost. K detekci kódu, který volá zakázaná rozhraní API, můžete použít certifikační sadu aplikací v aplikaci. Další informace najdete v tématu [Certifikační sada aplikací pro Windows](/windows/uwp/debug-test-perf/windows-app-certification-kit).

Pokud je pro knihovnu k dispozici zdrojový kód, může být možné eliminovat zakázaná volání rozhraní API. Podrobnosti, včetně seznamu povolených nebo zakázaných rozhraní API, najdete v tématu [rozhraní API Win32 a com pro aplikace UWP](/uwp/win32-and-com/win32-and-com-for-uwp-apps) a [funkce CRT nejsou podporované v aplikacích Univerzální platforma Windows](../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md). Některé alternativy najdete [v alternativách k rozhraním API Windows v aplikacích pro UWP](/uwp/win32-and-com/alternatives-to-windows-apis-uwp).

Pokud se pouze pokusíte přidat odkaz z univerzálního projektu pro Windows do klasické desktopové knihovny, zobrazí se chybová zpráva s informací, že knihovna není kompatibilní. V případě statické knihovny můžete k vaší knihovně propojit jednoduše přidáním knihovny (soubor. lib) do vstupu linkeru, stejně jako v klasické aplikaci Win32. V případě knihoven, kde je k dispozici pouze binární soubor, je tato možnost jedinou možností. Statická knihovna je propojená se spustitelným souborem vaší aplikace, ale knihovna DLL Win32, kterou využíváte v aplikaci UWP, musí být zabalená do aplikace, a to tak, že ji zahrnete do projektu a označíte ji jako obsah. Pro načtení knihovny DLL Win32 v aplikaci UWP je také nutné volat [LoadPackagedLibrary](/windows/win32/api/winbase/nf-winbase-loadpackagedlibrary) namísto `LoadLibrary` nebo `LoadLibraryEx`.

Pokud máte zdrojový kód pro knihovnu DLL nebo statickou knihovnu, můžete znovu kompilovat s `/ZW` jako projekt UWP. Pokud to uděláte, můžete přidat odkaz pomocí **Průzkumník řešení**a použít ho v aplikacích pro C++ UWP. V případě knihovny DLL můžete propojit s knihovnou exportu.

Pro vystavení funkcí volajícím v jiných jazycích můžete knihovnu převést na součást prostředí Windows Runtime. Prostředí Windows Runtime komponenty se liší od běžných knihoven DLL v tom, že obsahují metadata ve formě souborů. winmd, které popisují obsah způsobem, který vyžadují uživatelé rozhraní .NET a JavaScriptu. Chcete-li vystavit prvky rozhraní API jiným jazykům, můžete přidat C++konstrukce/CX, jako jsou referenční třídy, a nastavit je jako veřejné, nebo použít [knihovnu šablon prostředí Windows Runtime C++ (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).  Ve Windows 10 a novějších verzích C++můžete místo/CX. použít [ C++knihovnu/WinRT](https://github.com/microsoft/cppwinrt) .

Předchozí diskuze se nevztahuje na případ komponent modelu COM, které se musí zpracovat jinak. Pokud máte server COM v souboru EXE nebo DLL, můžete jej použít v univerzálním projektu pro Windows, pokud ho zabalíte jako [komponentu com bez registrace](/windows/win32/sbscs/creating-registration-free-com-objects), přidáte ho do projektu jako soubor obsahu a vytvoříte jeho instanci pomocí [CoCreateInstanceFromApp](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstancefromapp). Další informace najdete v tématu [použití knihovny DLL Free-com v projektu C++ Windows Store](https://blogs.msdn.microsoft.com/win8devsupport/2013/05/19/using-free-com-dll-in-windows-store-c-project/).

Máte-li existující knihovnu COM, kterou chcete přenést na UWP, je možné ji převést na součást prostředí Windows Runtime pomocí [knihovny šablon prostředí Windows Runtime C++ (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md). WRL nepodporuje všechny funkce ATL a OLE, takže pokud je takový port vhodný, závisí na tom, jaké funkce modelu COM, ATL a OLE vaše komponenta vyžaduje.

Jedná se o různé způsoby, jak můžete použít existující C++ kód v projektech UWP. Některé způsoby nevyžadují, aby byl kód znovu zkompilován s povoleným rozšířenímC++(tj. s `/ZW` možností) a nějakým způsobem, takže pokud potřebujete zachovat kód ve standardu C++nebo zachovat klasické prostředí Win32 kompilace pro některé kód, můžete tak učinit s vhodnými volbami architektury. Například všechen váš kód, který obsahuje uživatelské rozhraní UWP a typy, které mají být vystaveny C#, Visual Basic a volání JavaScriptu by měly být v projektech aplikací pro Windows a v projektech prostředí Windows Runtime komponent. Kód, který je nutné spotřebovat pouze C++ v kódu C++(včetně/CX), může být buď v projektu, který je zkompilován `/WX` s možností nebo standardním C++ projektem. Pouze binární kód lze použít tak, že ho propojíte s jako statickou knihovnou nebo zabalíte do aplikace jako obsah a načtete v knihovně DLL pouze v případě, že nepoužívá zakázaná rozhraní API.

Bez ohledu na to, který z těchto scénářů vývoje zvolíte, byste měli mít na paměti několik definicí maker, které můžete použít v kódu, aby bylo možné kompilovat kód podmíněně v klasickém desktopovém prostředí Win32 i UWP.

```cpp
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PC_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_PHONE_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_APP)
#if WINAPI_FAMILY_PARTITION(WINAPI_PARTITION_DESKTOP)
```

Tyto příkazy se vztahují na aplikace pro UWP, aplikace Windows Phone Storu, nebo ani žádná (Klasická plocha Win32). Tato makra jsou k dispozici pouze v Windows SDK 8,1 a novějším, takže pokud váš kód potřebuje kompilovat s dřívějšími verzemi Windows SDK nebo pro jiné platformy než Windows, měli byste také vzít v úvahu případ, že není definován žádný z nich.

Toto téma obsahuje následující postupy:

- [Použití knihovny DLL Win32 v aplikaci UWP](#BK_Win32DLL)

- [Použití nativní C++ statické knihovny v aplikaci UWP](#BK_StaticLib)

- [Přenos C++ knihovny do součásti prostředí Windows Runtime](#BK_WinRTComponent)

##  <a name="BK_Win32DLL"></a>Použití knihovny DLL Win32 v aplikaci UWP

Pro lepší zabezpečení a spolehlivost aplikace pro univerzální aplikace pro Windows běží v běhovém prostředí s omezeným přístupem, takže nemůžete použít jenom nativní knihovnu DLL způsobem, který byste měli v klasické desktopové aplikaci Windows. Pokud máte zdrojový kód pro knihovnu DLL, můžete kód portovat tak, aby běžel na UWP. Začnete změnou několika nastavení projektu a metadaty souboru projektu k identifikaci projektu jako projektu UWP. Je nutné zkompilovat kód knihovny pomocí `/ZW` možnosti, která umožňuje/CX. C++ Některá volání rozhraní API se v aplikacích pro UWP nepovolují kvůli přísnějším kontrolám přidruženým k danému prostředí. Viz [rozhraní API Win32 a com pro aplikace UWP](/uwp/win32-and-com/win32-and-com-for-uwp-apps).

Následující postup platí pro případ, kde máte nativní knihovnu DLL, která zpřístupňuje funkce pomocí `__declspec(dllexport)`.

### <a name="to-port-a-native-dll-to-the-uwp-without-creating-a-new-project"></a>Pro přenos nativní knihovny DLL na UWP bez vytvoření nového projektu

1. Máte-li nativní knihovnu DLL, která exportuje funkce pomocí `__declspec(dllexport)`, můžete tyto funkce volat z aplikace UWP tím, že knihovnu DLL znovu zkompilujete jako projekt UWP. Předpokládejme například, že máme knihovnu DLL, která exportuje několik tříd a jejich metody s kódem, jako je následující hlavičkový soubor:

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

   Všechno ostatní v projektu (stdafx. h, DllMain. cpp) je součástí standardní šablony projektu Win32. Pokud chcete postupovat podle, ale nechcete používat vlastní knihovnu DLL ještě v těchto krocích, zkuste vytvořit projekt Win32, vybrat knihovnu DLL v Průvodci projektem a pak přidat hlavičkový soubor Giraffe. h a soubor kódu Giraffe. cpp a zkopírovat obsah z kódu v tomto kroku do aplikace. soubory ropriate.

   Kód definuje makro `GIRAFFE_API` , které se překládá na `_DLL` to `__declspec(dllexport)` , kdy je definována (to znamená, když je projekt sestaven jako knihovna DLL).

2. Otevřete **Vlastnosti projektu** pro projekt knihovny DLL a nastavte **konfiguraci** na **všechny konfigurace**.

3. Ve **vlastnostech projektu**na kartě >  **C/C++** **Obecné** nastavte použít **rozšíření prostředí Windows Runtime** na **Ano (/ZW)** . To umožňuje rozšíření komponent (C++/CX).

4. V **Průzkumník řešení**vyberte uzel projektu, otevřete místní nabídku a zvolte **Uvolnit projekt**. Pak otevřete místní nabídku na odpojeném uzlu projektu a zvolte možnost upravit soubor projektu. `WindowsTargetPlatformVersion` Vyhledejte prvek a nahraďte ho následujícími prvky.

    ```xml
    <AppContainerApplication>true</AppContainerApplication>
    <ApplicationType>Windows Store</ApplicationType>
    <WindowsTargetPlatformVersion>10.0.10156.0</WindowsTargetPlatformVersion>
    <WindowsTargetPlatformMinVersion>10.0.10156.0</WindowsTargetPlatformMinVersion>
    <ApplicationTypeRevision>10.0</ApplicationTypeRevision>
    ```

   Zavřete soubor. vcxproj, znovu otevřete místní nabídku a vyberte možnost **znovu načíst projekt**.

   **Průzkumník řešení** nyní identifikuje projekt jako univerzální projekt pro Windows.

5. Ujistěte se, že název souboru předkompilované hlavičky je správný. V sekci **předkompilované hlavičky** změňte **soubor předkompilované hlavičky** z PCH. h na Stdafx. h. Pokud to neuděláte, zobrazí se následující chyba.

   > Chyba C2857: příkaz ' #include ' zadaný s parametrem příkazového řádku/Ycpch.h nebyl nalezen ve zdrojovém souboru.

   Příčinou tohoto problému je, že univerzální projekty Windows používají jiné zásady vytváření názvů pro soubor předkompilované hlavičky.

6. Sestavte projekt. Může se zobrazit několik chyb týkajících se nekompatibilních možností příkazového řádku. Například aktuálně zastaralá, ale často používaná možnost **Povolit minimální opětovné sestavení (/GM)** je ve výchozím nastavení nastavena v mnoha starších C++ projektech a není kompatibilní s `/ZW`.

   Některé funkce nejsou k dispozici při kompilaci Univerzální platforma Windows. V případě problémů se zobrazí chyby kompilátoru. Vyřešte je, dokud nebudete mít čisté sestavení.

7. Chcete-li použít knihovnu DLL v aplikaci UWP ve stejném řešení, otevřete místní nabídku uzlu projektu UWP a vyberte možnost **Přidat** > **odkaz**.

   V části**řešení** **projektů** > zaškrtněte políčko vedle projektu knihovny DLL a klikněte na tlačítko **OK** .

8. Do souboru PCH. h vaší aplikace pro UWP zahrňte soubory hlaviček knihovny.

    ```cpp
    #include "..\MyNativeDLL\giraffe.h"
    ```

9. Přidejte kód obvyklým způsobem v projektu UWP pro vyvolání funkcí a vytváření typů z knihovny DLL.

    ```cpp
    MainPage::MainPage()
    {
        InitializeComponent();
        GiraffeFactory gf;
        Giraffe* g = gf.Create();
        int id = g->GetID();
    }
    ```

##  <a name="BK_StaticLib"></a>Použití nativní C++ statické knihovny v aplikaci UWP

V projektu UWP můžete použít C++ nativní statickou knihovnu, ale existuje několik omezení a omezení, o kterých byste měli vědět. Začněte tím, že si přečtete informace o [statických knihovnách v C++/CX](../cppcx/static-libraries-c-cx.md). K nativnímu kódu ve vaší statické knihovně můžete přistupovat z aplikace pro UWP, ale nedoporučujeme vytvářet veřejné referenční typy v takové statické knihovně. Pokud zkompilujete statickou knihovnu s `/ZW` možností, Librarian (ve skutečnosti je linker v maskování) varuje:

> LNK4264: archivace souboru objektu kompilována s/ZW do statické knihovny; Pamatujte, že při vytváření prostředí Windows Runtime typů se nedoporučuje propojit se statickou knihovnou, která obsahuje prostředí Windows Runtime metadata.

Můžete však použít statickou knihovnu v UWP bez nutnosti jejich `/ZW`opětovné kompilace. Nebudete moci deklarovat žádné typy ref ani použít C++konstrukce/CX, ale pokud je vaším účelem jednoduše použít knihovnu nativního kódu, můžete to provést pomocí následujících kroků.

### <a name="to-use-a-native-c-static-library-in-a-uwp-project"></a>Použití nativní C++ statické knihovny v projektu UWP

1. Ve vlastnostech projektu pro projekt UWP v levém podokně vyberte možnost **vlastnosti** > konfigurace**linker** > **input** . V pravém podokně přidejte cestu ke knihovně do vlastnosti **Další závislosti** . Například pro knihovnu v projektu, který umístí svůj výstup do *SolutionFolder –* \Debug\MyNativeLibrary\MyNativeLibrary.lib, přidejte relativní cestu `Debug\MyNativeLibrary\MyNativeLibrary.lib`.

2. Přidejte příkaz include, který odkazuje na hlavičkový soubor na soubor PCH. h (Pokud je k dispozici), nebo v jakémkoli souboru. cpp podle potřeby a začněte přidávat kód, který používá knihovnu.

   ```cpp
   #include "..\MyNativeLibrary\giraffe.h"
   ```

   Nepřidávejte odkaz do uzlu **odkazy** v **Průzkumník řešení**. Tento mechanismus funguje jenom pro prostředí Windows Runtime komponenty.

##  <a name="BK_WinRTComponent"></a>Přenos C++ knihovny do součásti prostředí Windows Runtime

Pokud chcete využívat nativní rozhraní API ve statické knihovně z aplikace pro UWP a máte zdrojový kód pro nativní knihovnu, můžete kód portovat do prostředí Windows Runtime komponenty. Už nebude Statická knihovna, bude to knihovna DLL. Můžete ji použít v libovolné C++ aplikaci pro UWP, ale na rozdíl od velikosti statické knihovny můžete přidat typy ref a další C++konstrukce/CX, které jsou k dispozici pro klienty v jakémkoli kódu aplikace UWP bez ohledu na jazyk. Proto máte přístup k těmto typům z C#, Visual Basic nebo JavaScript.  Základní postup je vytvořit projekt komponenty prostředí Windows Runtime, zkopírovat kód pro statickou knihovnu do něj a vyřešit všechny chyby, které vznikají z přesunu kódu ze standardní C++ kompilace do `/ZW` kompilace.

### <a name="to-port-a-c-library-to-a-windows-runtime-component"></a>Postup při portování C++ knihovny pro komponentu prostředí Windows Runtime

1. Vytvořte projekt součásti prostředí Windows Runtime.

2. Zavřete projekt.

3. V **Průzkumníkovi souborů systému Windows**vyhledejte projekt. Ve výchozím nastavení používá Visual Studio složku projekty sady Visual Studio 2017 \ ve složce Dokumenty. Vyhledejte projekt C++ knihovny obsahující kód, který chcete přenést. Zkopírujte zdrojové soubory (soubory hlaviček, soubory kódu a všechny další prostředky, včetně v podadresářích) z projektu C++ knihovny a vložte je do složky projektu a nezapomeňte zachovat stejnou strukturu složek.

4. Znovu otevřete projekt součásti prostředí Windows Runtime a otevřete místní nabídku uzlu projektu v **Průzkumník řešení**a vyberte možnost **Přidat** > **existující položku**.

5. Vyberte všechny soubory, které chcete přidat z původního projektu, a zvolte **OK**. Pokud je to nutné pro podsložky, opakujte akci.

6. Teď můžete mít nějaký duplicitní kód. Pokud máte více než jednu předkompilovanou hlavičku (například stdafx. h a PCH. h), vyberte ji, kterou chcete zachovat. Zkopírujte libovolný požadovaný kód, například příkazy include, do kódu, který si zachováte. Pak odstraňte druhý a ve vlastnostech projektu v části **předkompilované hlavičky**Ujistěte se, že název souboru hlaviček je správný.

   Pokud jste soubor změnili tak, aby používal jako předkompilovanou hlavičku, ujistěte se, že možnosti předkompilovaných hlaviček jsou správné pro každý soubor. Postupně vyberte každý soubor. cpp, otevřete jeho okno Vlastnosti a ujistěte se, že všechny jsou nastaveny na **použití (/Yu)** , s výjimkou požadované předkompilované hlavičky, která by měla být nastavena na hodnotu **vytvořit (/Yc)** .

7. Sestavte projekt a vyřešte všechny chyby. Tyto chyby mohou být způsobeny použitím `/ZW` možnosti, nebo mohou být způsobeny novou verzí Windows SDK, nebo mohou odrážet závislosti, jako jsou soubory hlaviček, na kterých vaše knihovna závisí, nebo rozdíly v nastaveních projektu mezi vaší starou. projekt a nový.

8. Přidejte do projektu veřejné referenční typy nebo převeďte běžné typy na typy ref, abyste vystavili vstupní body do funkcionality, kterou chcete volat z aplikací UWP.

9. Otestujte komponentu tak, že do ní přidáte odkaz z projektu aplikace pro UWP a přidáte nějaký kód pro volání veřejných rozhraní API, které jste vytvořili.

## <a name="see-also"></a>Viz také:

[Portování do Univerzální platforma Windows](../porting/porting-to-the-universal-windows-platform-cpp.md)
