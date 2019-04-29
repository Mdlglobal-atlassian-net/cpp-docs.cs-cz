---
title: Vstupní datové proudy
ms.date: 11/04/2016
helpviewer_keywords:
- reading data [C++], from input streams
- data [C++], reading from input stream
- input streams
- input stream objects
ms.assetid: f14d8954-8f8c-4c3c-8b99-14ddb3683f94
ms.openlocfilehash: 0f56f5ffc8e61c0881eddbbd65e1c431b9219674
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404920"
---
# <a name="input-streams"></a>Vstupní datové proudy

Objekt vstupního datového proudu je zdrojem bajtů. Jsou tři třídy nejdůležitější vstupního datového proudu [istream](../standard-library/basic-istream-class.md), [ifstream](../standard-library/basic-ifstream-class.md), a [istringstream](../standard-library/basic-istringstream-class.md).

`istream` Třídy je nejvhodnější pro sekvenční režim textové zadání. Můžete nakonfigurovat objekty třídy `istream` pro operace bez vyrovnávací paměti nebo ve vyrovnávací paměti. Všechny funkce základní třídy `ios`, je součástí `istream`. Se jen zřídka objekty je možné vytvořit z třídy `istream`. Místo toho se obvykle použijete předdefinovanou `cin` objekt, který je ve skutečnosti objekt třídy [ostream](../standard-library/basic-ostream-class.md). V některých případech můžete přiřadit `cin` jiným objektům datového proudu po spuštění programu.

`ifstream` Třída podporuje vstupního souboru disku. Pokud potřebujete použití pouze soubor na disku, sestavte objekt třídy `ifstream`. Můžete zadat režim textové nebo binární data. Pokud zadáte filename v konstruktoru, soubor se automaticky otevře při vytvoření objektu. V opačném případě můžete použít `open` funkce po vyvolání výchozího konstruktoru. Mnoho formátování možnosti a členských funkcí platí pro `ifstream` objekty. Všechny funkce základní třídy `ios` a `istream` je součástí `ifstream`.

Funkce knihovny, jako jsou `sscanf_s`, `istringstream` třída podporuje vstup z řetězců v paměti. Extrahovat data z pole znaků, který má ukončovací znak null, přidělit a inicializuje řetězec a pak vytvořit objekt třídy `istringstream`.

## <a name="in-this-section"></a>V tomto oddílu

[Vytváření objektů vstupního streamu](../standard-library/constructing-input-stream-objects.md)

[Používání operátorů extrakce](../standard-library/using-extraction-operators.md)

[Testování pro nalezení chyb extrakce](../standard-library/testing-for-extraction-errors.md)

[Manipulátory vstupního streamu](../standard-library/input-stream-manipulators.md)

[Členské funkce vstupního streamu](../standard-library/input-stream-member-functions.md)

[Přetěžování operátoru >> pro vaše vlastní třídy](../standard-library/overloading-the-input-operator-for-your-own-classes.md)

## <a name="see-also"></a>Viz také:

[iostream – programování](../standard-library/iostream-programming.md)<br/>
