---
title: iostreams – konvence
ms.date: 11/04/2016
helpviewer_keywords:
- iostream header
- C++ Standard Library, iostreams
ms.assetid: 9fe5ded0-37a1-48d1-9671-c81ffc4760ad
ms.openlocfilehash: 52cdd06385994e49ff793e40318ca4cbbbcfcda0
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404829"
---
# <a name="iostreams-conventions"></a>iostreams – konvence

Záhlaví iostreams podporuje převody mezi textem a kódovaného formulářů a vstup a výstup na externí soubory:

|||
|-|-|
|[\<fstream – >](../standard-library/fstream.md)|[\<iomanip>](../standard-library/iomanip.md)|
|[\<ios>](../standard-library/ios.md)|[\<iosfwd>](../standard-library/iosfwd.md)|
|[\<iostream>](../standard-library/iostream.md)|[\<istream>](../standard-library/istream.md)|
|[\<ostream >](../standard-library/ostream.md)|[\<sstream>](../standard-library/sstream.md)|
|[\<streambuf>](../standard-library/streambuf.md)|[\<strstream>](../standard-library/strstream.md)|

Nejjednodušší použití iostreams vyžaduje pouze, že složku zahrnujete záhlaví [ \<iostream – >](../standard-library/iostream.md). Potom můžete extrahovat hodnoty ze [cin](../standard-library/iostream.md#cin) nebo [wcin](../standard-library/iostream.md#wcin) přečíst standardní vstup. Pravidla pro to uděláte tak jsou uvedeny v popisu třídy [basic_istream – třída](../standard-library/basic-istream-class.md). Můžete také vložit hodnoty [cout](../standard-library/iostream.md#cout) nebo [wcout](../standard-library/iostream.md#wcout) k zápisu ve standardním výstupu. Pravidla pro to uděláte tak jsou uvedeny v popisu třídy [basic_ostream – třída](../standard-library/basic-ostream-class.md). Formát ovládacího prvku společné pro extraktory a insertors spravuje třída [basic_ios – třída](../standard-library/basic-ios-class.md). Manipulace se tyto informace formát guise extrahování a vkládání objektů je provincie několik manipulátory.

Abyste mohli provádět stejné operace iostreams u souborů, které se otevřou podle názvu, pomocí třídy deklarované v [ \<fstream – >](../standard-library/fstream.md). K převodu mezi iostreams a objekty třídy [basic_string – třída](../standard-library/basic-string-class.md), použijte třídy deklarované v [ \<sstream >](../standard-library/sstream.md). Stejný postup provést s řetězci jazyka C, použijte třídy deklarované v [ \<strstream – >](../standard-library/strstream.md).

Záhlaví zbývající poskytovat služby podpory, obvykle s přímým přístupem zájmu nejpokročilejší uživatelům třídami iostreams.

## <a name="see-also"></a>Viz také:

[Standardní knihovna C++ – přehled](../standard-library/cpp-standard-library-overview.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
