---
title: XML dokumentace (Visual C++)
ms.date: 11/04/2016
helpviewer_keywords:
- XML documentation
- XML, documentation comments in source code
- comments, C++ source code files
- /// delimiter for C++ documentation
ms.assetid: a1aec1c5-b2d1-4c74-83ae-1dbbbb76b506
ms.openlocfilehash: d111d601d966ec5f863d62d9788654101a2ab56d
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823093"
---
# <a name="xml-documentation-visual-c"></a>XML dokumentace (Visual C++)

V jazyce Visual C++ můžete přidat komentáře do zdrojového kódu, který se zpracuje do souboru .xml. Tento soubor pak může být vstup do procesu, který vytvoří dokumentaci pro třídy v kódu.

V souboru kódu jazyka Visual C++ dokumentační komentáře XML musí být umístěné přímo před definici metody nebo typu. Komentáře lze použít k naplnění popisu dat rychlé informace technologie IntelliSense v následujících scénářích:

1. Pokud kód je zkompilován jako součást prostředí Windows Runtime s související soubor winmd

1. Pokud je zdrojový kód součástí aktuálního projektu

1. v knihovně, jehož typ deklarace a implementaci jsou umístěné ve stejném souboru záhlaví

> [!NOTE]
>  V aktuální verzi nebudou zpracovány komentářích ke kódu v šablonách nebo nic obsahující typ šablony (například funkci s parametrem jako šablonu). Přidání komentářů do takové způsobí nedefinované chování.

Podrobné informace o vytváření souboru XML s komentáře k dokumentaci naleznete v následujících tématech.

|Informace o|Další informace naleznete v tématu|
|---------------------------|---------|
|Použití možnosti kompilátoru|[/doc](doc-process-documentation-comments-c-cpp.md)|
|Značky, které můžete použít k poskytování běžně používané funkce v dokumentaci|[Doporučené značky pro komentáře dokumentace](recommended-tags-for-documentation-comments-visual-cpp.md)|
|ID řetězce, které kompilátor vytvoří k identifikaci jaké konstrukty jsou ve vašem kódu|[Zpracování souboru XML](dot-xml-file-processing.md)|
|Jak pro vymezení značky dokumentace|[Oddělovače pro dokumentační značky ve Visual C++](delimiters-for-visual-cpp-documentation-tags.md)|
|Generuje se soubor XML z jednoho nebo více souborů .xdc.|[Referenční dokumentace nástroje XDCMake](xdcmake-reference.md)|
|Odkazy na informace o XML, protože má vztah k oblasti funkcí sady Visual Studio|[XML v sadě Visual Studio](/visualstudio/xml-tools/xml-tools-in-visual-studio)|

Pokud potřebujete změnit speciální znaky XML na text komentáře dokumentace, musíte použít entity XML nebo oddíl CDATA.

## <a name="see-also"></a>Viz také:

[Přípony komponent pro platformy běhového prostředí](../../windows/component-extensions-for-runtime-platforms.md)