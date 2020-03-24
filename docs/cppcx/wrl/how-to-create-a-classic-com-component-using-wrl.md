---
title: 'Postupy: Vytvoření klasické komponenty COM s použitím knihovny WRL'
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: 5efe7690-90d5-4c3c-9e53-11a14cefcb19
ms.openlocfilehash: a1507a1a980dfd98a235b7456d73add955c02043
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80213912"
---
# <a name="how-to-create-a-classic-com-component-using-wrl"></a>Postupy: Vytvoření klasické komponenty COM s použitím knihovny WRL

Pomocí knihovny šablon prostředí Windows Runtime C++ (WRL) můžete vytvořit základní komponenty modelu COM pro použití v desktopových aplikacích, a to i v případě, že ji použijete pro aplikace Univerzální platforma Windows (UWP). Pro vytváření komponent modelu COM může knihovna šablon prostředí Windows Runtime C++ vyžadovat méně kódu než ATL. Informace o podmnožině modelu COM, kterou podporuje C++ knihovna šablon prostředí Windows Runtime, naleznete v tématu [Knihovna šablon prostředí Windows Runtime C++ (WRL)](windows-runtime-cpp-template-library-wrl.md).

Tento dokument ukazuje, jak použít knihovnu šablon C++ prostředí Windows Runtime k vytvoření základní komponenty modelu COM. I když můžete použít mechanismus nasazení, který nejlépe vyhovuje vašim potřebám, tento dokument také ukazuje základní způsob, jak registrovat a spotřebovávat komponentu modelu COM z desktopové aplikace.

### <a name="to-use-the-windows-runtime-c-template-library-to-create-a-basic-classic-com-component"></a>Použití knihovny šablon prostředí Windows Runtime C++ k vytvoření základní komponenty modelu COM Classic

1. V aplikaci Visual Studio vytvořte projekt **prázdného řešení** . Název projektu, například `WRLClassicCOM`.

2. Přidejte do řešení **projekt Win32** . Název projektu, například `CalculatorComponent`. Na kartě **nastavení aplikace** vyberte možnost **Knihovna DLL**.

3. Přidejte soubor **MIDL (. idl)** do projektu. Název souboru, například `CalculatorComponent.idl`.

4. Přidejte tento kód do CalculatorComponent. idl:

   [!code-cpp[wrl-classic-com-component#1](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_1.idl)]

5. V CalculatorComponent. cpp Definujte třídu `CalculatorComponent`. Třída `CalculatorComponent` dědí od [společnosti Microsoft:: WRL:: RuntimeClass](runtimeclass-class.md). [Microsoft:: WRL:: RuntimeClassFlags\<ClassicCom >](runtimeclassflags-structure.md) určuje, že třída je odvozena z rozhraní [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) a nikoli [IInspectable](/windows/win32/api/inspectable/nn-inspectable-iinspectable). (`IInspectable` je k dispozici pouze pro prostředí Windows Runtime součásti aplikace.) `CoCreatableClass` vytvoří objekt pro vytváření pro třídu, která se dá použít s funkcemi, jako je například funkce [CoCreateInstance](/windows/win32/api/combaseapi/nf-combaseapi-cocreateinstance).

   [!code-cpp[wrl-classic-com-component#2](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_2.cpp)]

6. Pomocí následujícího kódu nahraďte kód v `dllmain.cpp`. Tento soubor definuje funkce exportu knihovny DLL. Tyto funkce používají třídu třídy [Microsoft:: WRL:: Module](module-class.md) pro správu tříd Factory pro modul.

   [!code-cpp[wrl-classic-com-component#3](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_3.cpp)]

7. Přidejte do projektu soubor **definičního souboru modulu (. def)** . Název souboru, například `CalculatorComponent.def`. Tento soubor přidělí linkeru názvy funkcí, které mají být exportovány.

8. Přidejte tento kód do CalculatorComponent. def:

    ```
    LIBRARY

    EXPORTS
        DllGetActivationFactory PRIVATE
        DllGetClassObject       PRIVATE
        DllCanUnloadNow         PRIVATE
    ```

9. Přidejte runtimeobject. lib na řádek linkeru. Další informace najdete v tématu [. Soubory LIB jako vstup linkeru](../../build/reference/dot-lib-files-as-linker-input.md)

### <a name="to-consume-the-com-component-from-a-desktop-app"></a>Využití komponenty modelu COM z desktopové aplikace

1. Zaregistrujte komponentu COM v registru systému Windows. Provedete to tak, že vytvoříte soubor registračních položek, pojmenujte ho `RegScript.reg`a přidáte následující text. Nahraďte *\<DLL-path >* cestou k vaší knihovně DLL, například `C:\temp\WRLClassicCOM\Debug\CalculatorComponent.dll`.

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

2. Spusťte RegScript. reg nebo ho přidejte do **události po sestavení**projektu. Další informace naleznete v tématu [dialogové okno Příkazový řádek události před sestavením/po sestavení](/visualstudio/ide/reference/pre-build-event-post-build-event-command-line-dialog-box).

3. Přidejte do řešení projekt **konzolové aplikace Win32** . Název projektu, například `Calculator`.

4. Pomocí tohoto kódu nahraďte obsah `Calculator.cpp`:

   [!code-cpp[wrl-classic-com-component#6](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_6.cpp)]

## <a name="robust-programming"></a>Robustní programování

Tento dokument používá standardní funkce modelu COM k tomu, abyste předvedli C++ použití knihovny šablon prostředí Windows Runtime k vytvoření komponenty modelu COM a zpřístupnění jejího obsahu pro libovolnou technologii com. Můžete také použít prostředí Windows Runtime C++ typy knihoven šablon, jako je například [Microsoft:: WRL:: ComPtr](comptr-class.md) v desktopové aplikaci pro správu životnosti modelu COM a dalších objektů. Následující kód používá knihovnu šablon prostředí Windows Runtime C++ ke správě životního cyklu `ICalculatorComponent` ukazatele. Třída `CoInitializeWrapper` je obálka RAII, která zaručuje, že knihovna COM je uvolněna a také zaručuje, že životnost knihovny COM je živý objekt `ComPtr` inteligentní ukazatel.

[!code-cpp[wrl-classic-com-component#7](../codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_7.cpp)]

## <a name="see-also"></a>Viz také

[Knihovna šablon C++ prostředí Windows Runtime (WRL)](windows-runtime-cpp-template-library-wrl.md)
