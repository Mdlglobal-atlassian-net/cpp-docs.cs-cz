---
title: Dokumentace XML (Visual C++) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- XML documentation
- XML, documentation comments in source code
- comments, C++ source code files
- /// delimiter for C++ documentation
ms.assetid: a1aec1c5-b2d1-4c74-83ae-1dbbbb76b506
caps.latest.revision: "18"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: fb5b9968ad652e5ab6ef4dd29eb3c6ccc6da7493
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="xml-documentation-visual-c"></a>XML dokumentace (Visual C++)
V jazyce Visual C++ můžete přidat komentář ke zdrojovému kódu, který bude zpracován do souboru .xml. Tento soubor pak může být vstup proces, který vytvoří dokument pro třídy v kódu.  
  
 V souboru kódu Visual C++ dokumentační komentáře XML musí být umístěn přímo před definici metody nebo typu. Komentáře můžete použít k naplnění dat tip Intellisense QuickInfo v následujících scénářích:  
  
1.  Pokud je kód kompilována jako součást prostředí Windows Runtime s přidružený soubor .winmd  
  
2.  Pokud zdrojový kód je součástí aktuálního projektu  
  
3.  v knihovně, jehož typ deklarace a implementace jsou umístěny ve stejném souboru záhlaví  
  
> [!NOTE]
>  V aktuální verzi nebudou zpracovány komentáře kódu na šablony nebo nic obsahující typ šablony (například funkce trvá parametr jako šablonu). Přidávání takové komentářů způsobí nedefinované chování.  
  
 Podrobné informace o vytváření souboru .xml s dokumentační komentáře naleznete v následujících tématech.  
  
|Informace o|Další informace naleznete v tématu|  
|---------------------------|---------|  
|Možnosti kompilátoru používat|[/ DOC](../build/reference/doc-process-documentation-comments-c-cpp.md)|  
|Značky, které můžete použít k poskytování běžně používané funkce v dokumentaci k|[Doporučené značky pro dokumentační komentáře](../ide/recommended-tags-for-documentation-comments-visual-cpp.md)|  
|ID řetězce, které vytváří kompilátor k identifikaci konstrukce v kódu|[Zpracování souboru XML](../ide/dot-xml-file-processing.md)|  
|Postupy pro vymezení značky dokumentace|[Oddělovače pro dokumentační značky jazyka Visual C++](../ide/delimiters-for-visual-cpp-documentation-tags.md)|  
|Generování souboru .xml z jednoho nebo více soubory.|[Referenční dokumentace nástroje XDCMake](../ide/xdcmake-reference.md)|  
|Odkazy na informace o XML, protože má vztah k oblastech funkce sady Visual Studio|[XML v sadě Visual Studio](/visualstudio/xml-tools/xml-tools-in-visual-studio)|  
  
 Pokud potřebujete uvést speciální znaky XML do text komentáře dokumentace, musíte použít entity XML nebo oddílu CDATA.  
  
## <a name="see-also"></a>Viz také  
 [Rozšíření komponent pro platformy běhového prostředí](../windows/component-extensions-for-runtime-platforms.md)