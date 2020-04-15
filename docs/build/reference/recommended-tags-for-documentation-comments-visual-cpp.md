---
title: Doporučené značky pro komentáře k dokumentaci (komentáře k dokumentaci jazyka C++)
ms.date: 11/04/2016
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
ms.openlocfilehash: 1648d0eb019a3aad25641d7f6a7edd1ba26acf7e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81336176"
---
# <a name="recommended-tags-for-documentation-comments"></a>Doporučené značky pro komentáře dokumentace

Kompilátor MSVC zpracuje komentáře dokumentace ve vašem kódu a vytvoří soubor .xdc pro každý compiland a xdcmake.exe zpracuje soubory .xdc do souboru XML. Zpracování souboru XML za účelem vytvoření dokumentace je detail, který je třeba implementovat na vašem webu.

Značky jsou zpracovávány na konstrukcích, jako jsou typy a členy typu.

Značky musí bezprostředně předcházet typům nebo členům.

> [!NOTE]
> Komentáře dokumentace nelze použít v oboru názvů nebo na mimořádek definice vlastností a událostí; poznámky v dokumentaci musí být k prohlášením ve třídě.

Kompilátor zpracuje všechny značky, které jsou platné XML. Následující značky poskytují běžně používané funkce v uživatelské dokumentaci:

||||
|-|-|-|
|[\<c>](c-visual-cpp.md)|[\<kód>](code-visual-cpp.md)|[\<příklad>](example-visual-cpp.md)|
|výjimka>1 [ \< ](exception-visual-cpp.md)|patří>1 [ \< ](include-visual-cpp.md)|[\<seznam>](list-visual-cpp.md)|
|[\<para>](para-visual-cpp.md)|param>1 [ \< ](param-visual-cpp.md)|paramref>1 [ \< ](paramref-visual-cpp.md)|
|[ \<>1. ](permission-visual-cpp.md)|[\<poznámky>](remarks-visual-cpp.md)|[\<vrátí>](returns-visual-cpp.md)|
|viz>1 [ \< ](see-visual-cpp.md)|seealso>1 [ \< ](seealso-visual-cpp.md)|[\<souhrnný>](summary-visual-cpp.md)|
|[\<hodnota>](value-visual-cpp.md)|||

1. Kompilátor ověří syntaxi.

V aktuální verzi kompilátor MSVC `<paramref>`nepodporuje značku, která je podporována jinými kompilátory sady Visual Studio. Visual C++ `<paramref>` může podporovat v budoucí verzi.

## <a name="see-also"></a>Viz také

[Dokumentace XML](xml-documentation-visual-cpp.md)
