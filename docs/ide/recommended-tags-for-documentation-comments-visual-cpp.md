---
title: "Doporučené značky pro dokumentační komentáře (Visual C++) | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 5c1b0e762ec2167a988e8e18f3dce932214716c9
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="recommended-tags-for-documentation-comments-visual-c"></a>Doporučené značky pro dokumentační komentáře (Visual C++)
Visual C++ compiler zpracuje dokumentační komentáře v kódu a vytvoří soubor projektový pro každý kompilace a xdcmake.exe zpracovává soubory projektový do souboru .xml. Zpracování souboru XML k vytvoření dokumentace je podrobností, která musí být implementována ve vaší lokalitě.  
  
 Značky jsou zpracovávány na konstruktory, jako jsou typy a členy typu.  
  
 Značky musí předcházet okamžitě typy nebo členy.  
  
> [!NOTE]
>  Dokumentační komentáře nelze použít do oboru názvů, nebo na mimo řádek definice vlastností a událostí; dokumentační komentáře musí být na deklaracích v třídy.  
  
 Kompilátor zpracuje všechny značky, který je platný kód XML. Následující značky poskytují běžně používané funkce v dokumentaci pro uživatele:  
  
||||  
|-|-|-|  
|[\<c >](../ide/c-visual-cpp.md)|[\<kód >](../ide/code-visual-cpp.md)|[\<Příklad >](../ide/example-visual-cpp.md)|  
|[\<Výjimka >](../ide/exception-visual-cpp.md)1|[\<Zahrnout >](../ide/include-visual-cpp.md)1|[\<Seznam >](../ide/list-visual-cpp.md)|  
|[\<para >](../ide/para-visual-cpp.md)|[\<Param >](../ide/param-visual-cpp.md)1|[\<paramref >](../ide/paramref-visual-cpp.md)1|  
|[\<oprávnění >](../ide/permission-visual-cpp.md)1|[\<Poznámky >](../ide/remarks-visual-cpp.md)|[\<Vrátí >](../ide/returns-visual-cpp.md)|  
|[\<v tématu >](../ide/see-visual-cpp.md)1|[\<Viz také >](../ide/seealso-visual-cpp.md)1|[\<Souhrn >](../ide/summary-visual-cpp.md)|  
|[\<Hodnota >](../ide/value-visual-cpp.md)|||  
  
 1. Kompilátoru ověří syntaxi.  
  
 V aktuální verzi Visual C++ compiler nepodporuje `<paramref>`, značku, která je podporována jinými kompilátory Visual Studio. Visual C++ můžou podporovat `<paramref>` v budoucí verzi.  
  
## <a name="see-also"></a>Viz také  
 [Dokumentace XML](../ide/xml-documentation-visual-cpp.md)