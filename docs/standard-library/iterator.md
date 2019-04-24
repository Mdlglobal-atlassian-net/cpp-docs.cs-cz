---
title: '&lt;iterator&gt;'
ms.date: 11/04/2016
f1_keywords:
- <iterator>
- iterator/std::<iterator>
helpviewer_keywords:
- iterator header
ms.assetid: c61a3962-f3ed-411a-b5a3-e8b3c2b500bd
ms.openlocfilehash: 1b0d3282075246f3b217f0c8acac19ed8ece79cb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62224087"
---
# <a name="ltiteratorgt"></a>&lt;iterator&gt;

Definuje základní iterátor, předdefinované iterátory a iterátory proudu, jakož i několik podpůrných šablon. Předdefinované iterátory zahrnují vkládací a reverzní adaptéry. Existují tři třídy adapterů iterátoru vložení: přední, zadní a obecný. Poskytují sémantiku vkládání, nikoliv sémantikou přepsání, kterou poskytují iterátory členské funkce kontejneru.

## <a name="syntax"></a>Syntaxe

```cpp
#include <iterator>
```

## <a name="remarks"></a>Poznámky

Iterátory jsou generalizacemi ukazatelů – abstrahují z jejich požadavků způsobem, který umožňuje programu C++ pracovat s různými datovými strukturami jednotným způsobem. Iterátory fungují jako prostředníci mezi kontejnery a obecnými algoritmy. Místo práce na konkrétních datových typech jsou algoritmy definovány, aby pracovaly na rozsahu určeném typem iterátoru. Datová struktura, která splňuje požadavky iterace, může pak být provozována algoritmem. Existuje pět typů nebo kategorií iterátoru, každý s vlastní sadou požadavků a výsledné funkčnosti:

- Výstup: pohybující se vpřed může ukládat, ale ne načítat hodnoty poskytnuté ostream a inserter.

- Vstup: pohybující se vpřed může načíst, ale ne ukládat hodnoty poskytnuté istream.

- Předat dál: přesunutí vpřed, může ukládat a načítat hodnoty.

- Obousměrné: přesun vpřed a zpět může ukládat a načítat hodnoty podle seznamu, sady, multisady, mapy a multimapy.

- Náhodný přístup: přístup k prvkům v libovolném pořadí, může ukládat a načítat hodnoty, podle vektoru, deque, řetězce a pole.

Iterátory, které mají větší požadavky, a tedy silnější přístup k prvkům mohou být použity namísto iterátorů s menším počtem požadavků. Pokud je volán dopředný iterátor, může být místo toho použit iterátor náhodného přístupu.

Do sady Visual Studio byla přidána rozšíření iterátorů standardní knihovny C++ za účelem podpory pro řady situací v režimu ladění pro kontrolované a nekontrolované iterátory. Další informace najdete v tématu [bezpečné knihovny: C++Standardní knihovna](../standard-library/safe-libraries-cpp-standard-library.md).

### <a name="functions"></a>Funkce

|Funkce|Popis|
|-|-|
|[advance](../standard-library/iterator-functions.md#advance)|Zvýší iterátor o zadaný počet pozic.|
|[back_inserter](../standard-library/iterator-functions.md#back_inserter)|Vytvoří iterátor, který může vložit prvky do zadní části zadaného kontejneru.|
|[začít](../standard-library/iterator-functions.md#begin)|Načte iterátor na první prvek v zadaném kontejneru.|
|[cbegin](../standard-library/iterator-functions.md#cbegin)|Načte konstantní iterátor na první prvek v zadaném kontejneru.|
|[cend](../standard-library/iterator-functions.md#cend)|Načte konstantní iterátor na prvek, který následuje po posledním prvku v zadaném kontejneru.|
|[distance](../standard-library/iterator-functions.md#distance)|Určuje počet kroků mezi polohami řešenými dvěma iterátory.|
|[ukončení](../standard-library/iterator-functions.md#end)|Načte iterátor na prvek, který následuje po posledním prvku v zadaném kontejneru.|
|[front_inserter](../standard-library/iterator-functions.md#front_inserter)|Vytvoří iterátor, který může vložit prvky do přední části zadaného kontejneru.|
|[inserter](../standard-library/iterator-functions.md#inserter)|Adaptér iterátoru, který přidá nový prvek do kontejneru v určeném okamžiku vložení.|
|[make_checked_array_iterator](../standard-library/iterator-functions.md#make_checked_array_iterator)|Vytvoří [checked_array_iterator](../standard-library/checked-array-iterator-class.md) , který mohou používat ostatní algoritmy. **Poznámka:**  Tato funkce je rozšířením společnosti Microsoft pro standardní knihovnu jazyka C++. Kód implementovaný pomocí této funkce není přenosný do standardního prostředí pro sestavování v jazyce C++, která toto rozšíření společnosti Microsoft nepodporují.|
|[make_move_iterator](../standard-library/iterator-functions.md#make_move_iterator)|Vrátí iterátor přesunu obsahující zadaný iterátor jako svůj uložené základní iterátor.|
|[make_unchecked_array_iterator](../standard-library/iterator-functions.md#make_unchecked_array_iterator)|Vytvoří [unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md) , který mohou používat ostatní algoritmy. **Poznámka:**  Tato funkce je rozšířením společnosti Microsoft pro standardní knihovnu jazyka C++. Kód implementovaný pomocí této funkce není přenosný do standardního prostředí pro sestavování v jazyce C++, která toto rozšíření společnosti Microsoft nepodporují.|
|[next](../standard-library/iterator-functions.md#next)|Iteruje zadaný počet iterací a vrátí novou pozici iterace.|
|[prev](../standard-library/iterator-functions.md#prev)|Iteruje v opačném pořadí zadaný počet iterací a vrátí novou pozici iterace.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator!=](../standard-library/iterator-operators.md#op_neq)|Testuje, zda je objekt iterátoru na levé straně operátoru není roven objektu iterátoru na pravé straně.|
|[operator==](../standard-library/iterator-operators.md#op_eq_eq)|Testuje, zda je objekt iterátoru na levé straně operátoru roven objektu iterátoru na pravé straně.|
|[Operator <](../standard-library/iterator-operators.md#op_lt)|Testuje, zda je objekt iterátoru na levé straně operátoru menší než objekt iterátoru na pravé straně.|
|[– Operátor\<=](../standard-library/iterator-operators.md#op_gt_eq)|Testuje, zda je objekt iterátoru na levé straně operátoru menší než nebo roven objektu iterátoru na pravé straně.|
|[operator>](../standard-library/iterator-operators.md#op_gt)|Testuje, zda je objekt iterátoru na levé straně operátoru větší než objekt iterátoru na pravé straně.|
|[operator>=](../standard-library/iterator-operators.md#op_gt_eq)|Testuje, zda je objekt iterátoru na levé straně operátoru větší než nebo roven objektu iterátoru na pravé straně.|
|[Operator +](../standard-library/iterator-operators.md#op_add)|Přidá posun do iterátoru a vrátí nový `reverse_iterator` adresující vložený prvek na nové pozici posunu.|
|[Operator-](../standard-library/iterator-operators.md#operator-)|Odečte jeden iterátor od druhého a vrátí rozdíl.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[back_insert_iterator](../standard-library/back-insert-iterator-class.md)|Třída šablony popisuje výstupní objekt iterátoru. Vloží prvky do kontejneru typu `Container`, ke kterému přistupuje přes chráněný `pointer` objektu ukládá volaný kontejner.|
|[bidirectional_iterator_tag](../standard-library/bidirectional-iterator-tag-struct.md)|Třída, která poskytuje návratový typ pro `iterator_category` funkce, která představuje obousměrný iterátor.|
|[checked_array_iterator](../standard-library/checked-array-iterator-class.md)|Třída, která umožňuje přístup k poli pomocí náhodného přístupu, kontrolovaného iterátoru. **Poznámka:**  Tato třída je rozšířením společnosti Microsoft pro standardní knihovnu jazyka C++. Kód implementovaný pomocí této funkce není přenosný do standardního prostředí pro sestavování v jazyce C++, která toto rozšíření společnosti Microsoft nepodporují.|
|[forward_iterator_tag](../standard-library/forward-iterator-tag-struct.md)|Třída, která poskytuje návratový typ pro `iterator_category` funkce, která představuje iterátor předání.|
|[front_insert_iterator](../standard-library/front-insert-iterator-class.md)|Třída šablony popisuje výstupní objekt iterátoru. Vloží prvky do kontejneru typu `Container`, ke kterému přistupuje přes chráněný `pointer` objektu ukládá volaný kontejner.|
|[input_iterator_tag](../standard-library/input-iterator-tag-struct.md)|Třída, která poskytuje návratový typ pro `iterator_category` funkce, která představuje iterátor vstupu.|
|[insert_iterator](../standard-library/insert-iterator-class.md)|Třída šablony popisuje výstupní objekt iterátoru. Vloží prvky do kontejneru typu `Container`, ke kterému přistupuje přes chráněný `pointer` objektu ukládá volaný kontejner. Také ukládá chráněný `iterator` objekt třídy `Container::iterator`, označované jako `iter`.|
|[istream_iterator](../standard-library/istream-iterator-class.md)|Třída šablony popisuje vstupní objekt iterátoru. Extrahuje objekty třídy `Ty` ze vstupního datového proudu, ke kterému přistupuje prostřednictvím objektu, který ukládá, typu ukazatele do `basic_istream` \< **Elem**, **Tr**>.|
|[istreambuf_iterator](../standard-library/istreambuf-iterator-class.md)|Třída šablony popisuje vstupní objekt iterátoru. Vkládá prvky třídy `Elem` do výstupní mezipaměti datového proudu, ke kterému přistupuje prostřednictvím objektu, který se ukládá, typu `pointer` k `basic_streambuf` \< **Elem**, **Tr** >.|
|[iterator](../standard-library/iterator-struct.md)|Třída šablony slouží jako základní typ pro všechny iterátory.|
|[iterator_traits](../standard-library/iterator-traits-struct.md)|Třída pomocné šablony poskytující kritické typy, které jsou spojeny s různými typy iterátoru, aby na ně bylo možné odkazovat stejným způsobem.|
|[move_iterator](../standard-library/move-iterator-class.md)|A `move_iterator` ukládá iterátor náhodného přístupu typu `RandomIterator`. Chová se jako iterátor s náhodným přístupem, pokud není dereferencován. Výsledek `operator*` je implicitně přetypován na `value_type&&:` provést `rvalue reference`.|
|[ostream_iterator](../standard-library/ostream-iterator-class.md)|Třída šablony popisuje výstupní objekt iterátoru. Vkládá objekty třídy `Type` do výstupního proudu, ke kterému přistupuje prostřednictvím objektu, který se ukládá, typu `pointer` k `basic_ostream` \< **Elem**, **Tr**>.|
|[ostreambuf_iterator – třída](../standard-library/ostreambuf-iterator-class.md)|Třída šablony popisuje výstupní objekt iterátoru. Vkládá prvky třídy `Elem` do výstupní mezipaměti datového proudu, ke kterému přistupuje prostřednictvím objektu, který ukládá, typu ukazatele do `basic_streambuf` \< **Elem**, **Tr**>.|
|[output_iterator_tag](../standard-library/output-iterator-tag-struct.md)|Třída, která poskytuje návratový typ pro `iterator_category` funkce, která představuje iterátor výstupu.|
|[random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md)|Třída, která poskytuje návratový typ pro `iterator_category` funkce, která představuje iterátor náhodného přístupu.|
|[reverse_iterator](../standard-library/reverse-iterator-class.md)|Třída šablony popisuje objekt, který se chová jako iterátor s náhodným přístupem, jen obráceně.|
|[unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md)|Třída, která umožňuje přístup k poli pomocí náhodného přístupu, nekontrolovaného iterátoru. **Poznámka:**  Tato třída je rozšířením společnosti Microsoft pro standardní knihovnu jazyka C++. Kód implementovaný pomocí této funkce není přenosný do standardního prostředí pro sestavování v jazyce C++, která toto rozšíření společnosti Microsoft nepodporují.|

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
