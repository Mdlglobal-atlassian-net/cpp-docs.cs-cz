---
title: "Souhrn programování Unicode | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- Unicode [C++], programming with
- Unicode [C++], MFC and C run-time functions
ms.assetid: a4c9770f-6c9c-447c-996b-980920288bed
caps.latest.revision: "8"
author: ghogen
ms.author: ghogen
manager: ghogen
ms.openlocfilehash: f038a33fc46ec897b734555793a1290527f2e04b
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
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
  
     S **_UNICODE** definované, **_T –** překládá řetězcového literálu do formuláře předpony L; jinak hodnota **_T** převede řetězec bez předpony l..  
  
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
  
     `CDC::TextOut`přijímá a počet znaků, ne počet bajtů.  
  
-   Použití [fopen_s, _wfopen_s](../c-runtime-library/reference/fopen-s-wfopen-s.md) otevírat soubory Unicode.  
  
 To Shrneme, MFC a knihovna RTL – poskytují následující podpora pro Unicode programování v systému Windows 2000:  
  
-   S výjimkou funkce člena třídy databáze, jsou všechny funkce MFC kódování Unicode, včetně `CString`. `CString`také poskytuje funkce převodu znakové sady Unicode nebo ANSI.  
  
-   Knihovna RTL – poskytuje Unicode verze všechny funkce zpracování řetězců. (Běhové knihovny také poskytuje přenositelné verze vhodné pro kódování Unicode nebo MBCS. Jedná se o **_tcs** makra.)  
  
-   Tchar.h poskytuje přenosné datové typy a **_T** makro pro převod řetězců literálu a znaků. Další informace najdete v tématu [mapování obecného textu v souboru Tchar.h](../text/generic-text-mappings-in-tchar-h.md).  
  
-   Knihovna RTL – poskytuje široká charakterová verzi **hlavní**. Použití **wmain** aby vaše aplikace kódování Unicode.  
  
## <a name="see-also"></a>Viz také  
 [Podpora kódování Unicode](../text/support-for-unicode.md)