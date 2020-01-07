---
title: Tokeny a znakové sady
ms.date: 12/10/2019
helpviewer_keywords:
- Tokens (C++)
- Character sets
- basic source character set (C++)
- universal character names
- basic execution character set (C++)
ms.assetid: 379a2af6-6422-425f-8352-ef0bca6c0d74
ms.openlocfilehash: 1f6dbe2faa6348d61ec00b411cc35e8ef5ceb57a
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75301610"
---
# <a name="tokens-and-character-sets"></a>Tokeny a znakové sady

Text C++ programu se skládá z tokenů a mezer *.* Token je nejmenší prvek programu C++, který je smysluplný pro kompilátor. C++ Analyzátor rozpoznává tyto typy tokenů:

- [Klíčová slova](../cpp/keywords-cpp.md)
- [Identifikátory](../cpp/identifiers-cpp.md)
- [Číselné literály, logické a literály typu ukazatele](../cpp/numeric-boolean-and-pointer-literals-cpp.md)
- [Řetězcové a znakové literály](../cpp/string-and-character-literals-cpp.md)
- [Uživateli definované literály](../cpp/user-defined-literals-cpp.md)
- [Operátory](../cpp/cpp-built-in-operators-precedence-and-associativity.md)
- [Interpunkční znaky jazyka](../cpp/punctuators-cpp.md)

Tokeny jsou obvykle odděleny *prázdným znakem*, což může být jedna nebo více:

- Prázdné hodnoty
- Vodorovné nebo svislé tabulátory
- Nové řádky
- Informační kanály formuláře
- Komentáře

## <a name="basic-source-character-set"></a>Základní znaková sada zdroje

C++ Standard Určuje *základní zdrojovou znakovou sadu* , která může být použita ve zdrojových souborech. Pro reprezentaci znaků mimo tuto sadu lze zadat další znaky pomocí *univerzálního názvu znaku*. Implementace MSVC umožňuje další znaky. *Základní Zdrojová znaková sada* se skládá z 96 znaků, které mohou být použity ve zdrojových souborech. Tato sada obsahuje znak mezery, horizontální tabulátor, svislou kartu, kanál formuláře a řídicí znaky nového řádku a tuto sadu grafických znaků:

`a b c d e f g h i j k l m n o p q r s t u v w x y z`

`A B C D E F G H I J K L M N O P Q R S T U V W X Y Z`

`0 1 2 3 4 5 6 7 8 9`

`_ { } [ ] # ( ) < > % : ; . ? * + - / ^ & | ~ ! = , \ " '`

**Specifické pro společnost Microsoft**

MSVC zahrnuje znak `$` jako člen základní zdrojové znakové sady. MSVC také umožňuje použít další sadu znaků ve zdrojových souborech na základě kódování souboru. Ve výchozím nastavení Visual Studio ukládá zdrojové soubory pomocí výchozí znakové stránky. Když jsou zdrojové soubory uloženy pomocí znakové stránky specifické pro národní prostředí nebo znakové stránky Unicode, umožňuje MSVC použít libovolný ze znaků této znakové stránky ve zdrojovém kódu, s výjimkou řídicích kódů, které nejsou explicitně povoleny v základní zdrojové znakové sadě. Můžete například vložit japonské znaky do komentářů, identifikátorů nebo řetězcových literálů, pokud soubor uložíte pomocí japonské znakové stránky. MSVC nepovoluje sekvence znaků, které nelze přeložit na platné vícebajtové znaky nebo body kódu Unicode. V závislosti na možnostech kompilátoru nemusí být v identifikátorech zobrazeny všechny povolené znaky. Další informace najdete v článku [Identifikátory](../cpp/identifiers-cpp.md).

**Specifické pro konec Microsoftu**

### <a name="universal-character-names"></a>Univerzální názvy znaků

Vzhledem C++ k tomu, že programy můžou používat spoustu dalších znaků, než jsou zadané v základní zdrojové znakové sadě, můžete tyto znaky zadat přenositelném způsobem pomocí *názvů univerzálních znaků*. Univerzální název znaku se skládá ze sekvence znaků, které reprezentují bod kódu Unicode.  Ty mají dvě formy. Použijte `\UNNNNNNNN` pro reprezentaci bodu kódu Unicode ve formátu U + NNNNNNNN, kde NNNNNNNN je desítkové číslo bodu kódu v šestnáctkové soustavě. Použijte čtyřmístné `\uNNNN` pro reprezentaci bodu kódu Unicode ve formátu U + 0000NNNN.

Univerzální názvy znaků lze použít v identifikátorech a v řetězcových a znakových literálech. Univerzální název znaku nelze použít k reprezentaci náhradního bodu kódu v rozsahu 0xD800-0xDFFF. Místo toho použijte požadovaný bod kódu; kompilátor automaticky generuje všechny požadované náhrady. Další omezení platí pro názvy univerzálních znaků, které lze použít v identifikátorech. Další informace naleznete v tématu [identifikátory](../cpp/identifiers-cpp.md) a [řetězcové a znakové literály](../cpp/string-and-character-literals-cpp.md).

**Specifické pro společnost Microsoft**

Kompilátor společnosti C++ Microsoft považuje znak ve formě univerzálního znakového názvu a tvar literálu se zamění. Můžete například deklarovat identifikátor pomocí formuláře univerzálního názvu znaku a použít ho ve formě literálu:

```cpp
auto \u30AD = 42; // \u30AD is 'キ'
if (キ == 42) return true; // \u30AD and キ are the same to the compiler
```

Formát rozšířených znaků ve schránce systému Windows je specifický pro nastavení národního prostředí aplikace. Vyjmutí a vložení těchto znaků do kódu z jiné aplikace může vést k neočekávaným kódováním znaků. To může vést k analýze chyb bez viditelné příčiny v kódu. Před vložením rozšířených znaků doporučujeme, abyste nastavili kódování zdrojového souboru na znakovou stránku Unicode. Doporučujeme také použít editor IME nebo aplikaci Mapa znaků k vygenerování rozšířených znaků.

**Specifické pro konec Microsoftu**

### <a name="execution-character-sets"></a>Spouštěcí znakové sady

*Znakové sady spuštění* reprezentují znaky a řetězce, které se mohou objevit v kompilovaném programu. Tyto znakové sady se skládají ze všech znaků povolených ve zdrojovém souboru a také řídicích znaků, které reprezentují výstrahy, Backspace, CR a znak null. Znaková sada spuštění má reprezentaci specifickou pro národní prostředí.
