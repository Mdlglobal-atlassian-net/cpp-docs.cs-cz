---
title: Export z knihovny DLL pomocí souborů DEF | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
- exporting DLLs [C++], DEF files
ms.assetid: 9d31eda2-184e-47de-a2ee-a93ebd603f8e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a870df7ea803813a8403cd807c0f0612873d4576
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="exporting-from-a-dll-using-def-files"></a>Export z knihovny DLL pomocí souborů .DEF
Soubor definice modulu (.def) je textový soubor obsahující jeden nebo více příkazů modulu, které popisují různé atributy knihovny DLL. Pokud nepoužíváte **__declspec(dllexport)** – klíčové slovo pro export funkcí knihovny DLL, knihovny DLL vyžaduje .def souboru.  
  
 Minimální .def soubor musí obsahovat následující příkazy definice modulu:  
  
-   První příkaz v souboru musí být příkaz KNIHOVNY. Tento příkaz identifikuje soubor .def jako náležící do knihovny DLL. Příkaz KNIHOVNY následuje název knihovny DLL. Linkeru umístí tento název knihovny importu knihovnu DLL.  
  
-   Příkaz Export uvádí názvy a volitelně pořadové hodnoty funkce exportované sadou knihovnu DLL. Přiřadíte pořadové hodnoty pro funkci podle názvu funkce s znaku zavináče (@) a číslo. Když zadáte ordinální hodnoty, musí být v rozsahu 1 až N, kde N je počet funkce exportované sadou knihovnu DLL. Pokud chcete exportovat funkce podle pořadí, v tématu [export funkcí z knihovny DLL podle pořadí, nikoli podle názvu](../build/exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md) a také v tomto tématu.  
  
 Například knihovny DLL, která obsahuje kód pro implementaci stromu binární vyhledávání může vypadat následovně:  
  
```  
LIBRARY   BTREE  
EXPORTS  
   Insert   @1  
   Delete   @2  
   Member   @3  
   Min   @4  
```  
  
 Pokud použijete [MFC DLL – průvodce](../mfc/reference/mfc-dll-wizard.md) k vytvoření knihovny MFC DLL, Průvodce pro vás vytvoří kostru souboru .def a automaticky přidá do projektu. Přidáte názvy funkcí, které mají být exportovány do tohoto souboru. Pro non - MFC DLL, musíte vytvořit .def soubor a přidejte do projektu.  
  
 Pokud exportujete funkce v souboru C++, musíte umístit soubor .def dekorované názvy nebo definujte exportované funkce standardní propojení C pomocí extern "C". Pokud potřebujete umístit dekorované názvy souborů .def, můžete je získat pomocí [DUMPBIN](../build/reference/dumpbin-reference.md) nástroje nebo pomocí linkeru [/MAP](../build/reference/map-generate-mapfile.md) možnost. Upozorňujeme, že dekorované názvy produkované kompilátorem jsou specifické pro kompilátor. Pokud umístíte dekorované názvy vyprodukované – kompilátor Visual C++ do souboru .def, aplikace, které odkazují na knihovny DLL musí také být vytvořená s využitím stejnou verzi nástroje Visual C++ tak, aby odpovídaly exportovaný názvy v knihovně DLL .de dekorované názvy v volající aplikace f soubor.  
  
 Pokud vytváříte [rozšíření knihovny DLL](../build/extension-dlls-overview.md), a export pomocí souborů .def, umístěte následující kód na začátku a konci vaší hlavičky souborů, které obsahují exportované třídy:  
  
```  
#undef AFX_DATA  
#define AFX_DATA AFX_EXT_DATA  
// <body of your header file>  
#undef AFX_DATA  
#define AFX_DATA  
```  
  
 Tyto řádky zajistěte, aby MFC proměnné, která se používá interně nebo které jsou přidány do vaší třídy exportovat (nebo importovat) z vaší MFC – rozšiřující knihovny DLL. Například když odvození třídy pomocí `DECLARE_DYNAMIC`, se rozbalí makro pro přidání `CRuntimeClass` členské proměnné na třídu. Opouštění těchto čtyř řádků může způsobit vaše knihovna DLL zkompilovat nebo nesprávně propojení nebo způsobit chybu, pokud klientská aplikace odkazuje na knihovnu DLL.  
  
 Při vytváření knihovny DLL, používá linkeru .def soubor k vytvoření souboru exportu (.exp) a soubor importu knihovny (LIB). Linkeru pro sestavení souboru DLL použije soubor exportu. Spustitelné soubory, které implicitně propojit odkaz DLL knihovny importu při sestavení.  
  
 Všimněte si, že knihovna MFC sama používá soubory .def export z knihovny MFCx0.dll třídy a funkce.  
  
## <a name="what-do-you-want-to-do"></a>Co chcete udělat?  
  
-   [Export z knihovny DLL pomocí deklarace __declspec(dllexport)](../build/exporting-from-a-dll-using-declspec-dllexport.md)  
  
-   [Export a import pomocí třídy AFX_EXT_CLASS](../build/exporting-and-importing-using-afx-ext-class.md)  
  
-   [Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C](../build/exporting-cpp-functions-for-use-in-c-language-executables.md)  
  
-   [Export funkcí jazyka C pro použití ve spustitelných souborech jazyka C nebo jazyka C++](../build/exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)  
  
-   [Určení použité metody exportu](../build/determining-which-exporting-method-to-use.md)  
  
-   [Import do aplikace pomocí deklarace __declspec(dllimport)](../build/importing-into-an-application-using-declspec-dllimport.md)  
  
-   [Inicializace knihovny DLL](../build/run-time-library-behavior.md#initializing-a-dll)  
  
## <a name="what-do-you-want-to-know-more-about"></a>Co chcete vědět více o?  
  
-   [soubory .def](../build/reference/module-definition-dot-def-files.md)  
  
-   [Pravidla pro příkazy definice modulu](../build/reference/rules-for-module-definition-statements.md)  
  
-   [Dekorované názvy](../build/reference/decorated-names.md)  
  
-   [Import a export vložených funkcí](../build/importing-and-exporting-inline-functions.md)  
  
-   [Vzájemné importy](../build/mutual-imports.md)  
  
## <a name="see-also"></a>Viz také  
 [Export z knihovny DLL](../build/exporting-from-a-dll.md)