---
title: Export z knihovny DLL pomocí souborů .DEF
ms.date: 01/09/2018
helpviewer_keywords:
- def files [C++], exporting from DLLs
- .def files [C++], exporting from DLLs
- exporting DLLs [C++], DEF files
ms.assetid: 9d31eda2-184e-47de-a2ee-a93ebd603f8e
ms.openlocfilehash: 35f55ea525bd03c5b0b1b1750d25c1223bc608fc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62195474"
---
# <a name="exporting-from-a-dll-using-def-files"></a>Export z knihovny DLL pomocí souborů .DEF

Definice modulu nebo soubor DEF (*.def) je textový soubor obsahující jeden nebo více příkazů modulu, které popisují různé atributy knihovny DLL. Pokud nepoužíváte **__declspec(dllexport)** – klíčové slovo export funkcí knihovny DLL, pak vyžaduje knihovna DLL soubor DEF.

Minimální soubor DEF musí obsahovat následující příkazy definice modulu:

- Prvním příkazem v souboru musí být příkaz LIBRARY. Tento příkaz určuje soubor DEF jako patřící do knihovny DLL. Příkaz LIBRARY je následován názvem knihovny DLL. Propojovací program umístí tento název v knihovně importu knihovny DLL.

- Příkaz EXPORTS uvádí seznam názvů a volitelně pořadové hodnoty funkcí exportovaných knihovnou DLL. Funkci přiřadíte pořadové hodnoty podle názvu funkce zavináč (@) a číslo. Zadané pořadové hodnoty musí být v rozsahu 1 až N, kde N je počet funkcí exportovaných knihovnou DLL. Pokud chcete exportovat funkce podle řádu, přečtěte si téma [export funkcí z DLL Knihovny podle řádu, než podle názvu](exporting-functions-from-a-dll-by-ordinal-rather-than-by-name.md) stejně jako v tomto tématu.

Například knihovnu DLL, která obsahuje kód pro implementaci binárního vyhledávacího stromu, může vypadat takto:

```
LIBRARY   BTREE
EXPORTS
   Insert   @1
   Delete   @2
   Member   @3
   Min   @4
```

Pokud používáte [Průvodce MFC DLL](../mfc/reference/mfc-dll-wizard.md) k vytvoření knihovny DLL MFC, Průvodce pro vás vytvoří kostru souboru .def a automaticky přidá do vašeho projektu. Přidejte názvy funkcí, které mají být exportovány do tohoto souboru. Pro non - MFC knihovny DLL, vytvořit soubor DEF sami a přidejte ho do projektu. Pak přejděte na **projektu** > **vlastnosti** > **Linkeru** > **vstup**  >  **Soubor definice modulu** a zadejte název souboru definice. Tento krok opakujte pro každou konfiguraci a platformu, nebo provést všechny najednou tak, že vyberete **konfiguraci = všechny konfigurace**, a **platformy = všechny platformy**.

Pokud exportujete funkce v souboru jazyka C++, musíte umístit do souboru .def dekorované názvy nebo definovat vámi exportované funkce standardním C propojením pomocí externího "C". Pokud je potřeba umístit souboru .def dekorované názvy, můžete je získat pomocí [DUMPBIN](../build/reference/dumpbin-reference.md) nástroj nebo pomocí volby propojovacího programu [/MAP](../build/reference/map-generate-mapfile.md) možnost. Všimněte si, že dekorované názvy produkované kompilátorem jsou specifické pro kompilátor. Pokud umístíte dekorované názvy produkované kompilátorem jazyka Visual C++ do souboru definice, aplikace, které jsou propojeny s DLL Knihovnou musí také být vytvářejí pomocí stejné verze aplikace Visual C++ tak, aby dekorované názvy ve volání aplikace odpovídaly exportovaným názvům v knihovně DLL DEF f soubor.

Pokud vytváříte [rozšiřující knihovny DLL](../build/extension-dlls-overview.md), a exportujete pomocí souboru .def, umístěte následující kód na začátek a konec souborů hlaviček, které obsahují exportované třídy:

```
#undef AFX_DATA
#define AFX_DATA AFX_EXT_DATA
// <body of your header file>
#undef AFX_DATA
#define AFX_DATA
```

Tyto řádky zajistí, že proměnné knihovny MFC, která se používají interně nebo jsou přidané do třídy jsou exportovány (nebo importovány) z vaší MFC – rozšiřující knihovny DLL. Například při odvození třídy pomocí `DECLARE_DYNAMIC`, makro rozbalí a přidá `CRuntimeClass` členské proměnné do vaší třídy. Vynechání těchto čtyř řádků může způsobit, že vaše knihovna DLL pro kompilaci nebo propojit nesprávně nebo může způsobit chybu, když klientská aplikace odkazovat na knihovnu DLL.

Při sestavování knihovny DLL, linker používá soubor DEF k vytvoření souboru exportu (.exp) a soubor importu knihovny (.lib). Propojovací program poté použije exportní soubor pro sestavení souboru DLL. Spustitelné soubory, které jsou implicitně propojené na odkaz DLL s importovanou knihovnou při sestavení.

Všimněte si, že knihovna MFC sama používá soubory DEF pro export funkcí a tříd z knihovny MFCx0.dll.

## <a name="what-do-you-want-to-do"></a>Co chcete udělat?

- [Export z knihovny DLL pomocí __declspec(dllexport)](exporting-from-a-dll-using-declspec-dllexport.md)

- [Export a import pomocí AFX_EXT_CLASS](exporting-and-importing-using-afx-ext-class.md)

- [Export funkcí jazyka C++ pro použití ve spustitelných souborech jazyka C](exporting-cpp-functions-for-use-in-c-language-executables.md)

- [Export funkcí jazyka C pro použití ve spustitelných souborech jazyka C nebo C++ – jazyk](exporting-c-functions-for-use-in-c-or-cpp-language-executables.md)

- [Určit, kterou exportovací metodu použít](determining-which-exporting-method-to-use.md)

- [Import do aplikace s použitím deklarace __declspec(dllimport)](importing-into-an-application-using-declspec-dllimport.md)

- [Inicializace knihovny DLL](run-time-library-behavior.md#initializing-a-dll)

## <a name="what-do-you-want-to-know-more-about"></a>Co chcete zjistit více informací?

- [soubory .def](reference/module-definition-dot-def-files.md)

- [Pravidla pro příkazy definice modulu](reference/rules-for-module-definition-statements.md)

- [Dekorované názvy](reference/decorated-names.md)

- [Import a export vložených funkcí](importing-and-exporting-inline-functions.md)

- [Vzájemné importy](mutual-imports.md)

## <a name="see-also"></a>Viz také:

[Export z knihovny DLL](exporting-from-a-dll.md)
