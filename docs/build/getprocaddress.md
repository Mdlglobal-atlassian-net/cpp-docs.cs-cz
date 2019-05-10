---
title: GetProcAddress
ms.date: 11/04/2016
f1_keywords:
- GetProcAddress
helpviewer_keywords:
- DLLs [C++], GetProcAddress
- ordinal exports [C++]
- GetProcAddress method
ms.assetid: 48d14ae0-47ea-4c5d-96b1-2c158f1a26af
ms.openlocfilehash: 7b480314d195f50e4867f646208f2d9c70ce9b14
ms.sourcegitcommit: da32511dd5baebe27451c0458a95f345144bd439
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65220804"
---
# <a name="getprocaddress"></a>GetProcAddress

Zpracuje explicitní propojení s voláním knihovny DLL [GetProcAddress](/windows/desktop/api/libloaderapi/nf-libloaderapi-getprocaddress) pro získání adresy exportované funkce v knihovně DLL. Použijete ukazatele vrácené funkce pro volání funkce knihovny DLL. **GetProcAddress** přijímá jako parametry popisovač DLL modulu (vrácený buď **LoadLibrary**, `AfxLoadLibrary`, nebo **GetModuleHandle**) a přebírá buď název funkce, kterou chcete na volání nebo funkce exportním ordinálním.

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

- [Propojení spustitelného souboru s knihovnou DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [Propojení spustitelného souboru s knihovnou DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [LoadLibrary a AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)

- [FreeLibrary](/windows/desktop/api/libloaderapi/nf-libloaderapi-freelibrary)

- [Export z knihovny DLL pomocí souborů DEF](exporting-from-a-dll-using-def-files.md)

## <a name="see-also"></a>Viz také:

[Vytvoření knihovny DLL jazyka C/C++ v sadě Visual Studio](dlls-in-visual-cpp.md)
