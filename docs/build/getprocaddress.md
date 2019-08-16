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
ms.openlocfilehash: 2d322cfe7d3bd60d8d702a226e181eb7b4ede963
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493255"
---
# <a name="getprocaddress"></a>GetProcAddress

Procesy, které se explicitně propojí s voláním knihovny DLL [GetProcAddress](/windows/win32/api/libloaderapi/nf-libloaderapi-getprocaddress) pro získání adresy exportované funkce v knihovně DLL. Použijete ukazatel na vrácenou funkci pro volání funkce knihovny DLL. **GetProcAddress** přijímá jako parametry popisovač modulu knihovny DLL (vrácený funkcí **LoadLibrary**, nebo `AfxLoadLibrary` **GetModuleHandle**) a přebírá buď název funkce, kterou chcete volat, nebo exportní pořadové číslo funkce.

Vzhledem k tomu, že volání funkce knihovny DLL prostřednictvím ukazatele a nedochází k žádné kontrole typu při kompilaci, ujistěte se, že parametry funkce jsou správné, takže nebudete muset přesměrovat paměť přidělené do zásobníku a způsobit narušení přístupu. Jedním ze způsobů, jak zajistit bezpečnost typů, je podívat se na prototypy funkce exportovaných funkcí a vytvořit vyhovující definice TypeDef pro ukazatele na funkce. Příklad:

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

Způsob, jakým určíte požadovanou funkci při volání funkce **GetProcAddress** , závisí na tom, jak byla knihovna dll sestavena.

Exportní ordinální číslo lze získat pouze v případě, že knihovna DLL, na kterou propojujete, je sestavena pomocí souboru definice modulu (. def) a pokud jsou pořadí uvedena s funkcemi v oddílu EXPORTS souboru. def knihovny DLL. Volání **GetProcAddress** s exportním pořadovým číslem na rozdíl od názvu funkce je mírně rychlejší, pokud má knihovna DLL mnoho exportovaných funkcí, protože export řadových číslovek slouží jako indexy do exportní tabulky knihovny DLL. Pomocí pořadového čísla exportu může funkce **GetProcAddress** najít funkci přímo na rozdíl od porovnání zadaného názvu s názvy funkcí v exportní tabulce knihovny DLL. Nicméně byste měli volat **GetProcAddress** s exportním pořadovým číslem pouze v případě, že máte kontrolu nad přiřazením řadových funkcí do exportovaných funkcí v souboru. def.

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Propojení spustitelného souboru s knihovnou DLL](linking-an-executable-to-a-dll.md#linking-implicitly)

- [Propojení spustitelného souboru s knihovnou DLL](linking-an-executable-to-a-dll.md#determining-which-linking-method-to-use)

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace?

- [LoadLibrary a AfxLoadLibrary](loadlibrary-and-afxloadlibrary.md)

- [FreeLibrary](/windows/win32/api/libloaderapi/nf-libloaderapi-freelibrary)

- [Export z knihovny DLL pomocí souborů DEF](exporting-from-a-dll-using-def-files.md)

## <a name="see-also"></a>Viz také:

[Vytváření C/C++ knihoven DLL v aplikaci Visual Studio](dlls-in-visual-cpp.md)
