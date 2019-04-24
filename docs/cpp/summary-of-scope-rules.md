---
title: Souhrn pravidel rozsahu
ms.date: 11/04/2016
helpviewer_keywords:
- class scope [C++], rules
- classes [C++], scope
- class names [C++], scope rules
- names [C++], class
- scope [C++], class names
ms.assetid: 47e26482-0111-466f-b857-598c15d05105
ms.openlocfilehash: af708fd72904fb775ff1088948972bec159816c6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62266904"
---
# <a name="summary-of-scope-rules"></a>Souhrn pravidel rozsahu

Použití názvu musí být v daném oboru jednoznačné (až do místa, kde je určeno přetížení). Pokud název označuje funkci, musí být funkce jednoznačná vzhledem k počtu a typu parametrů. Pokud název zůstává jednoznačným, [přístup ke členu](../cpp/member-access-control-cpp.md) pravidla se použijí.

## <a name="constructor-initializers"></a>Inicializátory konstruktoru

[Inicializátory konstruktoru](constructors-cpp.md#member_init_list) jsou vyhodnoceny v rozsahu vnějšího bloku konstruktoru, pro které jsou určeny. Proto může používat názvy parametrů konstruktoru.

## <a name="global-names"></a>Globální názvy

Název objektu, funkce nebo enumerátoru je globální, pokud je zaveden mimo jakoukoli funkci nebo třídu nebo je umístěn za předponu globálního unárního operátoru oboru (`::`) a není-li použit ve spojení s některým z těchto binárních operátorů:

- Rozlišení oboru (`::`)

- Výběr členů objektů a odkazů (**.**)

- Výběr členů ukazatelů (**->**)

## <a name="qualified-names"></a>Kvalifikované názvy

Názvy použité s binárním operátorem rozlišení oboru (`::`) jsou označovány jako „kvalifikované názvy“. Název zadaný po binárním operátoru rozlišení oboru musí být členem třídy uvedené na levé straně operátoru nebo členem její základní třídy.

Názvy zadané po operátoru výběru členů (**.** nebo **->**) musí být členy typu třídy objektu uvedeného na levé straně operátoru nebo členy její základní třídy. Názvy zadané na pravé straně operátoru výběru členů (**->**) mohou být také objekty jiného typu třídy, za předpokladu, že levá strana příkazu **->** je objekt třídy a třídy definující operátora přetíženého výběru členů (**->**), který je vyhodnocen jako ukazatel na jiný typ třídy. (Toto ustanovení je podrobněji popsána podrobněji [přístup ke členům třídy](../cpp/member-access.md).)

Kompilátor vyhledá názvy v následujícím pořadí a toto hledání zastaví, když je název nalezen:

1. Rozsah aktuálního bloku, pokud je název použit uvnitř funkce, v opačném případě globální rozsah.

1. Směrem ven přes každý nadřazený blok rozsahu včetně rozsahu vnější funkce (která zahrnuje parametry funkce).

1. Pokud je název použit uvnitř členské funkce, je název vyhledán v rozsahu třídy.

1. Název je vyhledán v základních třídách této třídy.

1. Je prohledán nadřazený rozsah vnořené třídy (pokud existuje) a její základní třídy. Hledání pokračuje, dokud není prohledán vnější nadřazený rozsah třídy.

1. Je prohledán globální rozsah.

Avšak toto pořadí hledání lze upravit následujícím způsobem:

1. Názvy začínající `::` vynutí, aby hledání začalo v globálním rozsahu.

1. Názvy začínající **třídy**, **struktura**, a **sjednocení** klíčová slova vynutí, aby kompilátor prohledával pouze **třídy**,  **Struktura**, nebo **sjednocení** názvy.

1. Názvy na levé straně operátoru rozlišení oboru (`::`) může být pouze **třídy**, **struktura**, **obor názvů**, nebo **sjednocení**názvy.

Pokud název odkazuje na nestatický člen, ale je použit ve statické členské funkci, je vygenerována chybová zpráva. Podobně, pokud se název vztahuje k jakémukoli nestatickému členu v nadřazené třídě, chybová zpráva je generována, protože vnořené třídy nemají nadřazené třídu **to** ukazatele.

## <a name="function-parameter-names"></a>Názvy parametrů – funkce

Názvy parametrů funkce v definicích funkce jsou považovány za v rozsahu vnějšího bloku funkce. Proto jsou místními názvy a dostanou se mimo rozsah, když funkce skončí.

Názvy parametrů funkce v deklaracích funkce (prototypy) jsou v místním rozsahu deklarace a dostanou se mimo rozsah na konci této deklarace.

Výchozí parametry jsou v oboru parametr, pro který jsou výchozí, jak je popsáno v předchozích dvou odstavcích. Avšak nemají přístup k lokálním proměnným nebo nestatickým členům třídy. Výchozí parametry jsou vyhodnoceny v okamžiku volání funkce, ale jsou vyhodnocovány v původním rozsahu deklarace funkce. Proto výchozí parametry pro členské funkce jsou vždy vyhodnoceny v oboru třídy.

## <a name="see-also"></a>Viz také:

[Dědičnost](../cpp/inheritance-cpp.md)