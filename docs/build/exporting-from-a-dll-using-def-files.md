---
title: Export z knihovny DLL pomocí souborů .DEF
ms.date: 05/06/2019
helpviewer_keywords:
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
- exporting DLLs [C++], DEF files
ms.assetid: 9d31eda2-184e-47de-a2ee-a93ebd603f8e
ms.openlocfilehash: 6f7d58bcb42edd89527fff41b08a15321722a6cf
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80078525"
---
# <a name="exporting-from-a-dll-using-def-files"></a>Export z knihovny DLL pomocí souborů .DEF

Soubor definice modulu nebo DEF (*. def) je textový soubor obsahující jeden nebo více příkazů modulu, které popisují různé atributy knihovny DLL. Pokud nepoužíváte klíčové slovo **__declspec (dllexport)** pro export funkcí knihovny DLL, knihovna DLL vyžaduje soubor DEF.

Minimální DEF soubor musí obsahovat následující příkazy definice modulu:

- První příkaz v souboru musí být příkaz LIBRARY. Tento příkaz identifikuje DEF soubor jako patřící do knihovny DLL. Příkaz LIBRARY je následován názvem knihovny DLL. Linker umístí tento název do knihovny importu knihovny DLL.

- Příkaz EXPORTs Vypíše názvy a volitelně také ordinální hodnoty funkcí exportovaných knihovnou DLL. Funkci přiřadíte pořadovou hodnotu pomocí názvu funkce s znakem po znaku (@) a číslem. Když zadáte řadové hodnoty, musí být v rozsahu od 1 do N, kde N je počet funkcí exportovaných knihovnou DLL. Pokud chcete exportovat funkce podle pořadového čísla, přečtěte si téma [Export funkcí z knihovny DLL podle pořadových čísel, nikoli podle názvu](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md) a také v tomto tématu.

Například knihovna DLL, která obsahuje kód pro implementaci binárního vyhledávacího stromu, může vypadat takto:

```
LIBRARY   BTREE
EXPORTS
   Insert   @1
   Delete   @2
   Member   @3
   Min   @4
```

Použijete-li [Průvodce knihovnou MFC DLL](../mfc/reference/mfc-dll-wizard.md) k vytvoření knihovny MFC DLL, průvodce vytvoří soubor s kostrou pro vás a automaticky ho přidá do vašeho projektu. Přidejte názvy funkcí, které mají být exportovány do tohoto souboru. V případě knihoven DLL, které nejsou knihovny MFC, vytvořte soubor DEF sami a přidejte jej do projektu. Pak přejděte do **Project** > **vlastností** > **projektu linker** > **input** > **Module Definition File** a zadejte název def souboru. Tento krok opakujte pro každou konfiguraci a platformu, nebo to všechno najednou, a to tak, že vyberete **Konfigurace = všechny konfigurace**a **platforma = všechny platformy**.

Pokud exportujete funkce v souboru jazyka C++, je nutné buď umístit dekorované názvy do DEF souboru, nebo definovat exportované funkce pomocí standardního propojení jazyka C pomocí extern "C". Pokud potřebujete umístit dekorované názvy do souboru DEF, můžete je získat pomocí nástroje [DUMPBIN](../build/reference/dumpbin-reference.md) nebo pomocí možnosti linker [/map](../build/reference/map-generate-mapfile.md) . Všimněte si, že dekorované názvy vytvářené kompilátorem jsou specifické pro kompilátor. Pokud umístíte dekorované názvy vytvářené kompilátorem Microsoft C++ (MSVC) do DEF souboru, aplikace, které odkazují na vaši knihovnu DLL, musí být také sestaveny pomocí stejné verze MSVC, aby dekorované názvy v volající aplikaci odpovídaly exportovaným názvům v souboru DEF knihovny DLL.

> [!NOTE]
> Knihovna DLL vytvořená pomocí sady Visual Studio 2015 může být spotřebována aplikacemi sestavenými pomocí sady Visual Studio 2017 nebo sady Visual Studio 2019.

Pokud vytváříte [rozšiřující knihovnu DLL](../build/extension-dlls-overview.md)a exportujete pomocí def souboru, umístěte následující kód na začátek a konec hlavičkových souborů, které obsahují exportované třídy:

```
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

Tyto řádky zajistí, že proměnné MFC, které jsou použity interně nebo které jsou přidány do tříd, jsou exportovány (nebo importovány) z knihovny DLL rozšíření knihovny MFC. Například při odvozování třídy pomocí `DECLARE_DYNAMIC`se makro rozbalí a přidá `CRuntimeClass` členskou proměnnou do vaší třídy. Tyto čtyři řádky můžou způsobit, že vaše knihovna DLL nebude správně zkompilována nebo nesprávně fungovat, nebo může způsobit chybu, když klientská aplikace odkazuje na knihovnu DLL.

Při sestavování knihovny DLL používá linker soubor DEF k vytvoření souboru exportu (. exp) a souboru knihovny importu (. lib). Linker pak pomocí souboru exportu vytvoří soubor DLL. Spustitelné soubory, které jsou implicitně propojeny s knihovnou DLL, na knihovnu importů, když jsou sestaveny.

Všimněte si, že samotný MFC používá soubory DEF k exportu funkcí a tříd z knihovny MFCx0. dll.

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Export z knihovny DLL pomocí __declspec (dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Export a import pomocí AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Export funkcí jazyka C pro použití ve spustitelných souborech jazyka C nebo C++](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Určení metody exportu, která se má použít](determining-which-exporting-method-to-use.md)

- [Import do aplikace s použitím deklarace __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Inicializovat knihovnu DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>K čemu chcete získat další informace?

- [soubory. def](reference/module-definition-dot-def-files.md)

- [Pravidla pro příkazy definice modulu](reference/rules-for-module-definition-statements.md)

- [Dekorované názvy](reference/decorated-names.md)

- [Import a export vložených funkcí](importing-and-exporting-inline-functions.md)

- [Vzájemné importy](mutual-imports.md)

## <a name="see-also"></a>Viz také

[Export z knihovny DLL](exporting-from-a-dll.md)
