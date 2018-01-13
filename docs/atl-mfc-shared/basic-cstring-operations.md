---
title: "Základní CString Operations | Microsoft Docs"
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
- string literals, CString operations
- literal strings, CString operations
- CString objects
- string comparison, CString operations
- characters, accessing in CStrings
ms.assetid: 41db66b2-9427-4bb3-845a-9b6869159a6c
caps.latest.revision: "17"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 42353a9c59bead96da8eb3b114c8acb2361b53d0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="basic-cstring-operations"></a>CString základní operace
Toto téma vysvětluje následující basic [CString](../atl-mfc-shared/reference/cstringt-class.md) operace:  
  
- [Vytváření CString – objekty z standardní literály jazyka C](#_core_creating_cstring_objects_from_standard_c_literal_strings)  
  
- [Přístup k jednotlivých znaků v CString](#_core_accessing_individual_characters_in_a_cstring)  
  
- [Zřetězení dvě CString – objekty](#_core_concatenating_two_cstring_objects)  
  
- [Porovnání CString – objekty](#_core_comparing_cstring_objects)  
  
- [Převádění CString – objekty](#_core_converting_cstring_objects)  
  
 `Class CString`je založený na šabloně třída [CStringT třída](../atl-mfc-shared/reference/cstringt-class.md). `CString`je `typedef` z `CStringT`. Více přesně `CString` je `typedef` z *explicitní specializace* z `CStringT`, což je běžný způsob, jak pomocí třídy šablony definice třídy. Podobně definovaných tříd jsou `CStringA` a `CStringW`.  
  
 `CString`, `CStringA`, a `CStringW` jsou definovány v atlstr.h. `CStringT`je definována v cstringt.h.  
  
 `CString`, `CStringA`, a `CStringW` každý získat sadu metod a operátory definované `CStringT` pro řetězec dat, které podporují. Některé metody duplicitní a v některých případech se překročí maximální služby řetězec běhové knihovny jazyka C.  
  
 Poznámka: `CString` je nativních tříd. Pro třídu řetězec, který je určen pro použití v jazyce C + +/ CLI spravovaný projekt, použijte `System.String`.  
  
##  <a name="_core_creating_cstring_objects_from_standard_c_literal_strings"></a>Vytváření CString – objekty z standardní C řetězcové literály  
 Můžete přiřadit stylu jazyka C literály `CString` právě můžete přiřadit jednu `CString` objekt do jiné.  
  
-   Přiřadit hodnotu literálu řetězec C tak, aby `CString` objektu.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#183](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_1.cpp)]  
  
-   Přiřazení hodnoty jednoho `CString` do jiného `CString` objektu.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#184](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_2.cpp)]  
  
     Obsah `CString` objektu se zkopírují, pokud jeden `CString` objekt je přiřazen k jiné. Proto dva řetězce nesdílejí odkaz na skutečnými znaky, které tvoří řetězec. Další informace o tom, jak používat `CString` objekty jako hodnoty, najdete v části [CString sémantiku](../atl-mfc-shared/cstring-semantics.md).  
  
    > [!NOTE]
    >  Pro zápis aplikace tak, aby jej bylo možno zkompilovat pro kódování Unicode nebo ANSI, kódu s použitím _T – makro řetězcové literály. Další informace najdete v tématu [Podpora vícebajtových znakovou sadu (MBCS) kódování Unicode a](../atl-mfc-shared/unicode-and-multibyte-character-set-mbcs-support.md).  
  
##  <a name="_core_accessing_individual_characters_in_a_cstring"></a>Přístup k jednotlivých znaků v CString  
 Dostanete jednotlivých znaků `CString` objekt pomocí `GetAt` a `SetAt` metody. Pole element nebo dolní index, operátor ([]) můžete použít také místo `GetAt` získat jednotlivých znaků. (To se podobá přístupem elementy pole index, stejně jako standardní řetězce stylu jazyka C.) Index hodnoty pro `CString` znaky jsou od nuly.  
  
##  <a name="_core_concatenating_two_cstring_objects"></a>Zřetězení dvě CString – objekty  
 Ke zřetězení dva `CString` objekty, používají operátory řetězení (+ nebo +=), a to takto.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#185](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_3.cpp)]  
  
 Alespoň jeden argument operátory řetězení (+ nebo +=) musí být `CString` objektu, ale můžete použít řetězec konstantní znaků (například `"big"`) nebo `char` (například "x") v argumentu.  
  
##  <a name="_core_comparing_cstring_objects"></a>Porovnání CString – objekty  
 `Compare` Metoda a == – operátor pro `CString` odpovídají. `Compare`, `operator==`, a `CompareNoCase` víte MBCS a Unicode; `CompareNoCase` je také velká a malá písmena. `Collate` Metodu `CString` národní prostředí – velká a malá písmena a je často nižší než `Compare`. Použití `Collate` pouze kde musíte dodržet toto řazení pravidla uvedeného podle aktuální národní prostředí.  
  
 V následující tabulce jsou uvedeny dostupných [CString](../atl-mfc-shared/reference/cstringt-class.md) porovnání funkcí a jejich ekvivalentní Unicode nebo MBCS-přenositelností funkcí v běhové knihovny jazyka C.  
  
|CString – funkce|MBCS – funkce|Unicode – funkce|  
|----------------------|-------------------|----------------------|  
|`Compare`|`_mbscmp`|`wcscmp`|  
|`CompareNoCase`|`_mbsicmp`|`_wcsicmp`|  
|`Collate`|`_mbscoll`|`wcscoll`|  
  
 `CStringT` Šablona třídy definuje relační operátory (<, \<=, > =, >, ==, a! =), které jsou k dispozici pro použití `CString`. Můžete porovnat dva `CStrings` pomocí těchto operátorů, jak je znázorněno v následujícím příkladu.  
  
 [!code-cpp[NVC_ATLMFC_Utilities#186](../atl-mfc-shared/codesnippet/cpp/basic-cstring-operations_4.cpp)]  
  
##  <a name="_core_converting_cstring_objects"></a>Převádění CString – objekty  
 Informace o převodu CString – objekty na jiný typ řetězce, najdete v tématu [postupy: převod mezi různými typy řetězců](../text/how-to-convert-between-various-string-types.md).  
  
## <a name="using-cstring-with-wcout"></a>CString pomocí wcout  
 Použít CString s `wcout` musí explicitně převést objekt, který má `const wchar_t*` jak je znázorněno v následujícím příkladu:  
  
```  
CString cs("meow");

    wcout <<(const wchar_t*) cs <<endl;  
 
```  
  
 Bez přetypování `cs` je považován za `void*` a `wcout` vytiskne adresu objektu. Toto chování je způsobená jemně interakce mezi šablony argument odvození přetížení rozlišení a které jsou v samotných správné a vyhovující s C++ standard.  
  
## <a name="see-also"></a>Viz také  
 [Řetězce (ATL a MFC)](../atl-mfc-shared/strings-atl-mfc.md)   
 [CStringT – třída](../atl-mfc-shared/reference/cstringt-class.md)   
 [Specializace šablony](../cpp/template-specialization-cpp.md)   
 [Postupy: Převody mezi různými typy řetězců](../text/how-to-convert-between-various-string-types.md)

