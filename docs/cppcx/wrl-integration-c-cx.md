---
title: Integrace WRL (C + +/ CX) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.topic: language-reference
ms.assetid: 3ad43894-c574-477c-ad3e-240301f381d4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: ff2fc36582e6ffbff8f7608a5a26cc472687132e
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2018
ms.locfileid: "42598087"
---
# <a name="wrl-integration-ccx"></a>Integrace WRL (C + +/ CX)

Je volně kombinovat kód knihovny WRL kódem Windows Runtime C++ šablony knihovny (WRL). Ve stejné jednotce překladu, můžete použít objekty deklarované pomocí knihovny WRL popisovač objektu (`^`) zápisem a WRL inteligentní ukazatel (`ComPtr<T>`) notaci. Však musí ručně zpracovat vrácené hodnoty a kódy chyb WRL HRESULT a výjimek knihovny WRL.
  
## <a name="wrl-development"></a>Vývoj pro knihovny WRL

Další informace o vytváření a používání komponent knihovny WRL najdete v tématu [Windows Runtime C++ šablony knihovny (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).

### <a name="example"></a>Příklad

Následující fragment kódu ukazuje použití knihovny WRL a platformy WRL spotřeby třídy Windows Runtime a zkontrolujte soubor metadat.

V příkladu je převzata z fragmentu kódu ve fóru Microsoft Store sestavování aplikací. Autor tento fragment kódu nabízí následující zřeknutí se záruk a podmínek:

1. C++ neposkytuje konkrétní rozhraní API tak, aby odrážely na typy Windows Runtime, ale soubory metadat Windows (.winmd) pro typ jsou plně kompatibilní se soubory metadat CLR. Windows poskytuje nové zjišťování metadat rozhraní API (RoGetMetaDataFile) Chcete-li získat soubor winmd pro daný typ. Nicméně tato rozhraní API jsou omezené použití pro vývojáře v jazyce C++, protože nelze vytvořit instanci třídy.

1. Po kompilaci kódu, musíte taky předat Runtimeobject.lib a Rometadata.lib Linkeru.

1. Tento fragment kódu se zobrazí jako-je. Když se očekává fungovat správně, případně může obsahovat chyby.

```cpp
#include <hstring.h>
#include <cor.h>
#include <rometadata.h>
#include <rometadataresolution.h>
#include <collection.h>

namespace ABI_Isolation_Workaround {
    #include <inspectable.h>
    #include <WeakReference.h>
}
using namespace ABI_Isolation_Workaround;
#include <wrl/client.h>

using namespace Microsoft::WRL;
using namespace Windows::Foundation::Collections;

IVector<String^>^ GetTypeMethods(Object^);

MainPage::MainPage()
{
    InitializeComponent();

    Windows::Foundation::Uri^ uri = ref new Windows::Foundation::Uri("http://buildwindows.com/");
    auto methods = GetTypeMethods(uri);

    std::wstring strMethods;
    std::for_each(begin(methods), end(methods), [&strMethods](String^ methodName) {
        strMethods += methodName->Data();
        strMethods += L"\n";
    });

    wprintf_s(L"%s\n", strMethods.c_str());
}

IVector<String^>^ GetTypeMethods(Object^ instance)
{
    HRESULT hr;
    HSTRING hStringClassName;
    hr = instance->__cli_GetRuntimeClassName(reinterpret_cast<__cli_HSTRING__**>(&hStringClassName)); // internal method name subject to change post BUILD
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD
    String^ className = reinterpret_cast<String^>(hStringClassName);

    ComPtr<IMetaDataDispenserEx> metadataDispenser; ComPtr<IMetaDataImport2> metadataImport; hr = MetaDataGetDispenser(CLSID_CorMetaDataDispenser, IID_IMetaDataDispenser, (LPVOID*)metadataDispenser.GetAddressOf());
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD

    HSTRING hStringFileName;
    mdTypeDef typeDefToken;
    hr = RoGetMetaDataFile(hStringClassName, metadataDispenser.Get(), &hStringFileName, &metadataImport, &typeDefToken);
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD
    String^ fileName = reinterpret_cast<String^>(hStringFileName);

    HCORENUM hCorEnum = 0;
    mdMethodDef methodDefs[2048];
    ULONG countMethodDefs = sizeof(methodDefs);
    hr = metadataImport->EnumMethods(&hCorEnum, typeDefToken, methodDefs, countMethodDefs,  &countMethodDefs);
    if (FAILED(hr))
        __cli_WinRTThrowError(hr); // internal method name subject to change post BUILD

    wchar_t methodName[1024];
    ULONG countMethodName;
    std::wstring strMethods;
    Vector<String^>^ retVal = ref new Vector<String^>();

    for (int i = 0; i < countMethodDefs; ++i)
    {
        countMethodName = sizeof(methodName);
        hr = metadataImport->GetMethodProps(methodDefs[i], nullptr, methodName, countMethodName, &countMethodName, nullptr, nullptr, nullptr, nullptr, nullptr);
        if (SUCCEEDED(hr))
        {
            methodName[ countMethodName ] = 0;
            retVal->Append(ref new String(methodName));
        }
    }
    return retVal;
}

```

## <a name="see-also"></a>Viz také:

[Spolupráce s jinými jazyky](interoperating-with-other-languages-c-cx.md)  
