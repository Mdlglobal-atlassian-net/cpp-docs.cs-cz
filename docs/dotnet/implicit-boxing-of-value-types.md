---
title: Implicitní zabalení typů hodnot | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- boxing, Visual C++
- __box keyword
- boxing
- boxing, __box keyword
- value types, boxed
ms.assetid: 9597c92f-a3fe-44af-ad80-f9d656847a35
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: e9c232dba6d766d0855bb4bb29e33d85b5fd5a2d
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387585"
---
# <a name="implicit-boxing-of-value-types"></a>Implicitní zabalení typů hodnot

Zabalení typů hodnot změnil ze spravovaného rozšíření jazyka C++ pro Visual C++.

V návrhu jazyka jsme uložených filozofické pozice namísto praktické zkušenosti s funkcí a v praxi se to stalo omylem. Analogicky v původní více návrhu jazyka dědičnosti, Stroustrup rozhodla, že nebylo možné inicializovat objekt dílčí virtuální základní třídy v konstruktoru odvozené třídy, a proto jazyk zapotřebí všechny třídy, které slouží jako virtuální základ Třída musí definovat výchozí konstruktor. Je to výchozí konstruktor, který by mohly vyvolávat jakékoli následné virtuální odvození.

Problém hierarchie virtuální třídy base je, že odpovědnost za inicializaci sdílený virtuální dílčí objekt posune s každé následné odvození. Například pokud definovat základní třída pro které inicializace vyžaduje přidělení vyrovnávací paměti, velikost vyrovnávací paměti zadané uživatelem mohla být předána jako argument konstruktoru. Když uvedu pak dva další virtuální odvození, jejich volání `inputb` a `outputb`, každá obsahuje určitou hodnotu konstruktoru základní třídy. Teď, když odvodíme `in_out` z obou `inputb` a `outputb`, ani jedno z těchto hodnot sdílené virtuální základní třídy podobjektu podobjektu může být povoleno k vyhodnocení.

Proto v původní návrh jazyka zakázal Stroustrup explicitní inicializace virtuální základní třídy v rámci seznamu inicializace členů konstruktoru odvozené třídy. Přestože byl problém vyřešen, v praxi neschopnost přímá inicializace virtuální základní třídy dokázaly neproveditelné. Keith Gorlen národní Institute stavu, který měl implementovat freeware verzi knihovny kolekce SmallTalk volá nihcl, byla zásada plaformu přesvědčování, který měl na flexibilnější návrh jazyka.

Princip objektově orientované hierarchické návrh obsahuje, že odvozené třídy by se měla zabývat pouze s implementací nesoukromých přímé základní třídy. Aby bylo možné podporovat návrh flexibilní inicializace virtuální dědičnost, Stroustrup museli tuto zásadu. Nejvíce odvozené třídy v hierarchii předpokládá odpovědnost za všechny virtuální podobjektu inicializace bez ohledu na to, jak hluboko do hierarchie, k ní dojde. Například `inputb` a `outputb` jsou odpovědné za explicitní inicializací jejich okamžité virtuální základní třídy. Když `in_out` je odvozena z obou `inputb` a `outputb`, `in_out` zodpovědná za inicializaci jedné odebere virtuální základní třídy a v rámci explicitní inicializace `inputb` a `outputb` je potlačit.

Získáte tak flexibilitu, požadovaná vývojáři jazyka, ale za cenu složité sémantiku. Tato zatížení komplikací se zbavíme, pokud omezíme virtuální základní třídy bez stavu a jednoduše povolit k určení rozhraní. Toto je doporučený návrh idiom v rámci jazyka C++. V CLR programování je vyvolána zásady s typem rozhraní.

Tady je ukázka jednoduché kód – a v takovém případě je zbytečné explicitní zabalení:

```
// Managed Extensions for C++ requires explicit __box operation
int my1DIntArray __gc[] = { 1, 2, 3, 4, 5 };
Object* myObjArray __gc[] = {
   __box(26), __box(27), __box(28), __box(29), __box(30)
};

Console::WriteLine( "{0}\t{1}\t{2}", __box(0),
   __box(my1DIntArray->GetLowerBound(0)),
   __box(my1DIntArray->GetUpperBound(0)) );
```

Jak vidíte, je hodně zabalení děje. V části Visual C++, typ hodnoty zabalení je implicitní:

```
// new syntax makes boxing implicit
array<int>^ my1DIntArray = {1,2,3,4,5};
array<Object^>^ myObjArray = {26,27,28,29,30};

Console::WriteLine( "{0}\t{1}\t{2}", 0,
   my1DIntArray->GetLowerBound( 0 ),
   my1DIntArray->GetUpperBound( 0 ) );
```

## <a name="see-also"></a>Viz také

[Hodnotové typy a jejich chování (C++/CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)<br/>
[Zabalení](../windows/boxing-cpp-component-extensions.md)