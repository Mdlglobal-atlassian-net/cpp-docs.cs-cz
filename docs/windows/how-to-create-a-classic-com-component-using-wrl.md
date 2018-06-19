---
title: 'Postupy: vytvoření klasické komponenty COM s použitím knihovny WRL | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
ms.assetid: 5efe7690-90d5-4c3c-9e53-11a14cefcb19
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 00f00b265128ca388a3e9d4eb77631a320fbda81
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33880082"
---
# <a name="how-to-create-a-classic-com-component-using-wrl"></a>Postupy: Vytvoření klasické komponenty COM s použitím knihovny WRL
Windows Runtime C++ šablony knihovny (WRL) můžete použít k vytvoření základní klasické komponenty COM pro použití v aplikacích klasické pracovní plochy, kromě používání pro univerzální platformu Windows (UWP) aplikace. Vytváření komponenty modelu COM může knihovna šablon C++ Runtime Windows vyžadují méně kódu než ATL. Informace o podmnožinu COM, která podporuje knihovna šablon C++ Runtime Windows najdete v tématu [Windows Runtime C++ šablony knihovny (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).  
  
 Tento dokument ukazuje, jak vytvořit základní komponenty modelu COM pomocí knihovny šablon jazyka C++ Runtime systému Windows. Přestože je možné použít nasazení mechanismus, který nejlépe vyhovuje vašim potřebám, tento dokument také ukazuje základní způsob, jak zaregistrovat a využívat komponenty modelu COM z aplikace na ploše.  
  
### <a name="to-use-the-windows-runtime-c-template-library-to-create-a-basic-classic-com-component"></a>Použití knihovny šablon jazyka C++ Runtime Windows k vytvoření základní klasické komponenty COM  
  
1.  V sadě Visual Studio, vytvoření **prázdného řešení** projektu. Název projektu, například `WRLClassicCOM`.  
  
2.  Přidat **projektu Win32** k řešení. Název projektu, například `CalculatorComponent`. Na **nastavení aplikace** vyberte **DLL**.  
  
3.  Přidat **soubor Midl (.)** souboru do projektu. Název souboru, například `CalculatorComponent.idl`.  
  
4.  Tento kód vložte do CalculatorComponent.idl:  
  
     [!code-cpp[wrl-classic-com-component#1](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_1.idl)]  
  
5.  V CalculatorComponent.cpp, zadejte `CalculatorComponent` třídy. `CalculatorComponent` Třída dědí z [Microsoft::WRL::RuntimeClass](../windows/runtimeclass-class.md). [Microsoft::WRL::RuntimeClassFlags\<ClassicCom >](../windows/runtimeclassflags-structure.md) Určuje, že třída odvozená z [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509\(v=vs.85\).aspx) a není [IInspectable](http://msdn.microsoft.com/library/br205821\(v=vs.85\).aspx). (`IInspectable` je k dispozici pouze pro komponenty prostředí Windows Runtime aplikací.) `CoCreatableClass` vytvoří objekt pro vytváření pro třídu, která lze použít s funkcemi, jako například [CoCreateInstance](http://msdn.microsoft.com/library/windows/desktop/ms686615\(v=vs.85\).aspx).  
  
     [!code-cpp[wrl-classic-com-component#2](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_2.cpp)]  
  
6.  Nahraďte kód v dllmain.cpp pomocí následujícího kódu. Tento soubor definuje export funkcí knihovny DLL. Použijte tyto funkce [Microsoft::WRL::Module](../windows/module-class.md) třídy ke správě tříd pro modul.  
  
     [!code-cpp[wrl-classic-com-component#3](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_3.cpp)]  
  
7.  Přidat **soubor definice modulu (.def)** souboru do projektu. Název souboru, například `CalculatorComponent.def`. Tento soubor poskytuje linkeru názvy funkcí pro export.  
  
8.  Tento kód vložte do CalculatorComponent.def:  
  
    ```
    LIBRARY

    EXPORTS
        DllGetActivationFactory PRIVATE
        DllGetClassObject       PRIVATE
        DllCanUnloadNow         PRIVATE  
    ```

9. Přidáním runtimeobject.lib na řádek linkeru. Další informace, jak zjistit, [. Lib soubory jako vstup Linkeru](../build/reference/dot-lib-files-as-linker-input.md).  
  
### <a name="to-consume-the-com-component-from-a-desktop-app"></a>Chcete-li využívat komponenty modelu COM z aplikace na ploše  
  
1.  Zaregistrujte součást COM s registrem systému Windows. Uděláte to tak, vytvořte soubor položky registrace, pojmenujte ji `RegScript.reg`a přidejte následující text. Nahraďte  *\<cesta dll >* s cestou vaší knihovny DLL – například `C:\\temp\\WRLClassicCOM\\Debug\\CalculatorComponent.dll`.  
  
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
  
2.  Spustit RegScript.reg nebo ho přidat do vašeho projektu **události po sestavení**. Další informace najdete v tématu [před sestavením událostí/po sestavení příkazového řádku dialogové okno události](/visualstudio/ide/reference/pre-build-event-post-build-event-command-line-dialog-box).  
  
3.  Přidat **Konzolová aplikace Win32** projektu k řešení. Název projektu, například `Calculator`.  
  
4.  Pomocí tohoto kódu nahraďte obsah Calculator.cpp:  
  
     [!code-cpp[wrl-classic-com-component#6](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_6.cpp)]  
  
## <a name="robust-programming"></a>Robustní programování  
 Tento dokument použije standardní funkce COM k předvedení používané knihovna šablon C++ Runtime Windows vytváření komponenty modelu COM a zpřístupní ji pro všechny technologie podporou modelu COM. Můžete také použít knihovna šablon C++ prostředí Windows Runtime typy jako [Microsoft::WRL::ComPtr](../windows/comptr-class.md) ve vaší aplikace na ploše dobu trvání COM a jiné objekty. Následující kód používá ke správě životnost knihovna šablon C++ Runtime Windows `ICalculatorComponent` ukazatel. `CoInitializeWrapper` Třída je RAII obálky, který zaručuje, že knihovny COM uvolněno a také zaručuje, že doba platnosti knihovny COM outlives `ComPtr` chytré ukazatele objektu.  
  
 [!code-cpp[wrl-classic-com-component#7](../windows/codesnippet/CPP/how-to-create-a-classic-com-component-using-wrl_7.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Knihovna šablon C++ prostředí Windows Runtime (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md)