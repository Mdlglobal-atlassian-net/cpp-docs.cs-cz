---
title: 'Postupy: Vytvoření klasické komponenty COM s použitím knihovny WRL'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 5efe7690-90d5-4c3c-9e53-11a14cefcb19
ms.openlocfilehash: e19ff4a331a98e64c39dc2e163459b2696bbdee5
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/01/2019
ms.locfileid: "58786924"
---
# <a name="how-to-create-a-classic-com-component-using-wrl"></a>Postupy: Vytvoření klasické komponenty COM s použitím knihovny WRL

Windows Runtime C++ šablony knihovny (WRL) slouží k vytvoření základní komponenty modelu COM classic pro použití v aplikacích klasické pracovní plochy, kromě použití pro aplikace univerzální platformy Windows (UPW). Pro vytváření komponent modelu COM může knihovna šablon C++ Windows Runtime vyžadují méně kódu než knihovně ATL Informace o podmnožinu modelu COM, která knihovna šablon C++ Windows Runtime podporuje, najdete v tématu [Windows Runtime C++ šablony knihovny (WRL)](windows-runtime-cpp-template-library-wrl.md).

Tento dokument ukazuje, jak vytvořit základní komponenty modelu COM pomocí knihovny šablon jazyka C++ Runtime Windows. I když používáte mechanismus pro nasazení, který nejlépe vyhovuje vašim potřebám, tento dokument také ukazuje základní způsob, jak zaregistrovat a využívat komponenty modelu COM z desktopové aplikace.

### <a name="to-use-the-windows-runtime-c-template-library-to-create-a-basic-classic-com-component"></a>Použití knihovny šablon jazyka C++ Runtime Windows k vytvoření základní komponenty COM

1. V sadě Visual Studio, vytvořit **prázdné řešení** projektu. Název projektu, například `WRLClassicCOM`.

2. Přidat **projekt Win32** do řešení. Název projektu, například `CalculatorComponent`. Na **nastavení aplikace** kartu, vyberte možnost **DLL**.

3. Přidat **soubor Midl (.idl)** soubor do projektu. Název souboru, například `CalculatorComponent.idl`.

4. Tento kód vložte do CalculatorComponent.idl:

   [!code-cpp[wrl-classic-com-component#1](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_1.idl)]

5. V CalculatorComponent.cpp, definujte `CalculatorComponent` třídy. `CalculatorComponent` Třída dědí z [Microsoft::WRL::RuntimeClass](runtimeclass-class.md). [Microsoft::WRL::RuntimeClassFlags\<ClassicCom >](runtimeclassflags-structure.md) Určuje, že třída je odvozena z [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) a ne [IInspectable](/windows/desktop/api/inspectable/nn-inspectable-iinspectable). (`IInspectable` je dostupná jenom pro aplikace součástí prostředí Windows Runtime.) `CoCreatableClass` vytvoří objekt pro vytváření pro třídy, která lze použít s funkcemi, jako například [CoCreateInstance](/windows/desktop/api/combaseapi/nf-combaseapi-cocreateinstance).

   [!code-cpp[wrl-classic-com-component#2](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_2.cpp)]

6. Pomocí následujícího kódu do nahraďte kód v `dllmain.cpp`. Tento soubor definuje export funkcí knihovny DLL. Tyto funkce používají [Microsoft::WRL::Module](module-class.md) třídy spravovat objekty Factory třídy pro modul.

   [!code-cpp[wrl-classic-com-component#3](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_3.cpp)]

7. Přidat **souboru definice modulu (.def)** soubor do projektu. Název souboru, například `CalculatorComponent.def`. Tento soubor poskytuje linkeru názvy funkcí, které mají být exportovány.

8. Tento kód vložte do CalculatorComponent.def:

    ```
    LIBRARY

    EXPORTS
        DllGetActivationFactory PRIVATE
        DllGetClassObject       PRIVATE
        DllCanUnloadNow         PRIVATE
    ```

9. Přidáte runtimeobject.lib řádku linkeru. Další informace o postupu [. Lib soubory jako vstup Linkeru](../../build/reference/dot-lib-files-as-linker-input.md).

### <a name="to-consume-the-com-component-from-a-desktop-app"></a>Chcete-li využívat komponenty modelu COM z desktopové aplikace

1. Registrace komponenty modelu COM pomocí registru Windows. Chcete-li tak učinit, vytvořte soubor položky registrace, pojmenujte ho `RegScript.reg`a přidejte následující text. Nahraďte  *\<cesta ke knihovně dll >* s cestou vaše knihovna DLL – například `C:\temp\WRLClassicCOM\Debug\CalculatorComponent.dll`.

    ```
    Windows Registry Editor Version 5.00

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}]
    @="CalculatorComponent Class"

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\InprocServer32]
    @="<dll-path>"
    "ThreadingModel"="Apartment"

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\Programmable]

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\TypeLib]
    @="{9D3E6826-CB8E-4D86-8B14-89F0D7EFCD01}"

    [HKEY_CLASSES_ROOT\Wow6432Node\CLSID\{E68F5EDD-6257-4E72-A10B-4067ED8E85F2}\Version]
    @="1.0"
    ```

2. Spustit RegScript.reg nebo ho přidejte do svého projektu **post-build Event**. Další informace najdete v tématu [pre-build Event/po sestavení příkazového řádku dialogové okno události](/visualstudio/ide/reference/pre-build-event-post-build-event-command-line-dialog-box).

3. Přidat **Konzolová aplikace Win32** projektu do řešení. Název projektu, například `Calculator`.

4. Pomocí tohoto kódu nahraďte obsah `Calculator.cpp`:

   [!code-cpp[wrl-classic-com-component#6](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_6.cpp)]

## <a name="robust-programming"></a>Robustní programování

Tento dokument používá standardní funkce modelu COM prokázat, že vám pomůže knihovna šablon C++ Windows Runtime autorem komponenty modelu COM a zpřístupní ji pro jakékoli podporou modelu COM technologie. Můžete také použít typy knihovna šablon C++ Windows Runtime, jako [Microsoft::WRL::ComPtr](comptr-class.md) v desktopové aplikaci pro správu životního cyklu COM a jiných objektů. Následující kód používá knihovny šablon jazyka C++ Runtime Windows ke správě životnosti `ICalculatorComponent` ukazatele. `CoInitializeWrapper` Třídy je obálka RAII, který zaručuje, že je uvolněn knihovny modelu COM a také zaručuje, že outlives životního cyklu knihovny modelu COM `ComPtr` objekt inteligentního ukazatele.

[!code-cpp[wrl-classic-com-component#7](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_7.cpp)]

## <a name="see-also"></a>Viz také

[Knihovna šablon C++ prostředí Windows Runtime (WRL)](windows-runtime-cpp-template-library-wrl.md)