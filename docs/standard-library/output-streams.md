---
title: Výstupní datové proudy
ms.date: 11/04/2016
helpviewer_keywords:
- output streams
ms.assetid: b49410e3-5caa-4153-9d0d-c4266408dc83
ms.openlocfilehash: e650f9fd0bbc7ad483363706e632686e8ec3749e
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68450172"
---
# <a name="output-streams"></a>Výstupní datové proudy

Výstupní datový proud je cílovým objektem pro bajty. Tři nejdůležitější třídy výstupního datového proudu jsou `ostream`, `ofstream`a `ostringstream`.

Třída prostřednictvím odvozené třídy `basic_ostream`podporuje předdefinované objekty datového proudu: `ostream`

- `cout`standardní výstup

- `cerr`standardní chyba s omezeným ukládáním do vyrovnávací paměti

- `clog``cerr` podobně jako u plného ukládání do vyrovnávací paměti

Objekty jsou zřídka postaveny `ostream`. předdefinované objekty jsou obecně používány. V některých případech můžete znovu přiřadit předdefinované objekty po spuštění programu. `ostream` Třída, která se dá nakonfigurovat pro operaci s vyrovnávací pamětí nebo bez vyrovnávací paměti, je nejvhodnější pro sekvenční výstup v textovém režimu. Všechny funkce základní třídy `ios`jsou obsaženy v. `ostream` Při vytváření objektu třídy `ostream`je nutné `streambuf` zadat objekt do konstruktoru.

`ofstream` Třída podporuje výstup souboru na disku. Pokud potřebujete jenom výstupní disk, vytvořte objekt třídy `ofstream`. Můžete určit, zda `ofstream` objekty při vytváření `ofstream` `open` objektu nebo při volání členské funkce objektu přijímají data binárního nebo textového režimu. Mnoho možností formátování a členských funkcí platí pro `ofstream` objekty a `ostream` je součástí všech funkcí základních tříd `ios` .

Pokud zadáte název souboru v konstruktoru, tento soubor se automaticky otevře, když je objekt vytvořen. V opačném případě můžete použít `open` členskou funkci po vyvolání výchozího konstruktoru.

Podobně jako funkce `sprintf_s` `ostringstream` modulu runtime podporuje třída výstup do řetězců v paměti. Chcete-li vytvořit řetězec v paměti pomocí formátování vstupně-výstupních proudů, vytvořte objekt třídy `ostringstream`.

## <a name="in-this-section"></a>V tomto oddílu

[Vytváření objektů výstupního streamu](../standard-library/constructing-output-stream-objects.md)

[Používání operátorů insertion a řízení formátu](../standard-library/using-insertion-operators-and-controlling-format.md)

[Členské funkce streamu výstupního souboru](../standard-library/output-file-stream-member-functions.md)

[Účinky ukládání do vyrovnávací paměti](../standard-library/effects-of-buffering.md)

[Binární výstupní soubory](../standard-library/binary-output-files.md)

[Přetěžování operátoru << pro vaše vlastní třídy](../standard-library/overloading-the-output-operator-for-your-own-classes.md)

[Psaní vlastních manipulátorů bez argumentů](../standard-library/writing-your-own-manipulators-without-arguments.md)

## <a name="see-also"></a>Viz také:

[ofstream](../standard-library/basic-ofstream-class.md)\
[ostringstream –](../standard-library/basic-ostringstream-class.md)\
[iostream – programování](../standard-library/iostream-programming.md)
