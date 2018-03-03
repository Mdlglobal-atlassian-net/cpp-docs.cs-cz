---
title: GetProcAddress | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- GetProcAddress
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], GetProcAddress
- ordinal exports [C++]
- GetProcAddress method
ms.assetid: 48d14ae0-47ea-4c5d-96b1-2c158f1a26af
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2bc32c5f6b6ae4ee80c69dff028f05d2b334d920
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="getprocaddress"></a>GetProcAddress
Procesy explicitního propojení s volání knihovny DLL [GetProcAddress](http://msdn.microsoft.com/library/windows/desktop/ms683212) získat adresu exportované funkce v knihovně DLL. Použijete ukazatel vrácený funkce k volání funkce DLL. **GetProcAddress** přijímá jako parametry popisovač modulu DLL (vrácený buď **LoadLibrary**, `AfxLoadLibrary`, nebo **GetModuleHandle**) a trvá buď název funkce je Chcete hovor nebo funkce exportu pořadí.  
  
 Protože jsou volání funkce DLL prostřednictvím ukazatele a neexistuje žádný typ kompilaci kontrola, zajistěte, aby parametrů pro funkci správnost tak, aby nemáte overstep je paměť přidělená v zásobníku a způsobit narušení přístupu. Jedním ze způsobů pomáhají zajistit bezpečnost typů je prototypy funkcí exportovaných funkcí a vytvořte odpovídající definice TypeDef pro ukazatelů na funkce. Příklad:  
  
```  
typedef UINT (CALLBACK* LPFNDLLFUNC1)(DWORD,UINT);  
...  
  
HINSTANCE hDLL;               // Handle to DLL  
LPFNDLLFUNC1 lpfnDllFunc1;    // Function pointer  
DWORD dwParam1;  
UINT  uParam2, uReturnVal;  
  
hDLL = LoadLibrary("MyDLL");  
if (hDLL != NULL)  
{  
   lpfnDllFunc1 = (LPFNDLLFUNC1)GetProcAddress(hDLL,  
                                           "DLLFunc1");  
   if (!lpfnDllFunc1)  
   {  
      // handle the error  
      FreeLibrary(hDLL);  
      return SOME_ERROR_CODE;  
   }  
   else  
   {  
      // call the function  
      uReturnVal = lpfnDllFunc1(dwParam1, uParam2);  
   }  
}  
```  
  
 Jak určit funkce, které mají být při volání metody **GetProcAddress** závisí na tom, jak byl sestaven knihovnu DLL.  
  
 Export pořadí můžete získat pouze pokud je integrovaný knihovnu DLL se připojujete pomocí souboru modulu definice (.def), a pokud jsou pořadová čísla uvedena s funkcí v **EXPORTUJE** části souboru .def knihovnu DLL. Volání metody **GetProcAddress** exportu pořadí, a název funkce je mírně rychlejší, pokud knihovnu DLL má mnoho exportovaných funkcí, protože řadové číslovky exportu slouží jako indexy do knihovny DLL export tabulky. Pomocí exportu pořadí **GetProcAddress** můžete vyhledat funkci přímo a porovnávání zadaný název funkce názvy v tabulce export knihovny DLL. Nicméně, by měly volat **GetProcAddress** s exportu pořadí pouze v případě, že budete mít kontrolu nad přiřazení pořadová čísla exportovaných funkcí v souboru .def.  
  
## <a name="what-do-you-want-to-do"></a>Co chcete udělat?  
  
-   [Postup propojení implicitně s knihovny DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)  
  
-   [Rozhodování o způsobu vytváření použít](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [LoadLibrary a AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
  
-   [FreeLibrary](http://msdn.microsoft.com/library/windows/desktop/ms683152)  
  
-   [Export z knihovny DLL pomocí souborů DEF](../build/exporting-from-a-dll-using-def-files.md)  
  
## <a name="see-also"></a>Viz také  
 [Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)