---
title: "Používání příkazů dllimport a dllexport ve třídách jazyka C++ | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- exporting classes [C++]
- declarations [C++], class
- exportable classes [C++]
- classes [C++], declaring
- classes [C++], exportable and inheritance
- inheritance [C++], exportable classes [C++]
- dllimport attribute [C++], classes
- declaring classes [C++]
- dllexport attribute [C++]
- dllexport attribute [C++], classes [C++]
ms.assetid: 8d7d1303-b9e9-47ca-96cc-67bf444a08a9
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d8f9434387efcf3377cdc983116a51b524d16662
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="using-dllimport-and-dllexport-in-c-classes"></a>Používání příkazů dllimport a dllexport ve třídách jazyka C++
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Je možné deklarovat tříd C++ pomocí **dllimport** nebo `dllexport` atribut. Tyto formuláře určeno, že je celou třídu importovat nebo exportovat. Třídy exportovat tímto způsobem se označují jako exportovatelné třídy.  
  
 Následující příklad definuje třídu exportovatelný. Exportují se všechny jeho členských funkcí a statických dat:  
  
```  
#define DllExport   __declspec( dllexport )  
  
class DllExport C {  
   int i;  
   virtual int func( void ) { return 1; }  
};  
```  
  
 Všimněte si, že explicitní použití **dllimport** a `dllexport` atributy u členů exportovatelné třídy je zakázáno.  
  
##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bdllexportclasses"></a>dllexport – třídy  
 Když deklarování třídy `dllexport`, jeho členských funkcí a členy statických dat jsou exportovány. Je nutné zadat definice všichni členové takových stejný program. Chyba linkerů, jinak se generuje. Jedinou výjimkou toto pravidlo se vztahuje na čistý virtuální funkce, pro které nemusí poskytovat explicitní definice. Ale protože destruktor pro abstraktní třídu vždy volá destruktor pro základní třídu, čistý virtuální destruktorů musí vždy poskytovat definici. Všimněte si, že tato pravidla jsou stejné pro nonexportable třídy.  
  
 Při exportu dat typu třídy nebo funkce, které vrací třídy, je nutné exportovat třídy.  
  
##  <a name="_pluslang_dllexport_classesdllexportclasses"></a>DllImport – třídy  
 Když deklarování třídy **dllimport**, jeho členských funkcí a členy statických dat jsou importovány. Na rozdíl od chování **dllimport** a `dllexport` na typech nonclass členy statických dat nelze zadat definici ve stejné aplikaci, ve kterém **dllimport** třída definovaná.  
  
##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2binheritanceandexportableclasses"></a>Exportovatelné třídy a dědičnost  
 Všechny základní třídy exportovatelné třídy musí být exportovatelný. V opačném případě se generuje upozornění kompilátoru. Všechny dostupné členy, kteří jsou také třídy kromě toho musí být exportovatelný. Toto pravidlo umožňuje `dllexport` třídy dědí **dllimport** třída a **dllimport** třídy dědí `dllexport` třídy (i když tento není doporučeno). Pravidlo vše, které je přístupné pro knihovnu DLL klienta (podle pravidel C++ přístup) musí být součástí rozhraní exportovatelný. To zahrnuje privátní datových členů v vložené funkce odkazuje.  
  
##  <a name="_pluslang_using_dllimport_and_dllexport_in_c2b2bselectivememberimportexport"></a>Selektivní člen importu a exportu  
 Vzhledem k tomu členských funkcí a statických dat v rámci třídy implicitně externí propojení, je lze deklarovat s **dllimport** nebo `dllexport` atribut, pokud se exportují celou třídu. Pokud je importovat nebo exportovat, explicitní deklaraci členských funkcí a data jako celou třídu **dllimport** nebo `dllexport` je zakázáno. Pokud je deklarovat členem statických dat v definici třídy jako `dllexport`, definice musí nastat někde v stejný program (stejně jako u externí propojení nonclass).  
  
 Podobně deklarovat členské funkce s **dllimport** nebo `dllexport` atributy. V takovém případě je nutné zadat `dllexport` definice někde v rámci stejné aplikaci.  
  
 Je vhodné poznamenat několik důležitých bodů týkající se selektivní člen import a export:  
  
-   Selektivní člen importu a exportu je nejvhodnější pro zajištění verzi rozhraní exportované třídy, které je víc omezující; To znamená jednu pro kterou můžete navrhnout knihovny DLL, která zveřejňuje méně veřejné a privátní funkcí než jazyk by jinak povolit. Je také užitečné pro optimalizaci rozhraní exportovatelný: když víte, že klienta podle definice, nelze získat přístup k některé osobní data, není nutné exportovat celou třídu.  
  
-   Při exportu jeden virtuální funkce do třídy, musíte exportovat všechny nebo alespoň poskytují verze, které může klient použít přímo.  
  
-   Pokud máte třídu, ve kterém používáte selektivní člen importu a exportu s virtuální funkce, funkce musí být exportovatelný rozhraní nebo definovanými v řádku (viditelné klienta).  
  
-   Pokud definujete člena jako `dllexport` ale nezahrnují v definici třídy, je generována chyba kompilátoru. Člen je nutné definovat v hlavičce třídy.  
  
-   I když definici členy třídy jako **dllimport** nebo `dllexport` je povoleno, nelze přepsat rozhraní zadaný v definici třídy.  
  
-   Pokud definujete členské funkce na místě, než text definice třídy, ve kterém je deklarovaná, se generuje upozornění, pokud funkci je definován jako `dllexport` nebo **dllimport** (Pokud tuto definici se liší od zadaný v deklaraci třídy).  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [dllexport, dllimport](../cpp/dllexport-dllimport.md)