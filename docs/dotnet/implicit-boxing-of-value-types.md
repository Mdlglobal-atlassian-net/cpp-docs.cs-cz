---
title: Implicitní zabalení typů hodnot | Microsoft Docs
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
ms.openlocfilehash: f1f5a455333e5cb40b63d5a5237b2df053cef194
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33132216"
---
# <a name="implicit-boxing-of-value-types"></a>Implicitní zabalení typů hodnot
Zabalení typů hodnot změnil ze spravovaných rozšíření jazyka C++ na Visual C++.  
  
 V návrhu jazyka jsme vynucená filozofické pozici namísto praktických zkušeností s funkcí a v praxi, byla chyba. Jako analogie v původním více návrhu dědičnosti jazyka, Stroustrup rozhodl nebylo možné inicializovat objekt dílčí virtuální třídy base v konstruktoru odvozené třídy, a proto jazyk vyžaduje který jakákoli třída slouží jako virtuální základní Třída musí definovat výchozí konstruktor. Je to výchozí konstruktor, který bude vyvolán jakékoli následné virtuální odvození.  
  
 Problém hierarchie virtuální třídy base je, že odpovědnost za inicializaci objektu sdílené virtuální dílčí posune s každým následným odvozením. Například pokud definujeme základní třídu, pro kterou vyžaduje inicializace přidělení vyrovnávací paměti, uživatelem zadanou velikost vyrovnávací paměti mohla být předána jako argument konstruktoru. Pokud I pak zadejte dvě sobě jdoucí virtuální odvození, zavoláme `inputb` a `outputb`, každý obsahuje konkrétní hodnotu do konstruktoru základní třídy. Nyní v při I odvozené `in_out` třídy z obou `inputb` a `outputb`, ani jeden z těchto hodnot ze sdílené virtuální třídy base dílčí podobjektu nelze povolit k vyhodnocení.  
  
 Proto v původní návrhu jazyka, zakázal Stroustrup explicitní inicializaci virtuální základní třídu v rámci seznamu členů inicializace konstruktoru odvozené třídy. Když byl problém vyřešen, v praxi se neschopnost přímé inicializace virtuální základní třídy ukázalo jako proveditelné. Keith Gorlen National Institute stavu, který měl implementovat freeware verzi knihovny kolekce SmallTalk názvem nihcl, měl zásadní v přesvědčit, že měl přijít s flexibilnější návrhu jazyka.  
  
 Princip objektově orientované hierarchie návrhu obsahuje, že do odvozené třídy musí zabývat pouze veřejné provádění své přímé základní třídy. Aby bylo možné podporovat flexibilní inicializace návrhu pro virtuální dědičnost, porušil Stroustrup tuto zásadu. Většina odvozených tříd v hierarchii má odpovědnost za všechny inicializace virtuálních podobjektů bez ohledu na to, jak hluboko do hierarchie, k ní dojde. Například `inputb` a `outputb` jsou odpovědné za explicitní inicializaci jejich přímé virtuální základní třídy. Když `in_out` je odvozena z obou `inputb` a `outputb`, `in_out` zodpovědná za inicializaci jedné odebrat virtuální třídy base a v rámci explicitní inicializace `inputb` a `outputb` je potlačit.  
  
 To nabízí flexibilitu požadovaná vývojáři jazyka, ale za cenu složitou sémantiku. Tato zatížení komplikace se odstraní rychle a pokud jsme omezit virtuální základní třídu bez stavu a jednoduše povolit ji k určení rozhraní. Toto je doporučený návrh stylu v rámci jazyka C++. V rámci programování CLR je vyvolána do zásady s typem rozhraní.  
  
 Zde je ukázka jednoduchý kód – a v takovém případě je zbytečné explicitní zabalení:  
  
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
  
 Jak můžete vidět, není celé velké množství zabalení pryč. V části Visual C++, typ hodnoty je implicitní zabalení:  
  
```  
// new syntax makes boxing implicit  
array<int>^ my1DIntArray = {1,2,3,4,5};  
array<Object^>^ myObjArray = {26,27,28,29,30};  
  
Console::WriteLine( "{0}\t{1}\t{2}", 0,   
   my1DIntArray->GetLowerBound( 0 ),   
   my1DIntArray->GetUpperBound( 0 ) );  
```  
  
## <a name="see-also"></a>Viz také  
 [Hodnotové typy a jejich chování (C + +/ CLI)](../dotnet/value-types-and-their-behaviors-cpp-cli.md)   
 [Zabalení](../windows/boxing-cpp-component-extensions.md)