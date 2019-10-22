---
title: '&lt;iterator &gt;'
ms.date: 11/04/2016
f1_keywords:
- <iterator>
- iterator/std::<iterator>
helpviewer_keywords:
- iterator header
ms.assetid: c61a3962-f3ed-411a-b5a3-e8b3c2b500bd
ms.openlocfilehash: 31854834c418c6d563a0306bd2cde404b3254a23
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72687847"
---
# <a name="ltiteratorgt"></a>&lt;iterator &gt;

Definuje základní iterátor, předdefinované iterátory a iterátory proudu, jakož i několik podpůrných šablon. Předdefinované iterátory zahrnují vkládací a reverzní adaptéry. Existují tři třídy adapterů iterátoru vložení: přední, zadní a obecný. Poskytují sémantiku vkládání, nikoliv sémantikou přepsání, kterou poskytují iterátory členské funkce kontejneru.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<iterator >

**Obor názvů:** std

## <a name="remarks"></a>Poznámky

Iterátory jsou generalizacemi ukazatelů – abstrahují z jejich požadavků způsobem, který umožňuje programu C++ pracovat s různými datovými strukturami jednotným způsobem. Iterátory fungují jako prostředníci mezi kontejnery a obecnými algoritmy. Místo práce na konkrétních datových typech jsou algoritmy definovány, aby pracovaly na rozsahu určeném typem iterátoru. Datová struktura, která splňuje požadavky iterace, může pak být provozována algoritmem. Existuje pět typů nebo kategorií iterátoru, každý s vlastní sadou požadavků a výsledné funkčnosti:

- Výstup: pohybující se vpřed může ukládat, ale ne načítat hodnoty poskytnuté ostream a inserter.

- Vstup: pohybující se vpřed může načíst, ale ne ukládat hodnoty poskytnuté istream.

- Předat dál: přesunutí vpřed, může ukládat a načítat hodnoty.

- Obousměrné: přesun vpřed a zpět může ukládat a načítat hodnoty podle seznamu, sady, multisady, mapy a multimapy.

- Náhodný přístup: přístup k prvkům v libovolném pořadí, může ukládat a načítat hodnoty, podle vektoru, deque, řetězce a pole.

Iterátory, které mají větší požadavky, a tedy silnější přístup k prvkům mohou být použity namísto iterátorů s menším počtem požadavků. Pokud je volán dopředný iterátor, může být místo toho použit iterátor náhodného přístupu.

Do sady Visual Studio byla přidána rozšíření iterátorů standardní knihovny C++ za účelem podpory pro řady situací v režimu ladění pro kontrolované a nekontrolované iterátory. Další informace najdete v tématu [bezpečné knihovny: C++ standardní knihovna](../standard-library/safe-libraries-cpp-standard-library.md).

## <a name="members"></a>Členové

### <a name="functions"></a>Funkce

|||
|-|-|
|[předem](../standard-library/iterator-functions.md#advance)|Zvýší iterátor o zadaný počet pozic.|
|[back_inserter](../standard-library/iterator-functions.md#back_inserter)|Vytvoří iterátor, který může vložit prvky do zadní části zadaného kontejneru.|
|[ifunctiondiscovery](../standard-library/iterator-functions.md#begin)|Načte iterátor na první prvek v zadaném kontejneru.|
|[cbegin](../standard-library/iterator-functions.md#cbegin)|Načte konstantní iterátor na první prvek v zadaném kontejneru.|
|[cend](../standard-library/iterator-functions.md#cend)|Načte konstantní iterátor na prvek, který následuje po posledním prvku v zadaném kontejneru.|
|[crbegin –](../standard-library/iterator-functions.md#crbegin)||
|[crend](../standard-library/iterator-functions.md#crend)||
|[údajů](../standard-library/iterator-functions.md#data)||
|[délku](../standard-library/iterator-functions.md#distance)|Určuje počet kroků mezi polohami řešenými dvěma iterátory.|
|[účelu](../standard-library/iterator-functions.md#end)|Načte iterátor na prvek, který následuje po posledním prvku v zadaném kontejneru.|
|[obsahovat](../standard-library/iterator-functions.md#empty)||
|[front_inserter](../standard-library/iterator-functions.md#front_inserter)|Vytvoří iterátor, který může vložit prvky do přední části zadaného kontejneru.|
|[Inserter](../standard-library/iterator-functions.md#inserter)|Adaptér iterátoru, který přidá nový prvek do kontejneru v určeném okamžiku vložení.|
|[make_checked_array_iterator](../standard-library/iterator-functions.md#make_checked_array_iterator)|Vytvoří [checked_array_iterator](../standard-library/checked-array-iterator-class.md) , který mohou používat ostatní algoritmy. **Poznámka:**  Tato funkce je rozšířením společnosti Microsoft pro C++ standardní knihovnu. Kód implementovaný pomocí této funkce není přenosný do standardního prostředí pro sestavování v jazyce C++, která toto rozšíření společnosti Microsoft nepodporují.|
|[make_move_iterator](../standard-library/iterator-functions.md#make_move_iterator)|Vrátí iterátor přesunu obsahující zadaný iterátor jako svůj uložené základní iterátor.|
|[make_unchecked_array_iterator](../standard-library/iterator-functions.md#make_unchecked_array_iterator)|Vytvoří [unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md) , který mohou používat ostatní algoritmy. **Poznámka:**  Tato funkce je rozšířením společnosti Microsoft pro C++ standardní knihovnu. Kód implementovaný pomocí této funkce není přenosný do standardního prostředí pro sestavování v jazyce C++, která toto rozšíření společnosti Microsoft nepodporují.|
|[generace](../standard-library/iterator-functions.md#next)|Iteruje zadaný počet iterací a vrátí novou pozici iterace.|
|[prohlížen](../standard-library/iterator-functions.md#prev)|Iteruje v opačném pořadí zadaný počet iterací a vrátí novou pozici iterace.|
|[rbegin](../standard-library/iterator-functions.md#rbegin)||
|[rend](../standard-library/iterator-functions.md#rend)||
|[hodnota](../standard-library/iterator-functions.md#size)||

### <a name="operators"></a>Operátory

|||
|-|-|
|[operator!=](../standard-library/iterator-operators.md#op_neq)|Testuje, zda je objekt iterátoru na levé straně operátoru není roven objektu iterátoru na pravé straně.|
|[operator = = – operátor](../standard-library/iterator-operators.md#op_eq_eq)|Testuje, zda je objekt iterátoru na levé straně operátoru roven objektu iterátoru na pravé straně.|
|[operátor <](../standard-library/iterator-operators.md#op_lt)|Testuje, zda je objekt iterátoru na levé straně operátoru menší než objekt iterátoru na pravé straně.|
|[operátor \< =](../standard-library/iterator-operators.md#op_gt_eq)|Testuje, zda je objekt iterátoru na levé straně operátoru menší než nebo roven objektu iterátoru na pravé straně.|
|[operátor >](../standard-library/iterator-operators.md#op_gt)|Testuje, zda je objekt iterátoru na levé straně operátoru větší než objekt iterátoru na pravé straně.|
|[operator>=](../standard-library/iterator-operators.md#op_gt_eq)|Testuje, zda je objekt iterátoru na levé straně operátoru větší než nebo roven objektu iterátoru na pravé straně.|
|[operator + – operátor](../standard-library/iterator-operators.md#op_add)|Přidá posun k iterátoru a vrátí nový `reverse_iterator` adresování vloženého prvku na nové pozici posunu.|
|[podnikatel](../standard-library/iterator-operators.md#operator-)|Odečte jeden iterátor od druhého a vrátí rozdíl.|

### <a name="classes"></a>Třídy

|||
|-|-|
|[back_insert_iterator](../standard-library/back-insert-iterator-class.md)|Šablona třídy popisuje výstupní objekt iterátoru. Vloží prvky do kontejneru typu `Container`, ke kterému přistupuje prostřednictvím chráněného objektu `pointer`, který ukládá s názvem Container.|
|[bidirectional_iterator_tag](../standard-library/bidirectional-iterator-tag-struct.md)|Třída, která poskytuje návratový typ pro funkci `iterator_category`, která představuje obousměrný iterátor.|
|[checked_array_iterator](../standard-library/checked-array-iterator-class.md)|Třída, která umožňuje přístup k poli pomocí náhodného přístupu, kontrolovaného iterátoru. **Poznámka:**  Tato třída je rozšířením společnosti Microsoft pro C++ standardní knihovnu. Kód implementovaný pomocí této funkce není přenosný do standardního prostředí pro sestavování v jazyce C++, která toto rozšíření společnosti Microsoft nepodporují.|
|[forward_iterator_tag](../standard-library/forward-iterator-tag-struct.md)|Třída, která poskytuje návratový typ pro funkci `iterator_category`, která představuje dopředný iterátor.|
|[front_insert_iterator](../standard-library/front-insert-iterator-class.md)|Šablona třídy popisuje výstupní objekt iterátoru. Vloží prvky do kontejneru typu `Container`, ke kterému přistupuje prostřednictvím chráněného objektu `pointer`, který ukládá s názvem Container.|
|[input_iterator_tag](../standard-library/input-iterator-tag-struct.md)|Třída, která poskytuje návratový typ pro funkci `iterator_category`, která představuje vstupní iterátor.|
|[insert_iterator](../standard-library/insert-iterator-class.md)|Šablona třídy popisuje výstupní objekt iterátoru. Vloží prvky do kontejneru typu `Container`, ke kterému přistupuje prostřednictvím chráněného objektu `pointer`, který ukládá s názvem Container. Také ukládá chráněný objekt `iterator` třídy `Container::iterator` se nazývá `iter`.|
|[istream_iterator](../standard-library/istream-iterator-class.md)|Šablona třídy popisuje vstupní objekt iterátoru. Extrahuje objekty třídy `Ty` ze vstupního datového proudu, ke kterému přistupuje prostřednictvím objektu, který ukládá, typu pointer do `basic_istream` \<**elem**, **TR**>.|
|[istreambuf_iterator](../standard-library/istreambuf-iterator-class.md)|Šablona třídy popisuje vstupní objekt iterátoru. Vloží prvky třídy `Elem` do vyrovnávací paměti výstupního datového proudu, ke kterému přistupuje prostřednictvím objektu, který ukládá, typu `pointer` na `basic_streambuf` \<**elem**, **TR**>.|
|[iterátor](../standard-library/iterator-struct.md)|Šablona třídy se používá jako základní typ pro všechny iterátory.|
|[iterator_traits](../standard-library/iterator-traits-struct.md)|Třída pomocné šablony poskytující kritické typy, které jsou spojeny s různými typy iterátoru, aby na ně bylo možné odkazovat stejným způsobem.|
|[move_iterator](../standard-library/move-iterator-class.md)|Objekt `move_iterator` ukládá iterátor náhodného přístupu typu `RandomIterator`. Chová se jako iterátor s náhodným přístupem, pokud není dereferencován. Výsledek `operator*` je implicitně převeden na `value_type&&:` a vytvoří `rvalue reference`.|
|[ostream_iterator](../standard-library/ostream-iterator-class.md)|Šablona třídy popisuje výstupní objekt iterátoru. Vloží objekty třídy `Type` do výstupního datového proudu, ke kterému přistupuje prostřednictvím objektu, který ukládá, typu `pointer` na `basic_ostream` \<**elem**, **TR**>.|
|[ostreambuf_iterator – třída](../standard-library/ostreambuf-iterator-class.md)|Šablona třídy popisuje výstupní objekt iterátoru. Vloží prvky třídy `Elem` do vyrovnávací paměti výstupního datového proudu, ke kterému přistupuje prostřednictvím objektu, který ukládá, typu pointer do `basic_streambuf` \<**elem**, **TR**>.|
|[output_iterator_tag](../standard-library/output-iterator-tag-struct.md)|Třída, která poskytuje návratový typ pro funkci `iterator_category`, která představuje výstupní iterátor.|
|[random_access_iterator_tag](../standard-library/random-access-iterator-tag-struct.md)|Třída, která poskytuje návratový typ pro funkci `iterator_category`, která představuje iterátor náhodného přístupu.|
|[reverse_iterator](../standard-library/reverse-iterator-class.md)|Šablona třídy popisuje objekt, který se chová jako iterátor s náhodným přístupem, pouze v opačném případě.|
|[unchecked_array_iterator](../standard-library/unchecked-array-iterator-class.md)|Třída, která umožňuje přístup k poli pomocí náhodného přístupu, nekontrolovaného iterátoru. **Poznámka:**  Tato třída je rozšířením společnosti Microsoft pro C++ standardní knihovnu. Kód implementovaný pomocí této funkce není přenosný do standardního prostředí pro sestavování v jazyce C++, která toto rozšíření společnosti Microsoft nepodporují.|

## <a name="see-also"></a>Viz také:

@No__t_1 [referenčních souborů hlaviček](../standard-library/cpp-standard-library-header-files.md)
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md) \
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
