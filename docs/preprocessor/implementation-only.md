---
title: importovat atribut implementation_only
ms.date: 08/29/2019
f1_keywords:
- implementation_only
helpviewer_keywords:
- implementation_only attribute
ms.assetid: d8cabc86-4425-45a0-9587-d57536980088
ms.openlocfilehash: 08144b3c815350acfe6a856b36d2d88085d1c04d
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218983"
---
# <a name="implementation_only-import-attribute"></a>importovat atribut implementation_only

**C++Konkrétní**

Potlačí generování `.tlh` primárního souboru hlaviček knihovny typů.

## <a name="syntax"></a>Syntaxe

> **#import** *typ – Knihovna* **implementation_only**

## <a name="remarks"></a>Poznámky

Tento soubor obsahuje všechny deklarace, které slouží k vystavení obsahu knihovny typů. `.tli` Hlavičkový soubor s implementacemi členských funkcí obálky se vygeneruje a zahrne do kompilace.

Při zadání tohoto atributu je obsah `.tli` záhlaví ve stejném oboru názvů jako ten, který se běžně používá `.tlh` v hlavičce. Kromě toho členské funkce nejsou deklarovány jako inline.

Atribut **implementation_only** je určen pro použití ve spojení s atributem [no_implementation](../preprocessor/no-implementation.md) jako způsob zachování implementace z souboru předkompilované hlavičky (PCH). `#import` Příkaz`no_implementation` s atributem je umístěn ve zdrojové oblasti použité k vytvoření souboru PCH. Výsledný soubor PCH používá několik zdrojových souborů. Příkaz s atributem implementation_only se pak použije vně oblasti PCH. `#import` Tento příkaz je nutné použít pouze jednou v jednom ze zdrojových souborů. Generuje všechny požadované členské funkce obálky bez další nové kompilace pro každý zdrojový soubor.

> [!NOTE]
> Atribut **implementation_only** v jednom `#import` příkazu musí být použit ve spojení s jiným `#import` příkazem stejné knihovny typů s `no_implementation` atributem. V opačném případě jsou generovány chyby kompilátoru. Důvodem je, že definice obálkové třídy vygenerované `#import` příkazem `no_implementation` s atributem jsou požadovány pro zkompilování implementací generovaných atributem **implementation_only** .

**Specifické C++ pro konec**

## <a name="see-also"></a>Viz také:

[Atributy #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import direktiva](../preprocessor/hash-import-directive-cpp.md)
