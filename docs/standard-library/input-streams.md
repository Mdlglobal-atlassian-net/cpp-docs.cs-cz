---
title: Vstupní datové proudy
ms.date: 11/04/2016
helpviewer_keywords:
- reading data [C++], from input streams
- data [C++], reading from input stream
- input streams
- input stream objects
ms.assetid: f14d8954-8f8c-4c3c-8b99-14ddb3683f94
ms.openlocfilehash: 5dc3fa0af76f73897fe1181d944eb34c8d05bc64
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68449330"
---
# <a name="input-streams"></a>Vstupní datové proudy

Vstupní objekt datového proudu je zdrojem bajtů. Tři nejdůležitější třídy vstupního datového proudu jsou [IStream](../standard-library/basic-istream-class.md), [ifstream](../standard-library/basic-ifstream-class.md)a [istringstream –](../standard-library/basic-istringstream-class.md).

`istream` Třída se nejlépe používá pro sekvenční vstup v textovém režimu. Můžete nakonfigurovat objekty třídy `istream` pro operaci vyrovnávací paměti nebo neuloženou v vyrovnávací paměti. Všechny funkce základní třídy `ios`jsou obsaženy v. `istream` Nebudete pouze vytvářet objekty ze `istream`třídy. Místo toho budete obecně používat předdefinovaný `cin` objekt, který je ve skutečnosti objekt třídy [ostream](../standard-library/basic-ostream-class.md). V některých případech se můžete po spuštění `cin` programu přiřadit k ostatním objektům streamu.

`ifstream` Třída podporuje vstup ze souboru na disku. Pokud potřebujete soubor s pouze vstupním diskem, Sestavte objekt třídy `ifstream`. Můžete zadat binární data nebo data v textovém režimu. Pokud zadáte název souboru v konstruktoru, soubor se automaticky otevře při sestavení objektu. V opačném případě můžete `open` funkci použít po vyvolání výchozího konstruktoru. Mnoho možností formátování a členských funkcí se vztahuje `ifstream` na objekty. Všechny funkce základních tříd `ios` a `istream` jsou součástí `ifstream`.

Podobně jako funkce `sscanf_s` `istringstream` knihovny podporuje třída vstup z řetězců v paměti. Chcete-li extrahovat data z pole znaků, které má ukončovací znak null, přidělte a inicializujte řetězec a poté Sestavte objekt třídy `istringstream`.

## <a name="in-this-section"></a>V tomto oddílu

[Vytváření objektů vstupního streamu](../standard-library/constructing-input-stream-objects.md)

[Používání operátorů extrakce](../standard-library/using-extraction-operators.md)

[Testování pro nalezení chyb extrakce](../standard-library/testing-for-extraction-errors.md)

[Manipulátory vstupního streamu](../standard-library/input-stream-manipulators.md)

[Členské funkce vstupního streamu](../standard-library/input-stream-member-functions.md)

[Přetěžování operátoru >> pro vaše vlastní třídy](../standard-library/overloading-the-input-operator-for-your-own-classes.md)

## <a name="see-also"></a>Viz také:

[iostream – programování](../standard-library/iostream-programming.md)
