---
title: Souhrn programování Unicode | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- Unicode [C++], programming with
- Unicode [C++], MFC and C run-time functions
ms.assetid: a4c9770f-6c9c-447c-996b-980920288bed
author: ghogen
ms.author: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2a378d46c517dfc0fbb5857ad54bc31f4c34287b
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33859674"
---
# <a name="unicode-programming-summary"></a>Souhrn programování s kódem Unicode
Abyste mohli využívat MFC a C Runtime podpora pro Unicode, budete muset:  
  
-   Definování **_UNICODE**.  
  
     Definujte symbol **_UNICODE** před sestavením programu.  
  
-   Zadejte vstupní bod.  
  
     Na **výstup** stránka složky Linkeru do projektu [stránky vlastností](../ide/property-pages-visual-cpp.md) dialogové okno pole, nastavte symbol vstupního bodu na **wWinMainCRTStartup**.  
  
-   Pomocí přenosného běhové funkce a typy.  
  
     Použijte správnou běhové funkce jazyka C pro zpracování řetězce Unicode. Můžete použít **serveru webového obsahu** řadu funkcí, ale preferovat (mezinárodní úrovni povoleno) přenositelností plně **_TCHAR** makra. Tyto makra jsou všechny s předponou **_tcs**; se nahrazují pro jednu, pro **str** řadu funkcí. Tyto funkce jsou podrobně popsány v [internacionalizace](../c-runtime-library/internationalization.md) části *referenční dokumentace běhové knihovny*. Další informace najdete v tématu [mapování obecného textu v souboru Tchar.h](../text/generic-text-mappings-in-tchar-h.md).  
  
     Použití **_TCHAR** a související přenosné datové typy popsané v [podpora pro Unicode](../text/support-for-unicode.md).  
  
-   Zpracování řetězců literálu.  
  
     Kompilátor Visual C++ interpretuje řetězcový literál programového jako:  
  
    ```  
    L"this is a literal string"  
    ```  
  
     rozumí řetězec znaků Unicode. Literálové znaky můžete používat stejnou předponu. Použití **_T** makro do kódu obecných řetězců obecně, takže jsou kompilovány jako řetězce Unicode v kódu Unicode nebo řetězce ANSI (včetně MBCS) bez kódování Unicode. Například místo provedení:  
  
    ```  
    pWnd->SetWindowText( "Hello" );  
    ```  
  
     Použití:  
  
    ```  
    pWnd->SetWindowText( _T("Hello") );  
    ```  
  
     S **_UNICODE** definované, **_T –** překládá řetězcového literálu do formuláře předpony L; jinak hodnota **_T** převede řetězec bez předpony l.  
  
    > [!TIP]
    >  **_T** makro je stejný jako `_TEXT` makro.  
  
-   Buďte opatrní délky řetězců funkce.  
  
     Některé funkce mají počet znaků v řetězci; ostatní chtějí počet bajtů. Například pokud **_UNICODE** je definován následující volání do `CArchive` objekt nebude fungovat (`str` je `CString`):  
  
    ```  
    archive.Write( str, str.GetLength( ) );    // invalid  
    ```  
  
     V aplikaci Unicode délka umožňuje počet znaků, ale není správný počet bajtů, protože každý znak je 2 bajtů široké. Místo toho je nutné použít:  
  
    ```  
    archive.Write( str, str.GetLength( ) * sizeof( _TCHAR ) );    // valid  
    ```  
  
     Určuje, které správný počet bajtů k zápisu.  
  
     Ale MFC členské funkce, které jsou zaměřené na znak, nikoli orientované na bajtů fungovat bez další kódování:  
  
    ```  
    pDC->TextOut( str, str.GetLength( ) );  
    ```  
  
     `CDC::TextOut` přijímá a počet znaků, ne počet bajtů.  
  
-   Použití [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md) otevírat soubory Unicode.  
  
 To Shrneme, MFC a knihovna RTL – poskytuje následující podporu pro programování Unicode:  
  
-   S výjimkou funkce člena třídy databáze, jsou všechny funkce MFC kódování Unicode, včetně `CString`. `CString` také poskytuje funkce převodu znakové sady Unicode nebo ANSI.  
  
-   Knihovna RTL – poskytuje Unicode verze všechny funkce zpracování řetězců. (Běhové knihovny také poskytuje přenositelné verze vhodné pro kódování Unicode nebo MBCS. Jedná se o **_tcs** makra.)  
  
-   Tchar.h poskytuje přenosné datové typy a **_T** makro pro převod řetězců literálu a znaků. Další informace najdete v tématu [mapování obecného textu v souboru Tchar.h](../text/generic-text-mappings-in-tchar-h.md).  
  
-   Knihovna RTL – poskytuje široká charakterová verzi **hlavní**. Použití **wmain** aby vaše aplikace kódování Unicode.  
  
## <a name="see-also"></a>Viz také  
 [Podpora pro Unicode](../text/support-for-unicode.md)