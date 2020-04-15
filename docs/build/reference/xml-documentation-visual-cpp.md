---
title: XML dokumentace (Visual C++)
ms.date: 11/04/2016
helpviewer_keywords:
- XML documentation
- XML, documentation comments in source code
- comments, C++ source code files
- /// delimiter for C++ documentation
ms.assetid: a1aec1c5-b2d1-4c74-83ae-1dbbbb76b506
ms.openlocfilehash: c25c54e81bb9c10fc871a2abc178f57e661ae4e6
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81335722"
---
# <a name="xml-documentation-visual-c"></a>XML dokumentace (Visual C++)

V jazyce Visual C++ můžete přidat komentáře ke zdrojovému kódu, které budou zpracovány do souboru XML. Tento soubor pak může být vstup do procesu, který vytvoří dokumentaci pro třídy ve vašem kódu.

V souboru kódu Visual C++ musí být komentáře dokumentace XML umístěny přímo před definicí metody nebo typu. Komentáře lze použít k naplnění tipu dat IntelliSense QuickInfo v následujících scénářích:

1. Pokud je kód kompilován jako součást prostředí Windows Runtime s doprovodným souborem .winmd

1. pokud je zdrojový kód zahrnut do aktuálního projektu

1. v knihovně, jejíž deklarace typu a implementace jsou umístěny ve stejném souboru záhlaví

> [!NOTE]
> V aktuální verzi komentáře kódu nejsou zpracovány na šablony nebo nic, co obsahuje typ šablony (například funkce s parametrem jako šablona). Přidání těchto komentářů bude mít za následek nedefinované chování.

Podrobnosti o vytvoření souboru XML s poznámkami k dokumentaci naleznete v následujících tématech.

|Informace o|Seznamte se s |
|---------------------------|---------|
|Možnosti kompilátoru, které se mají použít|[/doc](doc-process-documentation-comments-c-cpp.md)|
|Značky, které můžete použít k poskytování běžně používaných funkcí v dokumentaci|[Doporučené značky pro komentáře k dokumentaci](recommended-tags-for-documentation-comments-visual-cpp.md)|
|ID řetězce, které kompilátor vytváří k identifikaci konstrukce v kódu|[Zpracování souboru XML](dot-xml-file-processing.md)|
|Jak vymezit značky dokumentace|[Oddělovače pro dokumentační značky ve Visual C++](delimiters-for-visual-cpp-documentation-tags.md)|
|Generování souboru XML z jednoho nebo více souborů .xdc.|[Referenční dokumentace nástroje XDCMake](xdcmake-reference.md)|
|Odkazy na informace o xml týkající se oblastí funkcí sady Visual Studio|[XML v sadě Visual Studio](/visualstudio/xml-tools/xml-tools-in-visual-studio)|

Pokud potřebujete vložit speciální znaky XML do textu komentáře v dokumentaci, musíte použít entity XML nebo oddíl CDATA.

## <a name="see-also"></a>Viz také

[Přípony komponent pro platformy běhového prostředí](../../extensions/component-extensions-for-runtime-platforms.md)
