---
title: '&lt;algoritmus&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <algorithm>
dev_langs:
- C++
helpviewer_keywords:
- algorithm header [C++]
- C++ Standard Library, algorithms
- <algorithm> header
ms.assetid: 19f97711-7a67-4a65-8fd1-9a2bd3ca327d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fc5e181a933c0c511802a0270026635a1766a7be
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33848203"
---
# <a name="ltalgorithmgt"></a>&lt;Algoritmus&gt;

Definuje standardní knihovna C++ kontejneru šablony funkce, které provádět algoritmy.

## <a name="syntax"></a>Syntaxe

```cpp
(see relevant links below for specific algorithm syntax)
```

## <a name="remarks"></a>Poznámky

Standardní knihovna C++ algoritmy jsou obecné, protože pracují na různých datové struktury. Datové struktury, které mohou pracovat s obsahují nejen třídy kontejnerů standardní knihovna C++, například `vector` a `list`, ale také program definované datové struktury a pole elementů, které splňují požadavky na konkrétní třídy algoritmus. Standardní knihovna C++ algoritmy tato úroveň obecné dosáhnout přístup k informacím a procházení elementy kontejneru nepřímo prostřednictvím iterátory.

Standardní knihovna C++ algoritmy zpracovat iterator rozsahy, které jsou obvykle určené jejich počáteční nebo koncová pozice. Tyto rozsahy musí být platné v tom smyslu, že na všechny ukazatele v rozsazích musí být možné nepřímo odkazovat a v rámci sekvencí každého rozsahu musí být poslední pozice dosažitelná z první pomocí přírůstku.

Algoritmy standardní knihovna C++ rozšířit akcí podporovaných operacích a členské funkce kontejneru každé standardní knihovna C++ a povolit práce, například různých typů objektů kontejneru ve stejnou dobu. K předání informací o účelu algoritmů byly použity dvě přípony.

- `_if` Příponu označuje, že algoritmus se používá s objekty funkcí operační na hodnoty elementů ne na hodnoty elementů sami. `find_if` Algoritmus hledá elementy, jejichž hodnoty splňují kritérium zadaný objekt funkce a `find` algoritmus hledá konkrétní hodnotu.

- Přípona „_copy“ označuje, že algoritmus nejen manipuluje s hodnotami prvků, ale také kopíruje změněné hodnoty do cílového rozsahu. `reverse` Algoritmus obrátí pořadí prvků v rozsahu a `reverse_copy` algoritmus také zkopíruje výsledek do cílové oblasti.

Standardní knihovna C++ algoritmy jsou často klasifikovány do skupin, které indikují něco o jejich účel nebo požadavky. Patří mezi ně úprava algoritmy, které změňte hodnotu elementů ve srovnání s úprava algoritmy, které nepodporují. Mutující algoritmy mění pořadí prvků, ale nikoli jejich hodnoty. Odebírající algoritmy mohou odstranit prvky z rozsahu nebo rozsah zkopírovat. Řazení algoritmy přeuspořádejte elementy v rozsahu různými způsoby a algoritmy seřazené oblasti fungovat jenom na rozsahy, jehož elementy seřazeny určitým způsobem.

Standardní knihovna C++ číselné algoritmy, které jsou k dispozici pro zpracování číselné mají své vlastní soubor hlaviček [ \<číselné >](../standard-library/numeric.md), a funkce objekty a adaptéry jsou definovány v hlavičce [ \<funkční >](../standard-library/functional.md) funkce objekty, které vracejí logické hodnoty jsou známé jako predikáty. Predikát binární výchozí je porovnání `operator<`. Seřazované prvky musí být obecně menší než srovnatelné, což znamená, že když jsou uvedeny dva prvky, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý), nebo zda jeden je menší než druhý. Výsledkem je řazení mezi neekvivalentními prvky.

### <a name="function-templates"></a>Šablony funkcí

|Šablony funkcí|Popis|
|-|-|
|[adjacent_find](../standard-library/algorithm-functions.md#adjacent_find)|Vyhledá dva sousedící prvky, které jsou buď rovny, nebo splňují zadanou podmínku.|
|[all_of](../standard-library/algorithm-functions.md#all_of)|Vrátí `true` při podmínku nachází na každý prvek v daném rozsahu.|
|[any_of](../standard-library/algorithm-functions.md#any_of)|Vrátí `true` Pokud je přítomen alespoň jednou v určeném rozsahu elementů podmínku.|
|[binary_search](../standard-library/algorithm-functions.md#binary_search)|Ověřuje, zda v seřazeném rozsahu existuje prvek, který je roven zadané hodnotě nebo je jí ekvivalentní ve smyslu určeném binárním predikátem.|
|[Kopírování](../standard-library/algorithm-functions.md#copy)|Přiřadí hodnoty prvků ze zdrojového rozsahu do cílového rozsahu a provede iterace přes zdrojové sekvence prvků a přiřadí je novým pozicím směrem dopředu.|
|[copy_backward –](../standard-library/algorithm-functions.md#copy_backward)|Přiřadí hodnoty prvků ze zdrojového rozsahu do cílového rozsahu a provede iterace přes zdrojové sekvence prvků a přiřadí je novým pozicím směrem dozadu.|
|[copy_if](../standard-library/algorithm-functions.md#copy_if)|Zkopírujte všechny elementy v zadaném rozsahu, který testovací `true` pro zadanou podmínku.|
|[copy_n](../standard-library/algorithm-functions.md#copy_n)|Zkopíruje zadaný počet prvků.|
|[Počet](../standard-library/algorithm-functions.md#count)|Vrátí počet prvků v rozsahu, jejichž hodnoty odpovídají zadané hodnotě.|
|[count_if](../standard-library/algorithm-functions.md#count_if)|Vrátí počet prvků v rozsahu, jejichž hodnoty odpovídají zadané podmínce.|
|[Rovná](../standard-library/algorithm-functions.md#equal)|Porovná dva rozsahy prvek podle prvku buď ke zjištění rovnosti, nebo ekvivalentnosti ve smyslu určeném binárním predikátem.|
|[equal_range](../standard-library/algorithm-functions.md#equal_range)|Najde dvojici pozic v seřazeném rozsahu. První bude menší nebo rovna pozici zadaného prvku a druhá větší než pozice prvku, kde smysl ekvivalence nebo řazení použitý k určení pozic v sekvenci může být určen binárním predikátem.|
|[výplně](../standard-library/algorithm-functions.md#fill)|Každému prvku v zadaném rozsahu přiřadí stejnou novou hodnotu.|
|[fill_n](../standard-library/algorithm-functions.md#fill_n)|Přiřadí novou hodnotu zadanému počtu prvků v rozsahu, který začíná konkrétním prvkem.|
|[Najít](../standard-library/algorithm-functions.md#find)|Vyhledá pozici prvního výskytu prvku v rozsahu, který má zadanou hodnotu.|
|[find_end –](../standard-library/algorithm-functions.md#find_end)|Vyhledá v rozsahu poslední dílčí sekvenci, která je shodná se zadanou sekvencí nebo která je ekvivalentní ve smyslu určeném binárním predikátem.|
|[find_first_of](../standard-library/algorithm-functions.md#find_first_of)|Vyhledá první výskyt jedné z několika hodnot v cílovém rozsahu nebo první výskyt jednoho z několika prvků, které jsou ekvivalentní ve smyslu určeném binárním predikátem zadané sadě prvků.|
|[find_if –](../standard-library/algorithm-functions.md#find_if)|Vyhledá pozici prvního výskytu prvku v rozsahu, který splňuje zadanou podmínku.|
|[find_if_not –](../standard-library/algorithm-functions.md#find_if_not)|Vrátí první prvek v zadaném rozsahu, který nesplňuje podmínku.|
|[for_each](../standard-library/algorithm-functions.md#for_each)|Na každý prvek v pořadí dopředu v rozsahu použije zadaný objekt funkce a vrátí objekt funkce.|
|[Generovat](../standard-library/algorithm-functions.md#generate)|Přiřadí hodnoty generované objektem funkce každému prvku v rozsahu.|
|[generate_n –](../standard-library/algorithm-functions.md#generate_n)|Přiřadí hodnoty generované objektem funkce zadanému počtu prvků v rozsahu a vrátí pozici prvku za poslední přiřazenou hodnotou.|
|[Zahrnuje](../standard-library/algorithm-functions.md#includes)|Ověřuje, zda jeden seřazený rozsah obsahuje všechny prvky obsažené ve druhém seřazeném rozsahu, kde kritérium pořadí nebo ekvivalence mezi prvky může být určeno binárním predikátem.|
|[inplace_merge](../standard-library/algorithm-functions.md#inplace_merge)|Kombinuje prvky ze dvou po sobě následujících seřazených rozsahů do jednoho seřazeného rozsahu, kde kritérium pořadí může být určeno binárním predikátem.|
|[is_heap](../standard-library/algorithm-functions.md#is_heap)|Vrátí `true` Pokud haldy formuláři elementů v zadaném rozsahu.|
|[is_heap_until –](../standard-library/algorithm-functions.md#is_heap_until)|Vrátí `true` Pokud zadaný rozsah forms haldy až posledním elementem.|
|[is_partitioned](../standard-library/algorithm-functions.md#is_partitioned)|Vrátí `true` Pokud všechny elementy v daném rozsahu, který testovací `true` pro podmínku dřívější než žádné elementy, které testovací `false`.|
|[is_permutation](../standard-library/algorithm-functions.md#is_permutation)|Určuje, zda elementů v daném rozsahu tvořit platný Permutace.|
|[is_sorted](../standard-library/algorithm-functions.md#is_sorted)|Vrátí `true` Pokud elementů v zadaném rozsahu seřazená.|
|[is_sorted_until –](../standard-library/algorithm-functions.md#is_sorted_until)|Vrátí `true` Pokud elementů v zadaném rozsahu seřazená.|
|[iter_swap](../standard-library/algorithm-functions.md#iter_swap)|Vymění dvě hodnoty odkazované dvojicí zadaných iterátorů.|
|[lexicographical_compare](../standard-library/algorithm-functions.md#lexicographical_compare)|Porovná prvek po prvku mezi dvěma sekvencemi k určení, která z nich je menší.|
|[lower_bound –](../standard-library/algorithm-functions.md#lower_bound)|Najde pozici prvního prvku v seřazeném rozsahu, jehož hodnota je větší nebo rovna zadané hodnotě, kde kritérium pořadí může být určeno primárním predikátem.|
|[make_heap](../standard-library/algorithm-functions.md#make_heap)|Převede prvky ze zadaného rozsahu do haldy, ve které je první prvek největší a pro kterou může být kritérium řazení určeno binárním predikátem.|
|[max](../standard-library/algorithm-functions.md#max)|Porovná dva objekty a vrátí větší z nich, kde kritérium pořadí může být určeno binárním predikátem.|
|[max_element](../standard-library/algorithm-functions.md#max_element)|Vyhledá první výskyt největšího prvku v zadaném rozsahu, kde kritérium pořadí může být určeno binárním predikátem.|
|[Sloučení](../standard-library/algorithm-functions.md#merge)|Kombinuje všechny prvky ze dvou po sobě seřazených zdrojových rozsahů do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.|
|[Min.](../standard-library/algorithm-functions.md#min)|Porovná dva objekty a vrátí menší z nich, kde kritérium pořadí může být určeno binárním predikátem.|
|[min_element](../standard-library/algorithm-functions.md#min_element)|Vyhledá první výskyt nejmenšího prvku v zadaném rozsahu, kde kritérium pořadí může být určeno binárním predikátem.|
|[minmax](../standard-library/algorithm-functions.md#minmax)|Porovná dva vstupní parametry a vrátí je jako dvojici v pořadí od nejmenšího po největší.|
|[minmax_element](../standard-library/algorithm-functions.md#minmax_element)|Provede práci provádí [min_element –](../standard-library/algorithm-functions.md#min_element) a [max_element –](../standard-library/algorithm-functions.md#max_element) jedno volání.|
|[Neshoda](../standard-library/algorithm-functions.md#mismatch)|Porovná dva rozsahy prvek po prvku buď ke zjištění rovnosti, nebo ekvivalence ve smyslu určeném binárním predikátem a vyhledá první pozici, kde existuje rozdíl.|
|[&lt;alg&gt; přesunout](../standard-library/algorithm-functions.md#alg_move)|Přesune prvky přidružené k určenému rozsahu.|
|[move_backward](../standard-library/algorithm-functions.md#move_backward)|Přesune prvky jednoho iterátoru do druhého. Pohyb začíná posledním prvkem v daném rozsahu a končí prvním prvkem v daném rozsahu.|
|[next_permutation](../standard-library/algorithm-functions.md#next_permutation)|Znovu uspořádá prvky v rozsahu tak, aby původní pořadí bylo nahrazeno lexikograficky následující větší permutací, pokud existuje, kde význam následujícího může být určen binárním predikátem.|
|[none_of](../standard-library/algorithm-functions.md#none_of)|Vrátí `true` při podmínku nachází nikdy mezi elementy v daném rozsahu.|
|[nth_element –](../standard-library/algorithm-functions.md#nth_element)|Oddíly rozsahu prvků, správně hledání *n*element TD pořadí v rozsahu, aby všechny elementy úrovních před ním jsou menší než nebo rovna hodnotě ho a všechny elementy, které následují v pořadí jsou větší než nebo roven k němu.|
|[partial_sort](../standard-library/algorithm-functions.md#partial_sort)|Uspořádá zadaný počet menších prvků v rozsahu do nesestupného pořadí nebo podle setřiďovacího kritéria určeného binárním predikátem.|
|[partial_sort_copy](../standard-library/algorithm-functions.md#partial_sort_copy)|Zkopíruje prvky ze zdrojového rozsahu do cílového rozsahu, kde zdrojové prvky jsou seřazeny buď podle binárního predikátu „menší než“ nebo jiného určeného binárního predikátu.|
|[Oddíl](../standard-library/algorithm-functions.md#partition)|Rozdělí prvky v rozsahu do dvou oddělených sad. Prvky, které splňují unární predikát, jsou umístěny před těmi, které jej nesplňují.|
|[partition_copy –](../standard-library/algorithm-functions.md#partition_copy)|Zkopíruje elementy, pro které je podmínku `true` do cílové a pro které podmínku `false` do jiného. Prvky musí pocházet ze zadaného rozsahu.|
|[partition_point](../standard-library/algorithm-functions.md#partition_point)|Vrátí první prvek v zadaném rozsahu, který nesplňuje podmínku. Prvky jsou seřazeny tak, aby ty, které splňují podmínku, předcházely těm, které ji nesplňují.|
|[pop_heap –](../standard-library/algorithm-functions.md#pop_heap)|Odstraní největší prvek z přední části haldy až do předposlední pozice v rozsahu a ze zbývajících prvků vytvoří novou haldu.|
|[prev_permutation](../standard-library/algorithm-functions.md#prev_permutation)|Znovu uspořádá prvky v rozsahu tak, aby původní pořadí bylo nahrazeno lexikograficky následující větší permutací, pokud existuje, kde význam následujícího může být určen binárním predikátem.|
|[push_heap –](../standard-library/algorithm-functions.md#push_heap)|Přidá prvek, který je na konci rozsahu, do stávající haldy, která zahrnuje předchozí prvky daného rozsahu.|
|[random_shuffle](../standard-library/algorithm-functions.md#random_shuffle)|Přeuspořádá posloupnost *N* elementy v rozsahu do jedné ze *N*! možné uspořádání náhodně vybrané.|
|[remove](../standard-library/algorithm-functions.md#remove)|Odstraní zadanou hodnotu z daného rozsahu bez narušení pořadí zbývajících prvků a vrácení konce nového rozsahu, který neobsahuje zadanou hodnotu.|
|[remove_copy](../standard-library/algorithm-functions.md#remove_copy)|Zkopíruje prvky ze zdrojového rozsahu do cílového rozsahu. Prvky zadané hodnoty zkopírovány nejsou. Nenaruší pořadí zbývajících prvků a nevrátí konec nového cílového rozsahu.|
|[remove_copy_if](../standard-library/algorithm-functions.md#remove_copy_if)|Zkopíruje prvky ze zdrojového rozsahu do cílového rozsahu. Prvky splňující predikát zkopírovány nejsou. Nenaruší pořadí zbývajících prvků a nevrátí konec nového cílového rozsahu.|
|[remove_if](../standard-library/algorithm-functions.md#remove_if)|Odstraní prvky, které splňují predikát, z daného rozsahu bez narušení pořadí zbývajících prvků a vrácení konce nového rozsahu, který neobsahuje zadanou hodnotu.|
|[Nahradit](../standard-library/algorithm-functions.md#replace)|Zkontroluje každý prvek v rozsahu a nahradí jej, pokud odpovídá zadané hodnotě.|
|[replace_copy –](../standard-library/algorithm-functions.md#replace_copy)|Zkontroluje každý prvek ve zdrojovém rozsahu a nahradí jej, pokud při kopírování výsledku do nového cílového rozsahu odpovídá zadané hodnotě.|
|[replace_copy_if –](../standard-library/algorithm-functions.md#replace_copy_if)|Zkontroluje každý prvek ve zdrojovém rozsahu a nahradí jej, pokud při kopírování výsledku do nového cílového rozsahu splňuje zadaný predikát.|
|[replace_if –](../standard-library/algorithm-functions.md#replace_if)|Zkontroluje každý prvek v rozsahu a nahradí jej, pokud splňuje zadaný predikát.|
|[Reverse](../standard-library/algorithm-functions.md#reverse)|Obrátí pořadí prvků v rozsahu.|
|[reverse_copy –](../standard-library/algorithm-functions.md#reverse_copy)|Obrátí pořadí prvků ve zdrojovém rozsahu při kopírování do cílového rozsahu.|
|[Otočit](../standard-library/algorithm-functions.md#rotate)|Vymění prvky ve dvou sousedních rozsazích.|
|[rotate_copy –](../standard-library/algorithm-functions.md#rotate_copy)|Vymění prvky ve dvou sousedních rozsazích v rámci zdrojového rozsahu a zkopíruje výsledek do cílového rozsahu.|
|[search](../standard-library/algorithm-functions.md#search)|Vyhledá první výskyt sekvence v cílovém rozsahu, jejíž prvky jsou rovné prvkům v dané sekvenci prvků nebo jejíž prvky jsou ekvivalentní ve smyslu určeném binárním predikátem prvkům v dané sekvenci.|
|[search_n](../standard-library/algorithm-functions.md#search_n)|Vyhledá první dílčí sekvenci v rozsahu zadaného počtu prvků s konkrétní hodnotou nebo vztahem k dané hodnotě podle binárního predikátu.|
|[set_difference](../standard-library/algorithm-functions.md#set_difference)|Sjednotí všechny prvky, které patří do jednoho seřazeného zdrojového rozsahu, ale nikoli do druhého seřazeného zdrojového rozsahu, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.|
|[set_intersection](../standard-library/algorithm-functions.md#set_intersection)|Sjednotí všechny prvky, které náleží do obou seřazených zdrojových rozsahů, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.|
|[set_symmetric_difference](../standard-library/algorithm-functions.md#set_symmetric_difference)|Sjednotí všechny prvky, které náleží do jednoho, ale nikoli obou seřazených zdrojových rozsahů, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.|
|[set_union](../standard-library/algorithm-functions.md#set_union)|Sjednotí všechny prvky, které náleží alespoň do jednoho ze dvou seřazených zdrojových rozsahů, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.|
|[Řazení](../standard-library/algorithm-functions.md#sort)|Uspořádá prvky v zadaném rozsahu do nesestupného pořadí nebo podle setřiďovacího kritéria určeného binárním predikátem.|
|[náhodný výběr](../standard-library/algorithm-functions.md#shuffle)|Prvky podle okolí posouvá (změní uspořádání) pro zadaný rozsah pomocí generování náhodných čísel.|
|[sort_heap –](../standard-library/algorithm-functions.md#sort_heap)|Převede haldu na seřazený rozsah.|
|[stable_partition –](../standard-library/algorithm-functions.md#stable_partition)|Rozdělí prvky v rozsahu do dvou oddělených sad. Prvky, které splňují unární predikát, jsou umístěny před těmi, které jej nesplňují. Relativní pořadí ekvivalentních prvků je zachováno.|
|[stable_sort –](../standard-library/algorithm-functions.md#stable_sort)|Uspořádá prvky v zadaném rozsahu do nesestupného pořadí nebo podle setřiďovacího kritéria určeného binárním predikátem a zachová relativní pořadí ekvivalentních prvků.|
|[Swap](../standard-library/algorithm-functions.md#swap)|Vymění hodnoty prvků mezi dvěma typy objektů, obsah prvního objektu přiřadí ke druhému objektu a obsah druhého k prvnímu objektu.|
|[swap_ranges](../standard-library/algorithm-functions.md#swap_ranges)|Vymění prvky z jednoho rozsahu za prvky druhého rozsahu o stejné velikosti.|
|[Transformace](../standard-library/algorithm-functions.md#transform)|Aplikuje zadaný objekt funkce na každý prvek ve zdrojovém rozsahu nebo na dvojici prvků ze dvou zdrojových rozsahů a zkopíruje vrácené hodnoty objektu funkce do cílového rozsahu.|
|[Jedinečné](../standard-library/algorithm-functions.md#unique)|Odstraní duplicitní prvky, které v zadaném rozsahu sousedí.|
|[unique_copy](../standard-library/algorithm-functions.md#unique_copy)|Zkopíruje prvky ze zdrojového rozsahu do cílového rozsahu s výjimkou sousedících duplicitních prvků.|
|[upper_bound –](../standard-library/algorithm-functions.md#upper_bound)|Najde pozici prvního prvku v seřazeném rozsahu, který má hodnotu větší než zadaná hodnota, kde kritérium pořadí může být určeno binárním predikátem.|

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)<br/>
