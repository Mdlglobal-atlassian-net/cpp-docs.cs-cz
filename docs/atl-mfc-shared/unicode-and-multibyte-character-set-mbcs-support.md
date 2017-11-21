---
title: "Kódování Unicode a vícebajtových znaků (MBCS) podporu sady | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- MFC [C++], character set support
- MBCS [C++], strings and MFC support
- strings [C++], MBCS support in MFC
- character sets [C++], multibyte
- Unicode [C++], MFC strings
- Unicode [C++], string objects
- strings [C++], Unicode
- strings [C++], character set support
ms.assetid: 44b3193b-c92d-40c5-9fa8-5774da303cce
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 08f15fd57cb1354399e4e85b886141d02cb49daa
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="unicode-and-multibyte-character-set-mbcs-support"></a>(MBCS) podporu kódování Unicode a vícebajtové znakové sady
Některé jazyky, například japonštiny a čínština, mají velký znakových sad. Pro podporu programování pro tyto trhy, Microsoft Foundation Class Library (MFC) je povolen pro dva různé přístupy pro zpracování velkých znakových sad:  
  
-   [Kódování Unicode](#_core_mfc_support_for_unicode_strings)  
  
-   [Vícebajtové znakové sady (MBCS)](#_core_mfc_support_for_mbcs_strings)  
  
 Pro všechny nové vývoj byste měli používat kódování Unicode.  
  
##  <a name="_core_mfc_support_for_unicode_strings"></a>Podpora MFC pro řetězců v kódu Unicode  
 Knihovna celou třídu je podmíněně povolena pro znaků Unicode a řetězce. Na konkrétní třídy [CString](../atl-mfc-shared/reference/cstringt-class.md) kódování Unicode.  
  
|||||  
|-|-|-|-|  
|UAFXCW. LIB|UAFXCW. PDB|UAFXCWD. LIB|UAFXCWD. PDB|  
|MFC*xx*U.LIB|MFC*xx*U.PDB|MFC*xx*U.DLL|MFC*xx*UD. LIB|  
|MFC*xx*UD. PDB|MFC*xx*UD. KNIHOVNY DLL|MFCS*xx*U.LIB|MFCS*xx*U.PDB|  
|MFCS*xx*UD. LIB|MFCS*xx*UD. PDB|MFCM*xx*U.LIB|MFCM*xx*U.PDB|  
|MFCM*xx*U.DLL|MFCM*xx*UD. LIB|MFCM*xx*UD. PDB|MFCM*xx*UD. KNIHOVNY DLL|  
  
 (*xx* představuje číslo verze souboru; '80, například znamená verzi 8.0.)  
  
 `CString`je založena na `TCHAR` datového typu. Pokud je symbol `_UNICODE` je definována pro sestavení vašeho programu `TCHAR` je definována jako typ `wchar_t`, typ kódování znaků 16 bitů. V opačném `TCHAR` je definován jako `char`, kódování normální 8bitové znaků. Proto v kódu Unicode `CString` se skládá z 16 rozšířené znaky. Bez kódování Unicode, se skládá z znaků typu `char`.  
  
 Do dokončení programování Unicode vaší aplikace, které je nutné také:  
  
-   Použití `_T` makro na podmíněně kód literálu řetězce přenosný na kódování Unicode.  
  
-   Pokud předáte řetězce, věnujte pozornost jestli argumenty funkce vyžadují délka ve znacích nebo délka v bajtech. Rozdíl je důležité, pokud používáte řetězců v kódu Unicode.  
  
-   Pomocí přenosného verzí funkcí jazyka C Runtime zpracování řetězce.  
  
-   Použijte následující typy dat pro znaky a znak ukazatele:  
  
    -   `TCHAR`Použít `char`.  
  
    -   `LPTSTR`Použít `char*`.  
  
    -   `LPCTSTR`Použít `const char*`. `CString`poskytuje operátor `LPCTSTR` pro převod mezi `CString` a `LPCTSTR`.  
  
 `CString`také poskytuje kódování Unicode konstruktory, přiřazení operátory a operátory porovnání.  
  
 Informace související s programováním znakové sady Unicode, najdete v části [témata Unicode](../mfc/unicode-in-mfc.md). [Referenční dokumentace běhové knihovny](../c-runtime-library/c-run-time-library-reference.md) definuje přenosné verzích všechny její funkce zpracování řetězců. Najdete v části kategorie [internacionalizace](../c-runtime-library/internationalization.md).  
  
##  <a name="_core_mfc_support_for_mbcs_strings"></a>Podpora MFC pro řetězce znakové sady MBCS  
  
 Knihovna tříd je povolená i u vícebajtových znakových sad, ale jenom pro dvoubajtové znakové nastaví (DBCS).  
  
 Znak v sadě vícebajtových znaků může být jedno nebo dvě bajtů široké. Pokud se dva bajty široké, jeho prvního bajtu je speciální "úvodní bajt" tedy vybrat z konkrétního rozsahu, v závislosti na tom, které kódu stránky se používá. Dohromady, realizace a "poslední bajt" Zadejte jedinečné znaky kódování.  
  
 Pokud je symbol `_MBCS` je definována pro sestavení vašeho programu typ `TCHAR`, na kterém `CString` je založen, se mapuje na `char`. Je určit, které bajtů `CString` jsou úvodní bajty a které jsou druhé bajty. Běhové knihovny jazyka C poskytuje funkce, můžete to zjistit.  
  
 V části DBCS daný řetězec může obsahovat všechny jednobajtové znaky ANSI, všechny dvoubajtové znaky nebo jejich kombinaci dva. Tyto možnosti vyžadují zvláštní pozornost při analýze řetězce. To zahrnuje `CString` objekty.  
  
> [!NOTE]
>  Serializace řetězec kódování Unicode v prostředí MFC může číst řetězce Unicode a MBCS bez ohledu na to, kterou verzi aplikace, kterou používáte. Datové soubory jsou přenosné mezi verzemi kódování Unicode a MBCS vašeho programu.  
  
 `CString`Členské funkce použít speciální "obecný text" verze C běhové funkce, které volají nebo používají funkce kódování Unicode. Tedy například pokud `CString` by obvykle volání funkce `strcmp`, volá funkci odpovídající obecného textu `_tcscmp` místo. V závislosti na tom, jak symboly `_MBCS` a `_UNICODE` jsou definovány `_tcscmp` mapuje následujícím způsobem:  
  
|||  
|-|-|  
|`_MBCS`definované|`_mbscmp`|  
|`_UNICODE`definované|`wcscmp`|  
|Ani symbol definované|`strcmp`|  
  
> [!NOTE]
>  Symboly `_MBCS` a `_UNICODE` se vzájemně vylučují.  
  
 Mapování obecného textu funkcí pro všechny běhové rutiny zpracování řetězců, které jsou popsané v [referenční dokumentace knihoven C Run-Time](../c-runtime-library/c-run-time-library-reference.md). Konkrétně, najdete v části [internacionalizace](../c-runtime-library/internationalization.md).  
  
 Podobně `CString` metody jsou implementovaná pomocí mapování "Obecné" datového typu. Umožňuje MBCS a Unicode MFC používá `TCHAR` pro `char`, `LPTSTR` pro `char*`, a `LPCTSTR` pro `const char*`. Tyto zajistit správné mapování pro MBCS nebo Unicode.  
  
## <a name="see-also"></a>Viz také  
 [Řetězce (ATL a MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
 [Zacházení s řetězci](../c-runtime-library/string-manipulation-crt.md)

