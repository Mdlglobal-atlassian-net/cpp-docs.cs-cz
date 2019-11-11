---
title: algoritmus &lt;&gt;
ms.date: 11/04/2016
f1_keywords:
- <algorithm>
helpviewer_keywords:
- algorithm header [C++]
- C++ Standard Library, algorithms
- <algorithm> header
ms.assetid: 19f97711-7a67-4a65-8fd1-9a2bd3ca327d
ms.openlocfilehash: f72969052ae3ecc0d9fb88382e1560c846e2167c
ms.sourcegitcommit: eb254b4462a58d219376ff501bf768bd1adc07ae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/11/2019
ms.locfileid: "73912893"
---
# <a name="ltalgorithmgt"></a>algoritmus &lt;&gt;

Definuje C++ standardní funkce šablon kontejneru, které provádějí algoritmy.

## <a name="syntax"></a>Syntaxe

```cpp
(see relevant links below for specific algorithm syntax)
```

> [!NOTE]
> \<algoritmus > Library také používá příkaz `#include <initializer_list>`.

## <a name="remarks"></a>Poznámky

C++ Standardní algoritmy knihovny jsou obecné, protože mohou pracovat na různých datových strukturách. Datové struktury, na kterých mohou fungovat, zahrnují nejen C++ standardní třídy kontejneru knihovny, například `vector` a `list`, ale také programové datové struktury a pole prvků, které splňují požadavky konkrétního algoritmu. C++Algoritmy standardní knihovny dosahují této úrovně obecného přístupem k prvkům kontejneru a jejich procházení nepřímo prostřednictvím iterátorů.

C++Algoritmy standardní knihovny mají rozsahy iterátoru, které jsou obvykle určeny počáteční nebo koncovou polohou. Tyto rozsahy musí být platné v tom smyslu, že na všechny ukazatele v rozsazích musí být možné nepřímo odkazovat a v rámci sekvencí každého rozsahu musí být poslední pozice dosažitelná z první pomocí přírůstku.

C++ Standardní algoritmy knihovny rozšíří akce podporované operacemi a členskými funkcemi každého C++ kontejneru standardních knihoven a umožňují práci, například s různými typy objektů kontejnerů současně. K předání informací o účelu algoritmů byly použity dvě přípony.

- Přípona `_if` označuje, že algoritmus je použit s objekty funkce, které pracují na hodnotách prvků, nikoli na samotných prvcích. Algoritmus `find_if` vyhledává prvky, jejichž hodnoty neodpovídají kritériu určenému objektem funkce, a algoritmus `find` vyhledává konkrétní hodnotu.

- Přípona „_copy“ označuje, že algoritmus nejen manipuluje s hodnotami prvků, ale také kopíruje změněné hodnoty do cílového rozsahu. Algoritmus `reverse` obrátí pořadí prvků v rozsahu a algoritmus `reverse_copy` také zkopíruje výsledek do cílového rozsahu.

C++Algoritmy standardní knihovny jsou často klasifikované do skupin, které označují něco o jejich účelu nebo požadavcích. Mezi ně patří modifikace algoritmů, které mění hodnotu prvků v porovnání s nezměněnými algoritmy, které nemění. Mutující algoritmy mění pořadí prvků, ale nikoli jejich hodnoty. Odebírající algoritmy mohou odstranit prvky z rozsahu nebo rozsah zkopírovat. Řazení algoritmů přeuspořádání prvků v rozsahu v různých způsobech a algoritmy seřazených rozsahů se chovají pouze v rozsahu, jehož prvky byly seřazeny určitým způsobem.

Číselné C++ algoritmy standardní knihovny, které jsou k dispozici pro numerické zpracování, mají vlastní hlavičkový soubor [\<číselná >](../standard-library/numeric.md)a objekty funkcí a adaptéry jsou definovány v záhlaví [\<funkčních](../standard-library/functional.md) objektech funkcí >, které vracejí logické hodnoty, jsou označovány jako predikáty. Výchozím binárním predikátem je `operator<`porovnání. Seřazované prvky musí být obecně menší než srovnatelné, což znamená, že když jsou uvedeny dva prvky, může být stanoveno, zda jsou ekvivalentní (v tom smyslu, že ani jeden není menší než ten druhý), nebo zda jeden je menší než druhý. Výsledkem je řazení mezi neekvivalentními prvky.

### <a name="function-templates"></a>Šablony funkcí

|||
|-|-|
|[adjacent_find](../standard-library/algorithm-functions.md#adjacent_find)|Vyhledá dva sousedící prvky, které jsou buď rovny, nebo splňují zadanou podmínku.|
|[all_of](../standard-library/algorithm-functions.md#all_of)|Vrátí **hodnotu pravda** , pokud je podmínka přítomna na každém prvku v daném rozsahu.|
|[any_of](../standard-library/algorithm-functions.md#any_of)|Vrátí **hodnotu pravda** , pokud je v zadaném rozsahu prvků alespoň jednou podmínka přítomna.|
|[binary_search](../standard-library/algorithm-functions.md#binary_search)|Ověřuje, zda v seřazeném rozsahu existuje prvek, který je roven zadané hodnotě nebo je jí ekvivalentní ve smyslu určeném binárním predikátem.|
|[Clamp](../standard-library/algorithm-functions.md#clamp)||
|[kopií](../standard-library/algorithm-functions.md#copy)|Přiřadí hodnoty prvků ze zdrojového rozsahu do cílového rozsahu a provede iterace přes zdrojové sekvence prvků a přiřadí je novým pozicím směrem dopředu.|
|[copy_backward](../standard-library/algorithm-functions.md#copy_backward)|Přiřadí hodnoty prvků ze zdrojového rozsahu do cílového rozsahu a provede iterace přes zdrojové sekvence prvků a přiřadí je novým pozicím směrem dozadu.|
|[copy_if](../standard-library/algorithm-functions.md#copy_if)|Kopírovat všechny prvky v daném rozsahu, které pro zadanou podmínku testují test na **hodnotu true**|
|[copy_n](../standard-library/algorithm-functions.md#copy_n)|Zkopíruje zadaný počet prvků.|
|[výpočtu](../standard-library/algorithm-functions.md#count)|Vrátí počet prvků v rozsahu, jejichž hodnoty odpovídají zadané hodnotě.|
|[count_if](../standard-library/algorithm-functions.md#count_if)|Vrátí počet prvků v rozsahu, jejichž hodnoty odpovídají zadané podmínce.|
|[výši](../standard-library/algorithm-functions.md#equal)|Porovná dva rozsahy prvek podle prvku buď ke zjištění rovnosti, nebo ekvivalentnosti ve smyslu určeném binárním predikátem.|
|[equal_range](../standard-library/algorithm-functions.md#equal_range)|Najde dvojici pozic v seřazeném rozsahu. První bude menší nebo rovna pozici zadaného prvku a druhá větší než pozice prvku, kde smysl ekvivalence nebo řazení použitý k určení pozic v sekvenci může být určen binárním predikátem.|
|[vyplnění](../standard-library/algorithm-functions.md#fill)|Každému prvku v zadaném rozsahu přiřadí stejnou novou hodnotu.|
|[fill_n](../standard-library/algorithm-functions.md#fill_n)|Přiřadí novou hodnotu zadanému počtu prvků v rozsahu, který začíná konkrétním prvkem.|
|[najít](../standard-library/algorithm-functions.md#find)|Vyhledá pozici prvního výskytu prvku v rozsahu, který má zadanou hodnotu.|
|[find_end](../standard-library/algorithm-functions.md#find_end)|Vyhledá v rozsahu poslední dílčí sekvenci, která je shodná se zadanou sekvencí nebo která je ekvivalentní ve smyslu určeném binárním predikátem.|
|[find_first_of](../standard-library/algorithm-functions.md#find_first_of)|Vyhledá první výskyt jedné z několika hodnot v cílovém rozsahu nebo první výskyt jednoho z několika prvků, které jsou ekvivalentní ve smyslu určeném binárním predikátem zadané sadě prvků.|
|[find_if](../standard-library/algorithm-functions.md#find_if)|Vyhledá pozici prvního výskytu prvku v rozsahu, který splňuje zadanou podmínku.|
|[find_if_not](../standard-library/algorithm-functions.md#find_if_not)|Vrátí první prvek v zadaném rozsahu, který nesplňuje podmínku.|
|[for_each](../standard-library/algorithm-functions.md#for_each)|Na každý prvek v pořadí dopředu v rozsahu použije zadaný objekt funkce a vrátí objekt funkce.|
|[for_each_n](../standard-library/algorithm-functions.md#for_each_n)||
|[vytváří](../standard-library/algorithm-functions.md#generate)|Přiřadí hodnoty generované objektem funkce každému prvku v rozsahu.|
|[generate_n](../standard-library/algorithm-functions.md#generate_n)|Přiřadí hodnoty generované objektem funkce zadanému počtu prvků v rozsahu a vrátí pozici prvku za poslední přiřazenou hodnotou.|
|[zahrnující](../standard-library/algorithm-functions.md#includes)|Ověřuje, zda jeden seřazený rozsah obsahuje všechny prvky obsažené ve druhém seřazeném rozsahu, kde kritérium pořadí nebo ekvivalence mezi prvky může být určeno binárním predikátem.|
|[inplace_merge](../standard-library/algorithm-functions.md#inplace_merge)|Kombinuje prvky ze dvou po sobě následujících seřazených rozsahů do jednoho seřazeného rozsahu, kde kritérium pořadí může být určeno binárním predikátem.|
|[is_heap](../standard-library/algorithm-functions.md#is_heap)|Vrátí **hodnotu true** , pokud prvky v zadaném rozsahu tvoří haldu.|
|[is_heap_until](../standard-library/algorithm-functions.md#is_heap_until)|Vrátí **hodnotu true** , pokud zadaný rozsah tvoří haldu do posledního prvku.|
|[is_partitioned](../standard-library/algorithm-functions.md#is_partitioned)|Vrátí **hodnotu true** , pokud všechny prvky v zadaném rozsahu, které testuje **hodnotu true** pro podmínku, předcházejí všem prvkům, které testují **false**.|
|[is_permutation](../standard-library/algorithm-functions.md#is_permutation)|Určuje, zda prvky v daném rozsahu tvoří platnou permutaci.|
|[is_sorted](../standard-library/algorithm-functions.md#is_sorted)|Vrátí **hodnotu true** , pokud prvky v zadaném rozsahu jsou v seřazeném pořadí.|
|[is_sorted_until](../standard-library/algorithm-functions.md#is_sorted_until)|Vrátí **hodnotu true** , pokud prvky v zadaném rozsahu jsou v seřazeném pořadí.|
|[iter_swap](../standard-library/algorithm-functions.md#iter_swap)|Vymění dvě hodnoty odkazované dvojicí zadaných iterátorů.|
|[lexicographical_compare](../standard-library/algorithm-functions.md#lexicographical_compare)|Porovná prvek po prvku mezi dvěma sekvencemi k určení, která z nich je menší.|
|[lower_bound](../standard-library/algorithm-functions.md#lower_bound)|Najde pozici prvního prvku v seřazeném rozsahu, jehož hodnota je větší nebo rovna zadané hodnotě, kde kritérium pořadí může být určeno primárním predikátem.|
|[make_heap](../standard-library/algorithm-functions.md#make_heap)|Převede prvky ze zadaného rozsahu do haldy, ve které je první prvek největší a pro kterou může být kritérium řazení určeno binárním predikátem.|
|[počet](../standard-library/algorithm-functions.md#max)|Porovná dva objekty a vrátí větší z nich, kde kritérium pořadí může být určeno binárním predikátem.|
|[max_element](../standard-library/algorithm-functions.md#max_element)|Vyhledá první výskyt největšího prvku v zadaném rozsahu, kde kritérium pořadí může být určeno binárním predikátem.|
|[sloučení](../standard-library/algorithm-functions.md#merge)|Kombinuje všechny prvky ze dvou po sobě seřazených zdrojových rozsahů do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.|
|[dlouhé](../standard-library/algorithm-functions.md#min)|Porovná dva objekty a vrátí menší z nich, kde kritérium pořadí může být určeno binárním predikátem.|
|[min_element](../standard-library/algorithm-functions.md#min_element)|Vyhledá první výskyt nejmenšího prvku v zadaném rozsahu, kde kritérium pořadí může být určeno binárním predikátem.|
|[minmax](../standard-library/algorithm-functions.md#minmax)|Porovná dva vstupní parametry a vrátí je jako dvojici v pořadí od nejmenšího po největší.|
|[minmax_element](../standard-library/algorithm-functions.md#minmax_element)|Provede práci prováděnou [Min_element](../standard-library/algorithm-functions.md#min_element) a [max_element](../standard-library/algorithm-functions.md#max_element) v jednom volání.|
|[shod](../standard-library/algorithm-functions.md#mismatch)|Porovná dva rozsahy prvek po prvku buď ke zjištění rovnosti, nebo ekvivalence ve smyslu určeném binárním predikátem a vyhledá první pozici, kde existuje rozdíl.|
|[přesunout &lt;ALG&gt;](../standard-library/algorithm-functions.md#alg_move)|Přesune prvky přidružené k určenému rozsahu.|
|[move_backward](../standard-library/algorithm-functions.md#move_backward)|Přesune prvky jednoho iterátoru do druhého. Pohyb začíná posledním prvkem v daném rozsahu a končí prvním prvkem v daném rozsahu.|
|[next_permutation](../standard-library/algorithm-functions.md#next_permutation)|Znovu uspořádá prvky v rozsahu tak, aby původní pořadí bylo nahrazeno lexikograficky následující větší permutací, pokud existuje, kde význam následujícího může být určen binárním predikátem.|
|[none_of](../standard-library/algorithm-functions.md#none_of)|Vrátí **hodnotu pravda** , pokud není podmínka nikdy obsažena v rámci prvků v daném rozsahu.|
|[nth_element](../standard-library/algorithm-functions.md#nth_element)|Rozdělí rozsah prvků na oddíly a správně vyhledá *n*-tý prvek sekvence v rozsahu tak, aby všechny prvky před ním byly menší nebo rovny hodnotě a všechny prvky, které následují v sekvenci, jsou větší než nebo rovny.|
|[partial_sort](../standard-library/algorithm-functions.md#partial_sort)|Uspořádá zadaný počet menších prvků v rozsahu do nesestupného pořadí nebo podle setřiďovacího kritéria určeného binárním predikátem.|
|[partial_sort_copy](../standard-library/algorithm-functions.md#partial_sort_copy)|Zkopíruje prvky ze zdrojového rozsahu do cílového rozsahu, kde zdrojové prvky jsou seřazeny buď podle binárního predikátu „menší než“ nebo jiného určeného binárního predikátu.|
|[rozdělován](../standard-library/algorithm-functions.md#partition)|Rozdělí prvky v rozsahu do dvou oddělených sad. Prvky, které splňují unární predikát, jsou umístěny před těmi, které jej nesplňují.|
|[partition_copy](../standard-library/algorithm-functions.md#partition_copy)|Zkopíruje prvky, pro které je podmínka **pravdivá** , do jednoho cíle a pro který je podmínka **NEPRAVDA** , na druhou. Prvky musí pocházet ze zadaného rozsahu.|
|[partition_point](../standard-library/algorithm-functions.md#partition_point)|Vrátí první prvek v zadaném rozsahu, který nesplňuje podmínku. Prvky jsou seřazeny tak, aby ty, které splňují podmínku, předcházely těm, které ji nesplňují.|
|[pop_heap](../standard-library/algorithm-functions.md#pop_heap)|Odstraní největší prvek z přední části haldy až do předposlední pozice v rozsahu a ze zbývajících prvků vytvoří novou haldu.|
|[prev_permutation](../standard-library/algorithm-functions.md#prev_permutation)|Znovu uspořádá prvky v rozsahu tak, aby původní pořadí bylo nahrazeno lexikograficky následující větší permutací, pokud existuje, kde význam následujícího může být určen binárním predikátem.|
|[push_heap](../standard-library/algorithm-functions.md#push_heap)|Přidá prvek, který je na konci rozsahu, do stávající haldy, která zahrnuje předchozí prvky daného rozsahu.|
|[random_shuffle](../standard-library/algorithm-functions.md#random_shuffle)|Změní uspořádání sekvence *N* prvků v rozsahu na jednu z *n*! možné postupy vybrané náhodně.|
|[remove](../standard-library/algorithm-functions.md#remove)|Odstraní zadanou hodnotu z daného rozsahu bez narušení pořadí zbývajících prvků a vrácení konce nového rozsahu, který neobsahuje zadanou hodnotu.|
|[remove_copy](../standard-library/algorithm-functions.md#remove_copy)|Zkopíruje prvky ze zdrojového rozsahu do cílového rozsahu. Prvky zadané hodnoty zkopírovány nejsou. Nenaruší pořadí zbývajících prvků a nevrátí konec nového cílového rozsahu.|
|[remove_copy_if](../standard-library/algorithm-functions.md#remove_copy_if)|Zkopíruje prvky ze zdrojového rozsahu do cílového rozsahu. Prvky splňující predikát zkopírovány nejsou. Nenaruší pořadí zbývajících prvků a nevrátí konec nového cílového rozsahu.|
|[remove_if](../standard-library/algorithm-functions.md#remove_if)|Odstraní prvky, které splňují predikát, z daného rozsahu bez narušení pořadí zbývajících prvků a vrácení konce nového rozsahu, který neobsahuje zadanou hodnotu.|
|[náhrady](../standard-library/algorithm-functions.md#replace)|Zkontroluje každý prvek v rozsahu a nahradí jej, pokud odpovídá zadané hodnotě.|
|[replace_copy](../standard-library/algorithm-functions.md#replace_copy)|Zkontroluje každý prvek ve zdrojovém rozsahu a nahradí jej, pokud při kopírování výsledku do nového cílového rozsahu odpovídá zadané hodnotě.|
|[replace_copy_if](../standard-library/algorithm-functions.md#replace_copy_if)|Zkontroluje každý prvek ve zdrojovém rozsahu a nahradí jej, pokud při kopírování výsledku do nového cílového rozsahu splňuje zadaný predikát.|
|[replace_if](../standard-library/algorithm-functions.md#replace_if)|Zkontroluje každý prvek v rozsahu a nahradí jej, pokud splňuje zadaný predikát.|
|[zpět](../standard-library/algorithm-functions.md#reverse)|Obrátí pořadí prvků v rozsahu.|
|[reverse_copy](../standard-library/algorithm-functions.md#reverse_copy)|Obrátí pořadí prvků ve zdrojovém rozsahu při kopírování do cílového rozsahu.|
|[před](../standard-library/algorithm-functions.md#rotate)|Vymění prvky ve dvou sousedních rozsazích.|
|[rotate_copy](../standard-library/algorithm-functions.md#rotate_copy)|Vymění prvky ve dvou sousedních rozsazích v rámci zdrojového rozsahu a zkopíruje výsledek do cílového rozsahu.|
|[vzorku](../standard-library/algorithm-functions.md#sample)||
|[nápovědě](../standard-library/algorithm-functions.md#search)|Vyhledá první výskyt sekvence v cílovém rozsahu, jejíž prvky jsou rovné prvkům v dané sekvenci prvků nebo jejíž prvky jsou ekvivalentní ve smyslu určeném binárním predikátem prvkům v dané sekvenci.|
|[search_n](../standard-library/algorithm-functions.md#search_n)|Vyhledá první dílčí sekvenci v rozsahu zadaného počtu prvků s konkrétní hodnotou nebo vztahem k dané hodnotě podle binárního predikátu.|
|[set_difference](../standard-library/algorithm-functions.md#set_difference)|Sjednotí všechny prvky, které patří do jednoho seřazeného zdrojového rozsahu, ale nikoli do druhého seřazeného zdrojového rozsahu, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.|
|[set_intersection](../standard-library/algorithm-functions.md#set_intersection)|Sjednotí všechny prvky, které náleží do obou seřazených zdrojových rozsahů, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.|
|[set_symmetric_difference](../standard-library/algorithm-functions.md#set_symmetric_difference)|Sjednotí všechny prvky, které náleží do jednoho, ale nikoli obou seřazených zdrojových rozsahů, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.|
|[set_union](../standard-library/algorithm-functions.md#set_union)|Sjednotí všechny prvky, které náleží alespoň do jednoho ze dvou seřazených zdrojových rozsahů, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.|
|[druhu](../standard-library/algorithm-functions.md#sort)|Uspořádá prvky v zadaném rozsahu do nesestupného pořadí nebo podle setřiďovacího kritéria určeného binárním predikátem.|
|[náhodný](../standard-library/algorithm-functions.md#shuffle)|Rozmístí prvky pro daný rozsah pomocí generátoru náhodných čísel (mění uspořádání).|
|[sort_heap](../standard-library/algorithm-functions.md#sort_heap)|Převede haldu na seřazený rozsah.|
|[stable_partition](../standard-library/algorithm-functions.md#stable_partition)|Rozdělí prvky v rozsahu do dvou oddělených sad. Prvky, které splňují unární predikát, jsou umístěny před těmi, které jej nesplňují. Relativní pořadí ekvivalentních prvků je zachováno.|
|[stable_sort](../standard-library/algorithm-functions.md#stable_sort)|Uspořádá prvky v zadaném rozsahu do nesestupného pořadí nebo podle setřiďovacího kritéria určeného binárním predikátem a zachová relativní pořadí ekvivalentních prvků.|
|[adresu](../standard-library/algorithm-functions.md#swap)|Vymění hodnoty prvků mezi dvěma typy objektů, obsah prvního objektu přiřadí ke druhému objektu a obsah druhého k prvnímu objektu.|
|[swap_ranges](../standard-library/algorithm-functions.md#swap_ranges)|Vymění prvky z jednoho rozsahu za prvky druhého rozsahu o stejné velikosti.|
|[převedení](../standard-library/algorithm-functions.md#transform)|Aplikuje zadaný objekt funkce na každý prvek ve zdrojovém rozsahu nebo na dvojici prvků ze dvou zdrojových rozsahů a zkopíruje vrácené hodnoty objektu funkce do cílového rozsahu.|
|[unique](../standard-library/algorithm-functions.md#unique)|Odstraní duplicitní prvky, které v zadaném rozsahu sousedí.|
|[unique_copy](../standard-library/algorithm-functions.md#unique_copy)|Zkopíruje prvky ze zdrojového rozsahu do cílového rozsahu s výjimkou sousedících duplicitních prvků.|
|[upper_bound](../standard-library/algorithm-functions.md#upper_bound)|Najde pozici prvního prvku v seřazeném rozsahu, který má hodnotu větší než zadaná hodnota, kde kritérium pořadí může být určeno binárním predikátem.|

## <a name="see-also"></a>Viz také:

\ [referenčních souborů hlaviček](../standard-library/cpp-standard-library-header-files.md)
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md) \
[Standardní knihovna C++ – referenční dokumentace](../standard-library/cpp-standard-library-reference.md)
