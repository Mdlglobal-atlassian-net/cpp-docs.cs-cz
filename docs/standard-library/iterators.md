---
title: "Iterátory | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- iterator conventions
- C++ Standard Library, iterator conventions
ms.assetid: 2f746be7-b37d-4bfc-bf05-be4336ca982f
caps.latest.revision: "12"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: c0a9b850100d78a18e39e5cc552cb8461b3726a0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="iterators"></a>Iterátory
Iterátor je objekt, který můžete iteraci nad elementy v kontejneru standardní knihovna C++ a poskytují přístup na jednotlivé prvky. Standardní knihovna C++ kontejnerů, které všechny poskytují iterátory, aby algoritmy přístup jejich elementů standardní způsobem, aniž by museli dělat starosti s typem kontejneru elementy jsou uloženy v.  
  
 Můžete použít iterátory explicitně pomocí člen a globální funkce jako je například begin() a end() a operátory, jako ++ a--k přesunutí nebo předchozí. Můžete také použít iterátory implicitně s rozsahem-pro smyčky nebo (pro některé typy iterator) operátor dolního indexu [].  
  
 Standardní knihovny C++ začátek pořadí nebo rozsah je první prvek. Konci pořadí nebo rozsah je vždy definována jako jeden za posledním elementem. Globální funkce začínat a končit návratový iterátory do zadaného kontejneru. Typické explicitní iterator smyčky přes všechny elementy v kontejneru vypadá takto:  
  
```  
 
vector<int> vec{ 0,1,2,3,4 };  
for (auto it = begin(vec);

it != end(vec);

it++)  
{  // Access element using dereference operator
    cout <<*it <<" ";  
}  
```  
  
 Totéž můžete udělat jednodušeji s rozsahem-pro smyčka:  
  
```  
for (auto num : vec)  
 {  // no deference operator
    cout <<num <<" ";  
 }  
```  
  
 Existuje pěti kategorií iterátory. V pořadí podle zvýšení výkonu jsou kategorií:  
  
- **Výstup**. Iterátor výstup `X` můžete předat iterace v sekvenci s použitím nástroje ++ operátor a lze zapsat pouze jednou, element pomocí * operátor.  
  
- **Vstup**. Vstupní iterator `X` můžete předat iterace v sekvenci s použitím nástroje ++ operátor a můžete číst element libovolný počet časy pomocí * operátor. Vstupní iterátory, můžete porovnat s použitím nástroje ++ a! = operátory. Poté, co bude zvýšit libovolné kopii vstupní iterator, žádný z jiné kopie bezpečně je možné porovnávat, zrušením odkazu, nebo zvýšena po tomto datu.  
  
- **Předat dál**. Předat dál iterator `X` můžete předat iterace v pořadí pomocí ++ operátor a můžete číst libovolný element, nebo můžete zapsat bez const elementy libovolný počet časy pomocí * operátor. Máte přístup k členy element pomocí -> – operátor a porovnání dopředného iterátory pomocí == a! = operátory. Může vytvářet více kopií dopředného iterator, z nichž každý vyhodnoceny odkazy a zvýší nezávisle. Předat dál iterator, který je inicializován bez ohledu na kontejneru, se nazývá null dopředného iterator. Null dopředného iterátory porovnat vždy stejná.  
  
-   Obousměrné. Iterator obousměrného `X` může proběhnout dopředného iterator. Můžete může, ale také snížení iterator obousměrného jako v –`X`, `X`–, nebo (`V` = *`X`--). Můžete používat členy element a porovnání obousměrného iterátory stejným způsobem jako dopředného iterátory.  
  
- **Náhodný přístup**. Iterator náhodný přístup `X` může proběhnout iterator obousměrné. S náhodným přístupem iterator můžete [] – operátor dolního indexu na elementy přístup. Můžete použít +, -, += a-= operátory k přesunutí nebo předchozí zadaný počet elementů a k výpočtu vzdálenost mezi iterátory. Iterátory obousměrného můžete porovnat s použitím ==,! =, \<, >, \<=, a > =.  
  
 Všechny iterátory můžete přiřadit nebo zkopírovat. Se předpokládá, že zjednodušené objekty a jsou často předán a vrácené hodnoty, není odkazem. Všimněte si také, že žádná z výše uvedených pokynů operací může vyvolat výjimku při provádění v platný iterator.  
  
 Hierarchie kategorií iterator jde vyhodnotit zobrazením tři pořadí. Pro přístup jen pro zápis do pořadí můžete použít některou z:  
  
```  
output iterator  
 -> forward iterator  
 -> bidirectional iterator  
 -> random-access iterator  
```  
  
 Na šipku vpravo znamená "může být nahrazen." Libovolný algoritmus, který volá pro výstup iterovat by měly fungovat vhodně s dopředného iterator, například ale *není* opačným způsobem.  
  
 Pro přístup jen pro čtení do pořadí můžete použít některou z:  
  
```  
input iterator  
 -> forward iterator  
 -> bidirectional iterator  
 -> random-access iterator  
```  
  
 V takovém případě je nejnižší prioritu všech kategorií, vstupní iterator.  
  
 Nakonec pro přístup pro čtení a zápis do pořadí, můžete použít některý z:  
  
```  
forward iterator  
 -> bidirectional iterator  
 -> random-access iterator  
```  
  
 Ukazatele na objekt může vždy sloužit jako iterator náhodným přístupem, aby mohl sloužit jako žádné kategorie iterator pokud ji podporuje přístup správné pro čtení a zápis pořadí, které určí.  
  
 Iterátor `Iterator` než objekt ukazatel třeba definovat typy členů vyžadují specializace `iterator_traits<Iterator>`. Všimněte si, že tyto požadavky lze splnit odvozením `Iterator` ze základní třídy veřejné [iterator](../standard-library/iterator-struct.md).  
  
 Je důležité porozumět lišící a omezení pro každou kategorii iterator najdete v části Jak iterátory používají kontejnery a algoritmy ve standardní knihovně C++.  
  
> [!NOTE]
>  Používání iterátory explicitně pomocí rozsah se můžete vyhnout-smyčky for. Další informace najdete v tématu [smyčky (moderní verze jazyka C++)](http://msdn.microsoft.com/en-us/b1b2779c-750e-4576-a514-a84178eae9da).  
  
 Visual C++ teď nabízí checked – iterátory a ladění iterátory zajistit Nepřepisovat hranice vaší kontejneru. Další informace najdete v tématu [zaškrtnutí iterátory](../standard-library/checked-iterators.md) a [podpora ladění iterátorů](../standard-library/debug-iterator-support.md).  
  
## <a name="see-also"></a>Viz také  
 [Standardní C++ – referenční dokumentace knihoven](../standard-library/cpp-standard-library-reference.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)

