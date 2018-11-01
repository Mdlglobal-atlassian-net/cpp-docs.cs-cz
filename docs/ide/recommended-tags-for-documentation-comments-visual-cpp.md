---
title: Doporučené značky pro dokumentační komentáře (Visual C++)
ms.date: 11/04/2016
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
ms.openlocfilehash: 251baedbf37901a58b34b66b7a10bbdcf5d66557
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50564187"
---
# <a name="recommended-tags-for-documentation-comments-visual-c"></a>Doporučené značky pro dokumentační komentáře (Visual C++)

Kompilátor Visual C++ zpracuje komentáře dokumentace ve vašem kódu a vytvoří soubor .xdc pro každý kompilace a xdcmake.exe zpracuje souborech .xdc do souboru .xml. Zpracování souboru XML pro vytvoření dokumentace je podrobností, které je potřeba implementovat ve vaší lokalitě.

Značky se zpracovávají na konstrukce, jako jsou typy a členy typu.

Značky musí bezprostředně předcházet typy nebo členy.

> [!NOTE]
>  Dokumentační komentáře nelze použít na obor názvů nebo na mimo definici řádek pro vlastnosti a události; komentáře dokumentace musí v deklaracích ve své třídě.

Kompilátor bude zpracovávat všechny značky, který je platný kód XML. Následující značky poskytuje běžně používané funkce v dokumentaci pro uživatele:

||||
|-|-|-|
|[\<c >](../ide/c-visual-cpp.md)|[\<kód >](../ide/code-visual-cpp.md)|[\<Příklad >](../ide/example-visual-cpp.md)|
|[\<Výjimka >](../ide/exception-visual-cpp.md)1|[\<Zahrnout >](../ide/include-visual-cpp.md)1|[\<Seznam >](../ide/list-visual-cpp.md)|
|[\<para >](../ide/para-visual-cpp.md)|[\<Param >](../ide/param-visual-cpp.md)1|[\<paramref >](../ide/paramref-visual-cpp.md)1|
|[\<oprávnění >](../ide/permission-visual-cpp.md)1|[\<REMARKS >](../ide/remarks-visual-cpp.md)|[\<Vrátí >](../ide/returns-visual-cpp.md)|
|[\<Zobrazit >](../ide/see-visual-cpp.md)1|[\<SeeAlso >](../ide/seealso-visual-cpp.md)1|[\<Summary >](../ide/summary-visual-cpp.md)|
|[\<Hodnota >](../ide/value-visual-cpp.md)|||

1. Kompilátor ověří syntaxi.

V aktuální verzi, kompilátor Visual C++ nepodporuje `<paramref>`, značky, který podporuje dalších kompilátorů aplikace Visual Studio. Visual C++ může podporovat `<paramref>` v budoucí verzi.

## <a name="see-also"></a>Viz také

[Dokumentace XML](../ide/xml-documentation-visual-cpp.md)