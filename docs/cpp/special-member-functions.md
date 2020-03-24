---
title: Zvláštní členské funkce
ms.date: 12/06/2016
helpviewer_keywords:
- special member functions [C++]
- constructors [C++]
- destructors [C++]
- copy operators [C++]
- move operators [C++]
- assignment operators [C++]
ms.assetid: 017d6817-b012-44f0-b153-f3076c251ea7
ms.openlocfilehash: b15a0e50774bbc4e70912a31f9a57ea0439f2c12
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80178688"
---
# <a name="special-member-functions"></a>Zvláštní členské funkce

*Zvláštní členské funkce* jsou členské funkce třídy (nebo struktury), které v některých případech kompilátor automaticky generuje za vás. Tyto funkce jsou [výchozí konstruktor](constructors-cpp.md#default_constructors), [destruktor](destructors-cpp.md), [kopírovací konstruktor a operátor přiřazení kopie](copy-constructors-and-copy-assignment-operators-cpp.md)a [konstruktor Move a operátor přiřazení přesunutí](move-constructors-and-move-assignment-operators-cpp.md). Pokud vaše třída nedefinuje jednu nebo více speciálních členských funkcí, kompilátor může implicitně deklarovat a definovat používané funkce. Implementace generované kompilátorem se nazývají *výchozí* speciální členské funkce. Kompilátor negeneruje funkce, pokud nejsou potřeba.

Výchozí speciální členskou funkci můžete explicitně deklarovat pomocí klíčového slova **= Default** . To způsobí, že kompilátor definuje funkci pouze v případě potřeby, stejným způsobem jako, pokud nebyla funkce deklarována vůbec.

V některých případech může kompilátor generovat *odstraněné* speciální členské funkce, které nejsou definovány, a proto nelze volat. K tomu může dojít v případech, kdy volání konkrétní zvláštní členské funkce na třídu nemá smysl, s ohledem na jiné vlastnosti třídy. Chcete-li explicitně zabránit automatické generaci speciální členské funkce, můžete ji deklarovat jako odstraněnou pomocí klíčového slova **= Delete** .

Kompilátor generuje *výchozí konstruktor*, který nepřijímá žádné argumenty, pouze v případě, že jste nedeklarovali žádný jiný konstruktor. Pokud jste deklarovali pouze konstruktor, který přebírá parametry, kód, který se pokusí volat výchozí konstruktor, způsobí, že kompilátor vytvoří chybovou zprávu. Výchozí konstruktor generovaný kompilátorem provádí jednoduchou [výchozí inicializaci](initializers.md#default_initialization) objektu. Výchozí inicializace opustí všechny členské proměnné v neurčitém stavu.

Výchozí destruktor provádí likvidaci objektu. Je virtuální pouze v případě, že je destruktor základní třídy virtuální.

Výchozí operace kopírování a přesunutí a operace přiřazení provádějí kopie bitových vzorů, které jsou k dispozici, a přesouvá nestatické datové členy. Operace přesunu jsou generovány pouze v případě, že nejsou deklarovány žádné operace destruktoru nebo přesunutí nebo kopírování. Výchozí kopírovací konstruktor je vygenerován pouze v případě, že není deklarován žádný kopírovací konstruktor. Implicitně se odstraní, pokud je deklarována operace přesunutí. Výchozí operátor přiřazení kopie je vygenerován pouze v případě, že není explicitně deklarován žádný operátor přiřazení kopie. Implicitně se odstraní, pokud je deklarována operace přesunutí.

## <a name="see-also"></a>Viz také

[Referenční dokumentace jazyka C++](cpp-language-reference.md)
