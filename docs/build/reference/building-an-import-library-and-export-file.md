---
title: Sestavení knihovny importu a exportu souboru | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLibrarianTool.ModuleDefinitionFile
- VC.Project.VCLibrarianTool.ExportNamedFunctions
- VC.Project.VCLibrarianTool.GenerateDebug
- VC.Project.VCLibrarianTool.ForceSymbolReferences
dev_langs:
- C++
helpviewer_keywords:
- OUT library manager option
- INCLUDE library manager option
- /DEF library manager option
- exporting data
- import libraries, building
- -INCLUDE library manager option
- /OUT library manager option
- DEF library manager option
- -DEF library manager option
- -OUT library manager option
- /INCLUDE library manager option
- -EXPORT library manager option
- exporting data, export (.exp) files
- /EXPORT library manager option
- EXPORT library manager option
- .lib files
- EXP files
ms.assetid: 2fe4f30a-1dd6-4b05-84b5-0752e1dee354
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c832ee24d500eba28c14713d1c0a092baf90a440
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894613"
---
# <a name="building-an-import-library-and-export-file"></a>Sestavení knihovny importu a souboru exportu

Sestavit knihovnu importu a exportu souboru, použijte následující syntaxi:

> **DEF LIB**[**:**<em>deffile</em>] [*možnosti*] [*objfiles*] [*knihovny*]

Pokud je zadána DEF, LIB vytvoří výstupní soubory z specifikace exportu, které jsou předány v příkazu LIB. Existují tři metody pro určení exportů uvedené v doporučené pořadí podle používání:

1. A **__declspec(dllexport)** definice v jednom z *objfiles* nebo *knihovny*

2. Specifikaci/Export je přebytečný:*název* na příkazovém řádku LIB

3. V definici **EXPORTY** příkaz v *deffile*

Jedná se o stejné metody, které se používá k určení exportů při propojování export programu. Program můžete použít více než jednu metodu. Můžete zadat část příkazu LIB (například více *objfiles* nebo specifikaci/Export je přebytečný) v souboru příkazů v příkazu LIB, stejně jako lze v příkazu LINK.

Následující možnosti platí pro vytváření knihovny importu a exportu souboru:

> **/ OUT:** *importovat*  

Přepíše výchozí název výstupního souboru pro *importovat* knihovna vytváří. Když se parametr/out nezadá, výchozí název je základní název prvního souboru objektu nebo knihovny v příkazu LIB a příponou. lib. Export souboru je uveden stejný základní název knihovny importu a rozšíření. exp.

> **/ EXPORT:** *Název_položky* \[ **=** *internalname*]\[,**\@** <em>ordinální</em>\[, **NONAME**]]\[, **DATA**]

Exportuje funkci ve svém programu povolit programy pro volání funkce. Data můžete také exportovat (pomocí **DATA** – klíčové slovo). Exporty jsou obvykle definovány v knihovně DLL.

*Název_položky* je název položky funkci nebo data, jako je pro volající program. Volitelně můžete zadat *internalname* jako funkce, která označuje definující programu; ve výchozím nastavení, *internalname* je stejný jako *Název_položky*. *Ordinální* Určuje index do tabulky exportu v rozsahu od 1 do 65 535; Pokud nezadáte *ordinální*, LIB přiřadí jednu. **NONAME** – klíčové slovo exportuje funkci pouze ordinální číslo, aniž by *Název_položky*. **DATA** – klíčové slovo slouží k exportu dat jen pro objekty.

> **/ INCLUDE:** *symbol*

Přidá zadaný *symbol* do tabulky symbolů. Tato možnost je užitečná pro vynucení použití objektu knihovny, který jinak by být zahrnut.

Všimněte si, že když vytvoříte knihovny importu v předběžný krok před vytvořením vaší knihovny DLL, je nutné předat stejnou sadu souborů objektů při sestavování knihovny DLL, jako úspěšný při sestavování knihovny importu.

## <a name="see-also"></a>Viz také

[Práce s knihovnami importu a soubory exportu](../../build/reference/working-with-import-libraries-and-export-files.md)