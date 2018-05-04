---
title: Sestavení knihovny importu a souboru exportu | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 93f817aadf2de826c628a14255ae9257be2f29ba
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="building-an-import-library-and-export-file"></a>Sestavení knihovny importu a souboru exportu
Sestavení knihovny importu a exportu souboru, použijte následující syntaxi:  
  
```  
LIB /DEF[:deffile] [options] [objfiles] [libraries]  
```  
  
 Pokud je zadána/DEF, LIB vytvoří výstupní soubory ze specifikací export, které se předávají v příkazu LIB. Existují tři metody pro určení exportů, uvedené v doporučené pořadí podle používání:  
  
1.  A **__declspec(dllexport)** definice v jednom z *objfiles* nebo *knihovny*  
  
2.  Specifikaci/export:*název* na příkazovém řádku LIB  
  
3.  Definice v **EXPORTUJE** příkaz v `deffile`  
  
 Jedná se o stejné metody, které se používá k určení exportů při propojování export programu. Program můžete použít více než jednu metodu. Můžete zadat části příkazu LIB (například více *objfiles* nebo/export specifikace) v soubor příkazů v příkazu LIB tak, jak jste můžete v příkazu odkaz.  
  
 Následující možnosti platí pro vytváření knihovnu importu a exportu souboru:  
  
 / OUT: *importovat*  
 Přepíše výchozí název výstupního souboru pro *importovat* knihovny vytváří. Pokud není zadána/out, výchozí název je základní název první objektu souboru nebo knihovny v rozšíření a příkaz LIB. lib. Export souboru je uveden základní stejný název jako knihovny importu a rozšíření. exp.  
  
 / EXPORT: *Název_položky*[= *internalname*] [, @ `ordinal`[, **NONAME**]] [, **DATA**]  
 Export funkce z vaší aplikace do jiných programů pro volání funkce. Můžete také exportovat data (pomocí **DATA** – klíčové slovo). Exportuje jsou obvykle definovány v knihovně DLL.  
  
 *Název_položky* je název položky funkce nebo data, jako je které volací program používat. Volitelně můžete zadat *internalname* jako funkce známé v programu definující; ve výchozím nastavení, *internalname* je stejný jako *Název_položky*. `ordinal` Určuje index do tabulky exportu v rozsahu od 1 do 65 535; Pokud nezadáte `ordinal`, LIB přiřadí jeden. **NONAME** – klíčové slovo exportuje funkce pouze jako pořadí, bez *Název_položky*. **DATA** – klíčové slovo slouží k exportu objekty jen data.  
  
 / PATŘÍ: `symbol`  
 Přidá zadaný symbol do tabulky symbolů. Tato možnost je užitečná pro vynucení použití objekt knihovny, který jinak by být zahrnut.  
  
 Všimněte si, že když vytvoříte své knihovny importu v předběžný krok před vytvořením vaší .dll, je nutné předat stejnou sadu soubory objektů při sestavování .dll, jako předaný při sestavení knihovny importu.  
  
## <a name="see-also"></a>Viz také  
 [Práce s knihovnami importu a soubory exportu](../../build/reference/working-with-import-libraries-and-export-files.md)