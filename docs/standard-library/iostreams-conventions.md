---
title: iostreams – konvence
ms.date: 11/04/2016
helpviewer_keywords:
- iostream header
- C++ Standard Library, iostreams
ms.assetid: 9fe5ded0-37a1-48d1-9671-c81ffc4760ad
ms.openlocfilehash: 222a65f60b231ba4b3768131c15d6e0d736f211e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449016"
---
# <a name="iostreams-conventions"></a>iostreams – konvence

Hlavičky iostreams podporují převody mezi textem a kódovanými formuláři a vstupem a výstupem do externích souborů:

|||
|-|-|
|[\<fstream – >](../standard-library/fstream.md)|[\<iomanip>](../standard-library/iomanip.md)|
|[\<ios>](../standard-library/ios.md)|[\<iosfwd>](../standard-library/iosfwd.md)|
|[\<iostream – >](../standard-library/iostream.md)|[\<IStream >](../standard-library/istream.md)|
|[\<ostream >](../standard-library/ostream.md)|[\<sstream>](../standard-library/sstream.md)|
|[\<streambuf>](../standard-library/streambuf.md)|[\<strstream >](../standard-library/strstream.md)|

Nejjednodušší použití iostreams vyžaduje pouze, abyste zahrnuli hlavičku [ \<iostream – >](../standard-library/iostream.md). Pak můžete extrahovat hodnoty z [CIN](../standard-library/iostream.md#cin) nebo [wcin](../standard-library/iostream.md#wcin) , abyste si přečetli standardní vstup. Pravidla pro tyto účely jsou popsána v popisu [třídy basic_istream](../standard-library/basic-istream-class.md)třídy. Můžete také vložit hodnoty do [cout](../standard-library/iostream.md#cout) nebo [wcout](../standard-library/iostream.md#wcout) a zapsat standardní výstup. Pravidla pro tyto účely jsou popsána v popisu [třídy basic_ostream](../standard-library/basic-ostream-class.md)třídy. Ovládací prvek formátu společný pro extraktory i pro seřazení je spravován třídou [basic_ios](../standard-library/basic-ios-class.md)třídy. Manipulace s těmito informacemi o formátu v GUI pro extrakci a vkládání objektů je provincie několika manipulací.

Stejné operace iostreams můžete provádět u souborů, které otevřete podle názvu, pomocí tříd deklarovaných v [ \<fstream – >](../standard-library/fstream.md). Chcete-li převést mezi iostreams a objekty [třídy basic_string](../standard-library/basic-string-class.md)třídy, použijte třídy deklarované v [ \<sstream >](../standard-library/sstream.md). Chcete-li provést totéž s řetězci jazyka C, použijte třídy deklarované v [ \<strstream >](../standard-library/strstream.md).

Zbývající hlavičky poskytují služby podpory, obvykle přímý zájem pouze na ty zkušené uživatele třídy iostreams.

## <a name="see-also"></a>Viz také:

[C++Přehled standardní knihovny](../standard-library/cpp-standard-library-overview.md)\
[Programování iostream –](../standard-library/iostream-programming.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
