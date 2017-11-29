---
title: Integrace knihovny WRL (C + +/ CX) | Microsoft Docs
ms.custom: 
ms.date: 01/22/2017
ms.technology: cpp-windows
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3ad43894-c574-477c-ad3e-240301f381d4
caps.latest.revision: "9"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: 289c82a69ebc549d53e7b8ae49b6939200eb3aac
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="wrl-integration-ccx"></a>Integrace knihovny WRL (C + +/ CX)
Můžete volně používat knihovny WRL kódu pomocí [!INCLUDE[cppwrl](includes/cppwrl-md.md)] ([!INCLUDE[cppwrl_short](includes/cppwrl-short-md.md)]) kódu. Ve stejné jednotce překlad, můžete použít objekty deklarovat s WRL popisovač objektu (`^`) zápis a [!INCLUDE[cppwrl_short](includes/cppwrl-short-md.md)] chytré ukazatele (`ComPtr<T>`) zápis. Však musí ručně zpracování vrácených hodnot, a [!INCLUDE[cppwrl_short](includes/cppwrl-short-md.md)] HRESULT kódy chyb a knihovny WRL výjimky.  
  
## <a name="includecppwrlshortincludescppwrl-short-mdmd-development"></a>[!INCLUDE[cppwrl_short](includes/cppwrl-short-md.md)]vývoj  
 Další informace o vytváření obsahu a využívání [!INCLUDE[cppwrl_short](includes/cppwrl-short-md.md)] součásti, najdete v části [Windows Runtime C++ šablony knihovny (WRL)](../windows/windows-runtime-cpp-template-library-wrl.md).  
  
### <a name="example"></a>Příklad  
 Následující fragment kódu ukazuje, jak pomocí knihovny WRL a [!INCLUDE[cppwrl_short](includes/cppwrl-short-md.md)] využívat [!INCLUDE[wrt](includes/wrt-md.md)] třídy a zkontrolujte soubor metadat.  
>>>>>>> master
  
 Příklad převzaty z fragmentu kódu v [fórum aplikace Windows Store vytváření](http://social.msdn.microsoft.com/Forums/winappswithnativecode/thread/211ef583-db11-4e55-926b-6d9ab53dbdb4). Autor tento fragment kódu nabízí následující omezení a určení zavedených:  
  
1.  C++ neposkytuje konkrétní rozhraní API, aby odpovídala v [!INCLUDE[wrt](includes/wrt-md.md)] typy, ale soubory metadat Windows (.winmd) pro typ jsou plně kompatibilní se soubory metadat CLR. Systém Windows nabízí nové zjišťování metadat rozhraní API (RoGetMetaDataFile) Chcete-li získat k souboru .winmd pro daného typu. Však tato rozhraní API jsou omezené použití pro vývojáře C++, protože nelze vytvořit instanci třídy.  
  
2.  Po kód je kompilovat, budete také muset Runtimeobject.lib a Rometadata.lib předat Linkeru.  
  
3.  Zobrazí se tento fragment kódu jako-je. Když se očekává, fungovat správně, případně může obsahovat chyby.  
  
```  
  
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
  
    for(int i = 0; i < countMethodDefs; ++i)  
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
  
## <a name="see-also"></a>Viz také  
 [Spolupráce s jinými jazyky](interoperating-with-other-languages-c-cx.md)