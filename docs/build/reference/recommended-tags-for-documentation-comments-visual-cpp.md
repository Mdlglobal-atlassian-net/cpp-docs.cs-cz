---
title: Doporučené značky pro dokumentační komentáře (C++ dokumentační komentáře)
ms.date: 11/04/2016
ms.assetid: 6548e798-5235-4a38-9482-bdc7b88f40a9
ms.openlocfilehash: 4e0937b79012f65ba136e18ac81f014be23688f8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80168860"
---
# <a name="recommended-tags-for-documentation-comments"></a>Doporučené značky pro komentáře dokumentace

Kompilátor MSVC zpracuje dokumentační komentáře ve vašem kódu a vytvoří soubor. xdc pro každý kompilantu a xdcmake. exe zpracuje soubory. xdc do souboru. XML. Zpracování souboru. XML pro vytvoření dokumentace je podrobnosti, které je třeba implementovat na vašem webu.

Značky jsou zpracovávány na konstrukcích, jako jsou typy a členy typu.

Značky musí bezprostředně předcházet typům nebo členům.

> [!NOTE]
>  Komentáře k dokumentaci nelze použít pro obor názvů nebo na definici mimo řádek pro vlastnosti a události; dokumentační komentáře musí splňovat deklarace v rámci třídy.

Kompilátor zpracuje všechny značky, které jsou platné XML. Následující značky poskytují běžně používané funkce v dokumentaci uživatele:

||||
|-|-|-|
|[\<c >](c-visual-cpp.md)|[kód \<>](code-visual-cpp.md)|[\<příklad >](example-visual-cpp.md)|
|[výjimka\<>](exception-visual-cpp.md)1|[\<zahrnout >](include-visual-cpp.md)1|[seznam \<>](list-visual-cpp.md)|
|[\<para >](para-visual-cpp.md)|[\<param >](param-visual-cpp.md)1|[\<paramref >](paramref-visual-cpp.md)1|
|[\<oprávnění >](permission-visual-cpp.md)1|[\<poznámky >](remarks-visual-cpp.md)|[\<returns>](returns-visual-cpp.md)|
|[\<zobrazit >](see-visual-cpp.md)1|[\<seealso >](seealso-visual-cpp.md)1|[\<summary>](summary-visual-cpp.md)|
|[\<value>](value-visual-cpp.md)|||

1. Kompilátor ověřuje syntaxi.

V aktuální verzi kompilátor MSVC nepodporuje `<paramref>`, značku, která je podporována jinými kompilátory sady Visual Studio. Vizuál C++ může v budoucí verzi podporovat `<paramref>`.

## <a name="see-also"></a>Viz také

[Dokumentace XML](xml-documentation-visual-cpp.md)
