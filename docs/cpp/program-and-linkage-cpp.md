---
title: Programy a propojení (C++) | Microsoft Docs
ms.custom: ''
ms.date: 04/09/2018
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
ms.assetid: a6493ba0-24e2-4c89-956e-9da1dea660cb
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 2dba8698461636e292771fc1e5a4f5ac0a633e73
ms.sourcegitcommit: d06966efce25c0e66286c8047726ffe743ea6be0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/19/2018
ms.locfileid: "36238666"
---
# <a name="program-and-linkage-c"></a>Program a propojení (C++)

V programu C++ *symbol*, například název proměnné nebo funkce, lze deklarovat všechny počet v rámci svého oboru, ale je možné definovat pouze jednou. Toto je jedna definice pravidla (ODR). A *deklarace* zavádí (nebo znovu zavádí) název do programu. A *definice* představuje název a v případě proměnnou, explicitně inicializaci. A *funkce definice* se skládá z podpis plus tělo funkce.

Jedná se o deklarace:

```cpp
int i;
int f(int x);
```

Toto jsou definice:

```cpp
int i{42};
int f(int x){ return x * i; }
```

Program se skládá z jednoho nebo více *jednotky překladu*. Jednotky překladu se skládá z soubor implementace (sada, .cxx atd.) a všechny hlavičky (.h, .hpp atd.), které obsahuje přímo nebo nepřímo. Jednotlivé jednotky překladu kompiluje nezávisle kompilátorem, po jejímž uplynutí linkeru sloučí jednotky kompilované překladu do jednoho *programu*. Porušení pravidel ODR obvykle zobrazují jako chybami linkeru Pokud stejný název má dva různé definice v různých překlad jednotkách.

Obecně platí, je nejlepší způsob, jak zviditelnit proměnné napříč více souborů uvést v záhlaví souboru a přidat #include – direktiva v každém sada souboru, který vyžaduje deklaraci. Přidáním *zahrnují chrání* kolem hlavičky obsahu, zajistíte, že názvy deklaruje jsou definována pouze jednou.

Ale v některých případech se může být nutné deklarovat – globální proměnná nebo třída v souboru sada. V takových případech musíte určit kompilátoru a linkeru, zda název objektu vztahuje jenom na jeden soubor, nebo všechny soubory.

## <a name="linkage-vs-scope"></a>Propojení oproti oboru

Koncept *propojení* vztahuje se k viditelnost globální symboly (například, názvy typů názvy proměnných a funkce) v rámci programu jako celek jednotky překladu. Koncept *oboru* odkazuje na symboly, které jsou deklarované v rámci bloku například obor názvů, třídu nebo tělo funkce. Tyto symboly jsou viditelné pouze v rámci oboru, ve kterém jsou definovány; Koncept propojení se nevztahuje na ně. 

## <a name="external-vs-internal-linkage"></a>Externí oproti vnitřní propojení

A *bez funkce* je funkce, která je definována v globální nebo oboru názvů. Globální proměnné non-const a bezplatné funkce ve výchozím nastavení mají *externí propojení*; jsou viditelné z jakékoli jednotky překladu v programu. Proto žádné jiné global – objekt (proměnné, definice třídy atd.) může mít tento název. Symbol s *vnitřní propojení* nebo *bez propojení* je viditelná pouze v rámci překladu jednotku, ve kterém je deklarovaná. Pokud název vnitřní propojení, pravděpodobně se stejným názvem existuje v jiné jednotce překlad. Proměnné deklarovány s definice třídy nebo funkce těla mít bez propojení. 

Můžete vynutit globální name má vnitřní propojení deklarováním explicitně jej jako **statické**. Toto nastavení omezuje jeho viditelnost na stejné překlad jednotku, ve kterém je deklarovaná. Všimněte si, že se v tomto kontextu **statické** znamená něco jiného než při použitá pro místní proměnné.

Následující objekty mají vnitřní propojení ve výchozím nastavení:
- Const objekty
- objektů constexpr
- definice Typedef
- statické objekty v oboru názvů

Umožnit const externí propojení objektu deklarujte ji jako **extern** a přiřaďte ho hodnotu:

```cpp
extern const int value = 42;
```

V tématu [extern](extern-cpp.md) Další informace.

## <a name="see-also"></a>Viz také

 [Základní koncepty](../cpp/basic-concepts-cpp.md)