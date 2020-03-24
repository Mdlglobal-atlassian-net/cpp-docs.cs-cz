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
ms.openlocfilehash: 1f8b79c637662d79051b72e6aabefc99c450bdc5
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80160876"
---
# <a name="summary-of-scope-rules"></a>Souhrn pravidel rozsahu

Použití názvu musí být v daném oboru jednoznačné (až do místa, kde je určeno přetížení). Pokud název označuje funkci, funkce musí být jednoznačná s ohledem na počet a typ parametrů. Pokud název zůstává nejednoznačný, používají se pravidla [přístupu členů](../cpp/member-access-control-cpp.md) .

## <a name="constructor-initializers"></a>Inicializátory konstruktoru

[Inicializátory konstruktoru](constructors-cpp.md#member_init_list) jsou vyhodnocovány v rozsahu vnějšího bloku konstruktoru, pro který jsou určeny. Proto mohou použít názvy parametrů konstruktoru.

## <a name="global-names"></a>Globální názvy

Název objektu, funkce nebo enumerátoru je globální, pokud je zaveden mimo jakoukoli funkci nebo třídu nebo je umístěn za předponu globálního unárního operátoru oboru (`::`) a není-li použit ve spojení s některým z těchto binárních operátorů:

- Rozlišení oboru (`::`)

- Výběr členů pro objekty a odkazy ( **.** )

- Výběr členů pro ukazatele ( **->** )

## <a name="qualified-names"></a>Kvalifikované názvy

Názvy použité s binárním operátorem rozlišení oboru (`::`) jsou označovány jako „kvalifikované názvy“. Název zadaný po binárním operátoru rozlišení oboru musí být členem třídy uvedené na levé straně operátoru nebo členem její základní třídy.

Názvy zadané po operátoru výběru členů ( **.** nebo **->** ) musí být členy typu třídy objektu zadaného na levé straně operátoru nebo členy své základní třídy (ES). Názvy zadané na pravé straně operátoru výběru členů ( **->** ) mohou být také objekty jiného typu třídy za předpokladu, že levá strana **->** je objekt třídy a že třída definuje přetížený operátor výběru členů ( **->** ), který je vyhodnocen jako ukazatel na jiný typ třídy. (Toto ustanovení je podrobněji popsáno v tématu [přístup ke členům třídy](../cpp/member-access.md).)

Kompilátor vyhledá názvy v následujícím pořadí a toto hledání zastaví, když je název nalezen:

1. Rozsah aktuálního bloku, pokud je název použit uvnitř funkce, v opačném případě globální rozsah.

1. Ven přes každý rozsah ohraničujícího bloku, včetně vnějšího oboru funkce (včetně parametrů funkce).

1. Pokud je název použit uvnitř členské funkce, je název vyhledán v rozsahu třídy.

1. Název je vyhledán v základních třídách této třídy.

1. Je prohledán nadřazený rozsah vnořené třídy (pokud existuje) a její základní třídy. Hledání pokračuje, dokud není prohledán vnější nadřazený rozsah třídy.

1. Je prohledán globální rozsah.

Avšak toto pořadí hledání lze upravit následujícím způsobem:

1. Názvy začínající `::` vynutí, aby hledání začalo v globálním rozsahu.

1. Názvy předcházejí klíčová slova **Třída**, **Struktura**a **sjednocení** vynutí, aby kompilátor hledal pouze názvy **tříd**, **struktur**nebo **sjednocení** .

1. Názvy na levé straně operátoru rozlišení oboru (`::`) mohou být pouze názvy **třídy**, **struktury**, **oboru názvů**nebo **sjednocení** .

Pokud název odkazuje na nestatický člen, ale je použit ve statické členské funkci, je vygenerována chybová zpráva. Podobně platí, že pokud název odkazuje na nestatického člena v nadřazené třídě, je vygenerována chybová zpráva, protože uzavřené třídy nemají **tyto** ukazatele nadřazené třídě.

## <a name="function-parameter-names"></a>Názvy parametrů funkce

Názvy parametrů funkce v definicích funkce jsou považovány za v rozsahu vnějšího bloku funkce. Proto jsou místními názvy a dostanou se mimo rozsah, když funkce skončí.

Názvy parametrů funkcí v deklaracích funkcí (prototypy) jsou v místním oboru deklarace a na konci deklarace se přejdou mimo rozsah.

Výchozí parametry jsou v oboru parametru, pro který jsou výchozí, jak je popsáno v předchozích dvou odstavcích. Avšak nemají přístup k lokálním proměnným nebo nestatickým členům třídy. Výchozí parametry jsou vyhodnocovány v místě volání funkce, ale jsou vyhodnocovány v původním rozsahu deklarace funkce. Proto jsou výchozí parametry pro členské funkce vždy vyhodnocovány v oboru třídy.

## <a name="see-also"></a>Viz také

[Dědičnost](../cpp/inheritance-cpp.md)
