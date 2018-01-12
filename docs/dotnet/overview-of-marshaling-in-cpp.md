---
title: "Přehled zařazování v jazyku C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- marshaling
- marshalling
dev_langs: C++
helpviewer_keywords:
- Visual C++, marshaling
- C++ Support Library, marshaling
- marshaling, about marshaling
ms.assetid: 997dd4bc-5f98-408f-b890-f35de9ce3bb8
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 9d910c7d6346d23f094e9359f0e5fe3536ee09dc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="overview-of-marshaling-in-c"></a>Přehled zařazování v jazyku C++
Ve smíšeném režimu někdy musí zařazování data mezi nativní a spravovaná typy. [!INCLUDE[vs_orcas_long](../atl/reference/includes/vs_orcas_long_md.md)]zavedly knihovny zařazování pomohou zařazování a převést data v jednoduchý způsob.  
  
 Můžete použít knihovny zařazování bez ohledu [marshal_context – třída](../dotnet/marshal-context-class.md). Některé převody vyžadují kontextu. Jiné převody lze implementovat pomocí [marshal_as](../dotnet/marshal-as.md) funkce. V následující tabulce jsou uvedeny aktuální převody podporována, zda vyžaduje kontextu a jaké zařazování soubor je nutné zahrnout:  
  
|Z typu|Na typ|Zařazování – metoda|Zahrnout soubor|  
|---------------|-------------|--------------------|------------------|  
|System::String ^|const char *|marshal_context –|Marshal.h|  
|const char *|System::String ^|marshal_as|Marshal.h|  
|Char *|System::String ^|marshal_as|Marshal.h|  
|System::String ^|Const wchar_t *|marshal_context –|Marshal.h|  
|Const wchar_t *|System::String ^|marshal_as|Marshal.h|  
|wchar_t *|System::String ^|marshal_as|Marshal.h|  
|System::IntPtr|POPISOVAČ|marshal_as|marshal_windows.h|  
|POPISOVAČ|System::IntPtr|marshal_as|marshal_windows.h|  
|System::String ^|BSTR|marshal_context –|marshal_windows.h|  
|BSTR|System::String ^|marshal_as|Marshal.h|  
|System::String ^|bstr_t|marshal_as|marshal_windows.h|  
|bstr_t|System::String ^|marshal_as|marshal_windows.h|  
|System::String ^|std::String|marshal_as|marshal_cppstd.h|  
|std::String|System::String ^|marshal_as|marshal_cppstd.h|  
|System::String ^|std::wstring|marshal_as|marshal_cppstd.h|  
|std::wstring|System::String ^|marshal_as|marshal_cppstd.h|  
|System::String ^|CStringT\<char >|marshal_as|marshal_atl.h|  
|CStringT\<char >|System::String ^|marshal_as|marshal_atl.h|  
|System::String ^|CStringT < wchar_t >|marshal_as|marshal_atl.h|  
|CStringT < wchar_t >|System::String ^|marshal_as|marshal_atl.h|  
|System::String ^|CComBSTR|marshal_as|marshal_atl.h|  
|CComBSTR|System::String ^|marshal_as|marshal_atl.h|  
  
 Zařazování vyžaduje kontext, pouze pokud zařazování ze spravované v nativním režimu datové typy a nativního typu, který převádíte na nemá destruktor pro automatické čištění. Kontext zařazování zničí přidělené nativní datový typ v jeho destruktor. Převody, které vyžadují kontextu proto bude platit pouze dokud kontextu se odstraní. Pokud chcete uložit všechny zařazené hodnoty, je nutné zkopírovat hodnoty na vlastní proměnné.  
  
> [!NOTE]
>  Pokud jste vložili `NULL`s ve vašem řetězci výsledek zařazování řetězec není zaručena. Vložený `NULL`s může způsobit, že řetězec, který má být zkrácen nebo může být zachována.  
  
 Zařazování hlaviček knihoven jsou umístěné v adresáři include v podadresáři msclr –. Tento příklad ukazuje, jak zahrnout adresář msclr – deklarace záhlaví zahrnout:  
  
 `#include "msclr\marshal_cppstd.h"`  
  
 Knihovny zařazování je rozšiřitelný, takže můžete přidat vlastní zařazování typů. Další informace o rozšíření knihovny zařazování najdete v tématu [postupy: rozšíření knihovny zařazování](../dotnet/how-to-extend-the-marshaling-library.md).  
  
 V dřívějších verzích, může zařazování dat s použitím [vyvolání platformy](/dotnet/framework/interop/consuming-unmanaged-dll-functions). Další informace o `PInvoke`, najdete v části [volání nativních funkcí ze spravovaného kódu](../dotnet/calling-native-functions-from-managed-code.md).  
  
## <a name="see-also"></a>Viz také  
 [Knihovna podpory C++](../dotnet/cpp-support-library.md)   
 [Postupy: Rozšíření knihovny zařazování](../dotnet/how-to-extend-the-marshaling-library.md)