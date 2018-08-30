---
title: GetProcAddress | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- GetProcAddress
dev_langs:
- C++
helpviewer_keywords:
- DLLs [C++], GetProcAddress
- ordinal exports [C++]
- GetProcAddress method
ms.assetid: 48d14ae0-47ea-4c5d-96b1-2c158f1a26af
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 91fd6b983d648b682cbd60fa6126189e102b9f1c
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194356"
---
# <a name="getprocaddress"></a>GetProcAddress
Zpracuje explicitní propojení s voláním knihovny DLL [GetProcAddress](https://msdn.microsoft.com/library/windows/desktop/ms683212) pro získání adresy exportované funkce v knihovně DLL. Použijete ukazatele vrácené funkce pro volání funkce knihovny DLL. **GetProcAddress** přijímá jako parametry popisovač DLL modulu (vrácený buď **LoadLibrary**, `AfxLoadLibrary`, nebo **GetModuleHandle**) a přebírá buď název funkce, kterou chcete na volání nebo funkce exportním ordinálním.  
  
 Protože jsou volání funkce DLL prostřednictvím ukazatele a neexistuje žádná kontrola typu v čase kompilace, ujistěte se, že jsou parametry funkce správné tak, že nemáte k překročení paměti přidělené v zásobníku a způsobí narušení přístupu. Jedním ze způsobů, které vám pomůžou zajistit bezpečnost typů je podívat se na funkční prototypy exportovaných funkcí a vytvořit odpovídající výrazy TypeDef pro ukazatele na funkce. Příklad:  
  
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
  
 Jak určit funkci, kterou chcete při volání metody **GetProcAddress** závisí na tom, jak byla sestavena knihovna DLL.  
  
 Můžete si opatřit pouze ordinální export Pokud odkazujete na knihovnu DLL sestaveno pomocí souboru modulu definice (.def) a pokud jsou ordinály uvedeny s funkcemi v **EXPORTY** části souboru .def knihovny DLL. Volání **GetProcAddress** s export je mírně rychlejší, pokud má knihovna DLL mnoho exportovaných funkcí, protože řadové číslovky exportu slouží jako indexy knihovnou DLL exportovat tabulku řadová, nikoli s názvem funkce. S ordinálním exportem **GetProcAddress** lze nalézt funkci přímo na rozdíl od porovnání zadaného názvu s názvy funkcí v exportní tabulce knihovny DLL. Nicméně byste měli volat **GetProcAddress** s ordinálním exportem pouze v případě, že budete mít kontrolu nad přiřazením řadové číslovky do exportovaných funkcí v .def souboru.  
  
## <a name="what-do-you-want-to-do"></a>Co chcete udělat?  
  
-   [Jak implicitní propojení s knihovnou DLL](../build/linking-an-executable-to-a-dll.md#linking-implicitly)  
  
-   [Určit, kterou propojovací metodu použít](../build/linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?  
  
-   [LoadLibrary a AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
  
-   [FreeLibrary](https://msdn.microsoft.com/library/windows/desktop/ms683152)  
  
-   [Export z knihovny DLL pomocí souborů DEF](../build/exporting-from-a-dll-using-def-files.md)  
  
## <a name="see-also"></a>Viz také  
 [Knihovny DLL v jazyce Visual C++](../build/dlls-in-visual-cpp.md)