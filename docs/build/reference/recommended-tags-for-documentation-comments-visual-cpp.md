---
title: Doporučené značky pro dokumentační komentáře (C++ dokumentačních komentářů)
ms.date: 11/04/2016
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
ms.openlocfilehash: adb8440dc07f8f3e193b58be6782859fbb8413e4
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57823127"
---
# <a name="recommended-tags-for-documentation-comments"></a>Doporučené značky pro komentáře dokumentace

Kompilátor MSVC zpracuje komentáře dokumentace ve vašem kódu a vytvoří soubor .xdc pro každý kompilace a xdcmake.exe zpracuje souborech .xdc do souboru .xml. Zpracování souboru XML pro vytvoření dokumentace je podrobností, které je potřeba implementovat ve vaší lokalitě.

Značky se zpracovávají na konstrukce, jako jsou typy a členy typu.

Značky musí bezprostředně předcházet typy nebo členy.

> [!NOTE]
>  Dokumentační komentáře nelze použít na obor názvů nebo na mimo definici řádek pro vlastnosti a události; komentáře dokumentace musí v deklaracích ve své třídě.

Kompilátor bude zpracovávat všechny značky, který je platný kód XML. Následující značky poskytuje běžně používané funkce v dokumentaci pro uživatele:

||||
|-|-|-|
|[\<c>](c-visual-cpp.md)|[\<code>](code-visual-cpp.md)|[\<example>](example-visual-cpp.md)|
|[\<exception>](exception-visual-cpp.md)1|[\<include>](include-visual-cpp.md)1|[\<list>](list-visual-cpp.md)|
|[\<para>](para-visual-cpp.md)|[\<Param >](param-visual-cpp.md)1|[\<paramref>](paramref-visual-cpp.md)1|
|[\<permission>](permission-visual-cpp.md)1|[\<remarks>](remarks-visual-cpp.md)|[\<returns>](returns-visual-cpp.md)|
|[\<see>](see-visual-cpp.md)1|[\<seealso>](seealso-visual-cpp.md)1|[\<summary>](summary-visual-cpp.md)|
|[\<value>](value-visual-cpp.md)|||

1. Kompilátor ověří syntaxi.

V aktuální verzi se nepodporuje a kompilátorem MSVC `<paramref>`, značky, který podporuje dalších kompilátorů aplikace Visual Studio. Visual C++ může podporovat `<paramref>` v budoucí verzi.

## <a name="see-also"></a>Viz také

[Dokumentace XML](xml-documentation-visual-cpp.md)