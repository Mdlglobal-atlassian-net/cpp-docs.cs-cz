---
title: DLLs (C++/CX)
ms.date: 02/06/2018
ms.assetid: 5b8bcc57-64dd-4c54-9f24-26a25bd5dddd
ms.openlocfilehash: 4db0ed4f11f03c65c440c7b654653347da1d4536
ms.sourcegitcommit: 180f63704f6ddd07a4172a93b179cf0733fd952d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70740262"
---
# <a name="dlls-ccx"></a>DLLs (C++/CX)

Můžete použít aplikaci Visual Studio k vytvoření standardní knihovny DLL Win32 nebo knihovny DLL prostředí Windows Runtime komponenty, které mohou být spotřebovány aplikacemi Univerzální platforma Windows (UWP). Standardní knihovna DLL, která byla vytvořena pomocí verze sady Visual Studio nebo kompilátoru společnosti Microsoft C++ , která je starší než Visual Studio 2012, se nemusí správně načíst v aplikaci pro UWP a nemůže předat ověřovací test aplikace v Microsoft Store.

## <a name="windows-runtime-component-dlls"></a>Knihovny DLL prostředí Windows Runtime komponent

V téměř všech případech, pokud chcete vytvořit knihovnu DLL pro použití v aplikaci UWP, ji vytvořte jako komponentu prostředí Windows Runtime pomocí šablony projektu daného názvu. Můžete vytvořit projekt komponenty prostředí Windows Runtime pro knihovny DLL, které mají typy Public nebo Private prostředí Windows Runtime. K prostředí Windows Runtime komponentě se dá dostat z aplikací, které jsou napsané v jakémkoli jazyce kompatibilním s prostředí Windows Runtime. Ve výchozím nastavení má nastavení kompilátoru pro projekt komponenty prostředí Windows Runtime použít přepínač **/ZW** . Soubor. winmd musí mít stejný název, který má kořenový obor názvů. Například třída s názvem A. B. C. MyClass může být vytvořena pouze v případě, že je definována v souboru metadat s názvem A. winmd nebo A. B. winmd nebo A. B. C. winmd. Název knihovny DLL není nutné odpovídat názvu souboru. winmd.

Další informace naleznete v tématu [Creating prostředí Windows Runtime Components C++in ](/windows/uwp/winrt-components/creating-windows-runtime-components-in-cpp).

### <a name="to-reference-a-third-party-windows-runtime-component-binary-in-your-project"></a>Odkazování na binární soubor komponenty prostředí Windows Runtime třetí strany v projektu

1. Otevřete místní nabídku pro projekt, který bude používat knihovnu DLL, a pak zvolte možnost **vlastnosti**. Na stránce **společné vlastnosti** klikněte na tlačítko **Přidat nový odkaz** .

1. Komponenta prostředí Windows Runtime se skládá ze souboru DLL a souboru. winmd, který obsahuje metadata. Obvykle se tyto soubory nacházejí ve stejné složce. V levém podokně dialogového okna **Přidat odkaz** klikněte na tlačítko **Procházet** a potom přejděte do umístění knihovny DLL a jejího souboru winmd. Další informace najdete v tématu [rozšiřující sady SDK](/visualstudio/extensibility/creating-a-software-development-kit#extension-sdks).

## <a name="standard-dlls"></a>Standardní knihovny DLL

Můžete vytvořit standardní knihovnu DLL pro C++ kód, který nespotřebovává nebo produkuje veřejné prostředí Windows Runtime typy a spotřebovat ho z aplikace pro UWP. Použijte typ projektu dynamické knihovny (DLL), pokud chcete pouze migrovat existující knihovnu DLL pro kompilaci v této verzi sady Visual Studio, ale nikoli převést kód na projekt prostředí Windows Runtime komponenty. Použijete-li následující postup, knihovna DLL bude nasazena společně se spustitelným souborem aplikace v balíčku. appx.

### <a name="to-create-a-standard-dll-in-visual-studio"></a>Vytvoření standardní knihovny DLL v aplikaci Visual Studio

1. Na panelu nabídek zvolte položku **soubor**, **Nový**, **projekt**a potom vyberte šablonu **Knihovna DLL (Dynamic Link Library)** .

1. Zadejte název projektu a pak klikněte na tlačítko **OK** .

1. Přidejte kód. Nezapomeňte použít `__declspec(dllexport)` pro funkce, které máte v úmyslu exportovat – například`__declspec(dllexport) Add(int I, in j);`

1. Přidejte `#include winapifamily.h` pro zahrnutí tohoto souboru hlaviček z Windows SDK pro aplikace pro UWP a nastavte makro `WINAPI_FAMILY=WINAPI_PARTITION_APP`.

### <a name="to-reference-a-standard-dll-project-from-the-same-solution"></a>Odkazování na standardní projekt knihovny DLL ze stejného řešení

1. Otevřete místní nabídku pro projekt, který bude používat knihovnu DLL, a pak zvolte možnost **vlastnosti**. Na stránce **společné vlastnosti** klikněte na tlačítko **Přidat nový odkaz** .

1. V levém podokně vyberte **řešení**a potom zaškrtněte příslušné políčko v pravém podokně.

1. V souborech zdrojového kódu přidejte `#include` příkaz pro hlavičkový soubor DLL podle potřeby.

### <a name="to-reference-a-standard-dll-binary"></a>Odkazování na standardní binární soubor DLL

1. Zkopírujte soubor DLL, soubor. lib a hlavičkový soubor a vložte je do známého umístění, například do složky aktuálního projektu.

1. Otevřete místní nabídku pro projekt, který bude používat knihovnu DLL, a pak zvolte možnost **vlastnosti**. Na stránce **Vlastnosti konfigurace**, **linker**, **vstupní** stránka přidejte soubor. lib jako závislost.

1. V souborech zdrojového kódu přidejte `#include` příkaz pro hlavičkový soubor DLL podle potřeby.

### <a name="to-migrate-an-existing-win32-dll-for-uwp-app-compatibility"></a>Migrace stávající knihovny DLL Win32 pro kompatibilitu aplikací pro UWP

1. Vytvořte projekt typu DLL (univerzální pro Windows) a přidejte do něj svůj existující zdrojový kód.

1. Přidejte `#include winapifamily.h` pro zahrnutí tohoto souboru hlaviček z Windows SDK pro aplikace pro UWP a nastavte makro `WINAPI_FAMILY=WINAPI_PARTITION_APP`.

1. V souborech zdrojového kódu přidejte `#include` příkaz pro hlavičkový soubor DLL podle potřeby.
