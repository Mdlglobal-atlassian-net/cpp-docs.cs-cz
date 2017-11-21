---
title: "CString operace vztahující se k stylu jazyka C řetězce | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
dev_langs: C++
helpviewer_keywords:
- CString objects, basic operations
- MFC [C++], string handling class
- string conversion [C++], C-style strings
- strings [C++], string operations
- standard run-time library string functions
- null values, Null-terminated string conversion
- string functions
- strings [C++], in C
- string arguments
- C-style strings
- strings [C++], class CString
- casting CString objects
ms.assetid: 5048de8a-5298-4891-b8a0-c554b5a3ac1b
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 499f7d7b1a286f85a13f2b2a8e87a3ee09f44086
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="cstring-operations-relating-to-c-style-strings"></a>CString operace vztahující se k řetězce stylu jazyka C
A [CString](../atl-mfc-shared/using-cstring.md) objektu obsahuje znak řetězec data. `CString`dědí sadu [metody a operátory](../atl-mfc-shared/reference/cstringt-class.md) , jsou definovány v šabloně třídy [CStringT](../atl-mfc-shared/reference/cstringt-class.md) pracovat s řetězcovými daty. (`CString` je `typedef` který se specializuje `CStringT` pro práci s druh textová data, `CString` podporuje.)  
  
 `CString`neukládá data znak interně jako řetězec stylu jazyka C ukončené hodnotou null. Místo toho `CString` sleduje délka textová data tak, aby mohli sledovat bezpečněji data a místo vyžaduje.  
  
 `CString`Přijměte řetězce stylu jazyka C a poskytuje způsoby, jak přistupovat k datům znak jako řetězec stylu jazyka C. Toto téma obsahuje následující části, které vysvětlují, jak používat `CString` objektů, jako by šlo stylu jazyka C řetězce ukončené hodnotou null.  
  
- [Převádění na řetězce ukončené hodnotou null stylu jazyka C](#_core_using_cstring_as_a_c.2d.style_null.2d.terminated_string)  
  
- [Práce s funkcemi řetězec standardní běhové knihovny](#_core_working_with_standard_run.2d.time_library_string_functions)  
  
- [Přímém upravování CString obsah](#_core_modifying_cstring_contents_directly)  
  
- [CString – objekty pomocí funkce argumentů proměnných](#_core_using_cstring_objects_with_variable_argument_functions)  
  
- [Zadání CString formální parametrů](#_core_specifying_cstring_formal_parameters)  
  
##  <a name="_core_using_cstring_as_a_c.2d.style_null.2d.terminated_string"></a>Použití CString jako řetězce ukončené hodnotou Null stylu jazyka C  
 Použít `CString` objektu jako řetězec stylu jazyka C, převést objekt, který má `LPCTSTR`. V následujícím příkladu `CString` vrací ukazatel na jen pro čtení stylu jazyka C ukončené hodnotou null řetězec. `strcpy` Funkce převádí kopii řetězce stylu jazyka C v proměnné `myString`.  
  
```  
CString aCString = "A string";  
char myString[256];  
strcpy(myString, (LPCTSTR)aCString);
```  
  
 Můžete použít `CString` metody, například `SetAt`a změňte jednotlivých znaků v objekt řetězce. Ale `LPCTSTR` ukazatel je dočasný a stává neplatným při jakékoli změně k `CString`. `CString` Můžete také přejít mimo obor a automaticky se odstraní. Doporučujeme, abyste měli čerstvou `LPCTSTR` ukazatel `CString` objektu pokaždé, když použijete jednu.  
  
 Někdy může vyžadovat kopii `CString` dat můžete změnit přímo. Použijte funkci bezpečnější `strcpy_s` (nebo Unicode nebo MBCS-přenositelností `_tcscpy_s`) pro kopírování `CString` objektu do samostatné vyrovnávací paměti. Toto je, kde je možné bezpečně upravit znaků, jak ukazuje následující příklad.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#189](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_1.cpp)]  
  
> [!NOTE]
>  Třetí argument `strcpy_s` (nebo Unicode nebo MBCS-přenositelností `_tcscpy_s`) je buď `const wchar_t*` (Unicode) nebo `const char*` (ANSI). V příkladu výše předává `CString` pro tento argument. C++ compiler automaticky použije definované pro funkci pro převod `CString` třídu, která se převede `CString` k `LPCTSTR`. Schopnost definovat operations přetypování z jednoho typu do jiného je jedním z nejužitečnějších funkcí jazyka C++.  
  
##  <a name="_core_working_with_standard_run.2d.time_library_string_functions"></a>Práce s funkcemi řetězec standardní běhové knihovny  
 Nyní byste měli mít k vyhledání `CString` metoda provádět všechny operace řetězců, pro které můžete zvážit použití standardní funkcí řetězec běhové knihovny jazyka C, jako `strcmp` (nebo Unicode nebo MBCS-přenositelností `_tcscmp`).  
  
 Pokud musíte použít funkcí jazyka C Runtime řetězec, můžete použít techniky popsané v _core_using_cstring_as_a_c.2d.style_null.2d.terminated_string. Můžete zkopírovat `CString` objektu do vyrovnávací paměti ekvivalentní řetězec stylu jazyka C, provádět vaše operace s vyrovnávací paměti a potom přiřadit výsledný řetězec stylu jazyka C zpět na `CString` objektu.  
  
##  <a name="_core_modifying_cstring_contents_directly"></a>Přímém upravování CString obsah  
 Ve většině případů byste měli používat `CString` členské funkce změnit obsah `CString` objektu nebo převést `CString` na řetězec znaků stylu jazyka C.  
  
 Některých situacích, kde má smysl přímo upravit `CString` obsah, například při práci s funkcí operačního systému, které vyžadují znak vyrovnávací paměti.  
  
 `GetBuffer` a `ReleaseBuffer` metody nabízí přístup k interní znak vyrovnávací paměti `CString` objektu a umožňují upravovat přímo. Následující kroky ukazují, jak používat tyto funkce pro tento účel.  
  
#### <a name="to-use-getbuffer-and-releasebuffer-to-access-the-internal-character-buffer-of-a-cstring-object"></a>Používat pro přístup k interní znak vyrovnávací paměti objektu CString getbuffer – a ReleaseBuffer  
  
1.  Volání `GetBuffer` pro `CString` objektu a zadejte délka vyrovnávací paměti, budete potřebovat.  
  
2.  Použít ukazatele vrácený `GetBuffer` zápis znaků do přímo `CString` objektu.  
  
3.  Volání `ReleaseBuffer` pro `CString` objekt, který chcete aktualizovat všechny interní `CString` stavu informace, například délka řetězce. Po úpravě obsah `CString` objektu přímo, musí volat `ReleaseBuffer` před voláním jakékoli jiné `CString` členské funkce.  
  
##  <a name="_core_using_cstring_objects_with_variable_argument_functions"></a>CString – objekty pomocí funkce argumentů proměnných  
 Některé funkce C trvat proměnný počet argumentů. Významné příkladem je `printf_s`. Kvůli způsobu, kterým je tento druh funkce deklarovaný kompilátor nemůže být zda typu argumentů a nemůže určit, které operaci převodu provést na každý argument. Proto je důležité, že používáte typ explicitní přetypování při předávání `CString` objekt, který má funkci, která přebírá proměnný počet argumentů.  
  
 Použít `CString` objekt ve funkci argumentů s proměnnou, explicitně přetypovat `CString` k `LPCTSTR` řetězce, jak je znázorněno v následujícím příkladu.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#190](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_2.cpp)]  
  
##  <a name="_core_specifying_cstring_formal_parameters"></a>Zadání parametrů CString Formal  
 Pro většinu funkce, které je třeba argument řetězce, je nejlepší určit typ formálního parametru v prototypu funkce jako `const` ukazatel na znak (`LPCTSTR`) místo `CString`. Pokud je zadán parametr formální jako `const` ukazatel na znak, můžete předat ukazatel na `TCHAR` pole řetězcový literál [`"hi there"`], nebo `CString` objektu. `CString` Objektu budou automaticky převedeny na `LPCTSTR`. Jakékoli místo, můžete použít `LPCTSTR`, můžete použít také `CString` objektu.  
  
 Můžete také určit formální parametr jako odkaz na konstantní řetězec (to znamená, `const CString&`) Pokud je argument se nezmění. Vyřaďte `const` modifikátor, pokud se změní řetězec pomocí funkce. Pokud se požaduje výchozí hodnotu null, inicializuje ji řetězec null [`""`], jak je uvedeno níže:  
  
 [!code-cpp[NVC_ATLMFC_Utilities#191](../atl-mfc-shared/codesnippet/cpp/cstring-operations-relating-to-c-style-strings_3.cpp)]  
  
 Pro většinu výsledky funkce, můžete jednoduše vrátit `CString` objektu podle hodnoty.  
  
## <a name="see-also"></a>Viz také  
 [Řetězce (ATL a MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
 [Předávání argumentů CString](../atl-mfc-shared/cstring-argument-passing.md)

