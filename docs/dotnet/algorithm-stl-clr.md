---
title: algoritmus (STL/CLR) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: <cliext/algorithm>
dev_langs: C++
helpviewer_keywords:
- algorithm functions [STL/CLR]
- <algorithm> header [STL/CLR]
- <cliext/algorithm> header [STL/CLR]
ms.assetid: ee2718dc-a98d-40b8-8341-593fe7d2ac15
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a1f598b0aba0f5f697fc6603728e2735f0cd50f6
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="algorithm-stlclr"></a>algorithm (STL/CLR)
Definuje funkce šablony kontejneru STL/CLR, které provádět algoritmy.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#include <cliext/algorithm>  
```  
  
## <a name="functions"></a>Funkce  
  
|Funkce|Popis|  
|--------------|-----------------|  
|[adjacent_find – (STL/CLR)](../dotnet/adjacent-find-stl-clr.md)|Vyhledá dva přiléhající prvky, které jsou stejné.|  
|[binary_search – (STL/CLR)](../dotnet/binary-search-stl-clr.md)|Ověřuje, zda je seřazená posloupnost obsahuje danou hodnotou.|  
|[kopírování (STL/CLR)](../dotnet/copy-stl-clr.md)|Kopie hodnoty z rozsahu zdrojového na cílový rozsah, iterace směrem vpřed.|  
|[copy_backward – (STL/CLR)](../dotnet/copy-backward-stl-clr.md)|Zkopíruje hodnoty z zdrojový rozsah na cílový rozsah, iterace v zpětně směru.|  
|[Count (STL/CLR)](../dotnet/count-stl-clr.md)|Vrátí počet prvků v rozsahu, jejichž hodnoty odpovídají zadané hodnotě.|  
|[count_if – (STL/CLR)](../dotnet/count-if-stl-clr.md)|Vrátí počet prvků v rozsahu, jejichž hodnoty odpovídají zadané podmínce.|  
|[EQUAL (STL/CLR)](../dotnet/equal-stl-clr.md)|Porovná dva rozsahy, elementu pomocí elementu.|  
|[equal_range – (STL/CLR)](../dotnet/equal-range-stl-clr.md)|Vyhledá seřazené posloupnosti hodnot a vrátí dvě místa, které vymezují dalším hodnot, které jsou na stejné úrovni pro daný element.|  
|[Fill (STL/CLR)](../dotnet/fill-stl-clr.md)|Každému prvku v zadaném rozsahu přiřadí stejnou novou hodnotu.|  
|[fill_n (STL/CLR)](../dotnet/fill-n-stl-clr.md)|Přiřadí novou hodnotu na zadaný počet elementů v rozsahu od jazyka.|  
|[Najít (STL/CLR)](../dotnet/find-stl-clr.md)|Vrátí pozici prvního výskytu zadané hodnoty.|  
|[find_end – (STL/CLR)](../dotnet/find-end-stl-clr.md)|Vrátí poslední dalším rozsah, který je stejný jako do zadaného pořadí.|  
|[find_first_of – (STL/CLR)](../dotnet/find-first-of-stl-clr.md)|Vyhledá v rozsahu pro první výskyt některého z daného rozsahu prvků.|  
|[find_if – (STL/CLR)](../dotnet/find-if-stl-clr.md)|Vrátí pozici první prvek v pořadí hodnot, kde element splňuje zadanou podmínku.|  
|[for_each – (STL/CLR)](../dotnet/for-each-stl-clr.md)|Objekt zadaný funkce se vztahuje na každý prvek v pořadí hodnot a vrátí objekt funkce.|  
|[Generovat (STL/CLR)](../dotnet/generate-stl-clr.md)|Přiřadí hodnoty generované objekt funkce pro každý prvek v pořadí hodnot.|  
|[generate_n – (STL/CLR)](../dotnet/generate-n-stl-clr.md)|Přiřadí hodnoty generované funkce objektu na zadaný počet elementů.|  
|[zahrnuje (STL/CLR)](../dotnet/includes-stl-clr.md)|Ověřuje, zda jeden seřazené rozsah obsahuje všechny elementy v druhé seřazená.|  
|[inplace_merge (STL/CLR)](../dotnet/inplace-merge-stl-clr.md)|Spojuje elementy ze dvou po sobě jdoucích seřazené rozsahy do jednoho seřazené oblasti.|  
|[iter_swap – (STL/CLR)](../dotnet/iter-swap-stl-clr.md)|Vymění dvě hodnoty odkazované dvojicí zadaných iterátorů.|  
|[lexicographical_compare – (STL/CLR)](../dotnet/lexicographical-compare-stl-clr.md)|Porovná dvě pořadí, ve elementu, identifikace, které pořadí je menší dvou.|  
|[lower_bound – (STL/CLR)](../dotnet/lower-bound-stl-clr.md)|Vyhledá pozici prvním elementem v seřazené posloupnosti hodnoty, který má hodnotu větší než nebo rovna zadané hodnotě.|  
|[make_heap – (STL/CLR)](../dotnet/make-heap-stl-clr.md)|Převede elementy ze zadaného rozsahu haldy, kde je největší prvním elementem v haldě.|  
|[maximální počet (STL/CLR)](../dotnet/max-stl-clr.md)|Porovná dva objekty a vrátí delší než dva.|  
|[max_element – (STL/CLR)](../dotnet/max-element-stl-clr.md)|Vyhledá nejvyšší element v zadané pořadí hodnot.|  
|[Merge (STL/CLR)](../dotnet/merge-stl-clr.md)|Spojuje všechny elementy ze dvou oblastí seřazené zdroje do jednoho, seřazené cílový rozsah.|  
|[min (STL/CLR)](../dotnet/min-stl-clr.md)|Porovná dva objekty a vrátí menší dvou.|  
|[min_element – (STL/CLR)](../dotnet/min-element-stl-clr.md)|Vyhledá nejnižší element v zadané pořadí hodnot.|  
|[Neshoda (STL/CLR)](../dotnet/mismatch-stl-clr.md)|Porovná dva rozsahy elementu pomocí elementu a vrátí první pozici, kde dochází k rozdíl.|  
|[next_permutation (STL/CLR)](../dotnet/next-permutation-stl-clr.md)|Změní elementy v rozsahu, takže původní řazení lexicographically další větší Permutace nahrazuje, pokud existuje.|  
|[nth_element (STL/CLR)](../dotnet/nth-element-stl-clr.md)|Oddíly pořadí elementů správně hledání `n`element TD pořadí tak, aby všechny elementy úrovních před ním jsou menší než nebo rovna ho a všechny prvky, které na něho kliknout, jsou větší než nebo rovna hodnotě ho.|  
|[partial_sort (STL/CLR)](../dotnet/partial-sort-stl-clr.md)|Zadaný počet v rozsahu menší elementy uspořádány nondescending pořadí.|  
|[partial_sort_copy (STL/CLR)](../dotnet/partial-sort-copy-stl-clr.md)|Zkopíruje elementy ze zdrojový rozsah do cílový rozsah tak, aby elementy ze rozsah zdrojových seřazeni.|  
|[oddíl (STL/CLR)](../dotnet/partition-stl-clr.md)|Elementy v rozsahu uspořádá tak, aby tyto prvky, které splňují unárního predikátu předcházet ty, které nesplňují ho.|  
|[pop_heap – (STL/CLR)](../dotnet/pop-heap-stl-clr.md)|Přesune největší element zpředu haldy na konec a pak forms nové haldy z zbývající elementů.|  
|[prev_permutation – (STL/CLR)](../dotnet/prev-permutation-stl-clr.md)|Změní pořadí elementů tak, aby původní řazení lexicographically předchozí větší Permutace nahrazuje, pokud existuje.|  
|[push_heap – (STL/CLR)](../dotnet/push-heap-stl-clr.md)|Přidá prvek, který je na konci rozsahu, do stávající haldy, která zahrnuje předchozí prvky daného rozsahu.|  
|[random_shuffle (STL/CLR)](../dotnet/random-shuffle-stl-clr.md)|Přeuspořádá posloupnost `N` elementy v rozsahu do jedné ze `N`! možné uspořádání náhodně vybrané.|  
|[odebrat (STL/CLR)](../dotnet/remove-stl-clr.md)|Odstraní zadanou hodnotu z daného rozsahu bez narušení pořadí zbývající elementy a vrátí konec bezplatné zadaná hodnota nový rozsah.|  
|[remove_copy – (STL/CLR)](../dotnet/remove-copy-stl-clr.md)|Zkopíruje elementy z zdrojový rozsah cílový rozsah, s tím rozdílem, že nejsou zkopírovali elementy zadané hodnoty, bez narušení pořadí zbývající prvků.|  
|[remove_copy_if – (STL/CLR)](../dotnet/remove-copy-if-stl-clr.md)|Kopie elementů od zdrojový rozsah cílový rozsah, kromě těch, které splňují predikátu, bez narušení pořadí zbývající prvků.|  
|[remove_if – (STL/CLR)](../dotnet/remove-if-stl-clr.md)|Odstraní prvky, které splňují predikát z daného rozsahu bez narušení pořadí zbývající prvků. .|  
|[Nahraďte (STL/CLR)](../dotnet/replace-stl-clr.md)|Nahradí elementy v rozsahu, které odpovídají zadané hodnotě s novou hodnotou.|  
|[replace_copy – (STL/CLR)](../dotnet/replace-copy-stl-clr.md)|Zkopíruje elementy z rozsah zdrojových na cílový rozsah, nahraďte elementy, které odpovídají zadané hodnotě s novou hodnotou.|  
|[replace_copy_if – (STL/CLR)](../dotnet/replace-copy-if-stl-clr.md)|Zkontroluje každý prvek ve zdrojovém rozsahu a nahradí jej, pokud při kopírování výsledku do nového cílového rozsahu splňuje zadaný predikát.|  
|[replace_if – (STL/CLR)](../dotnet/replace-if-stl-clr.md)|Zkontroluje každý prvek v rozsahu a nahradí jej, pokud splňuje zadaný predikát.|  
|[reverse (STL/CLR)](../dotnet/reverse-stl-clr.md)|Obrátí pořadí prvků v rozsahu.|  
|[reverse_copy – (STL/CLR)](../dotnet/reverse-copy-stl-clr.md)|Obrátí pořadí prvků v rámci zdrojový rozsah při kopírování do cílové oblasti.|  
|[Otočit (STL/CLR)](../dotnet/rotate-stl-clr.md)|Vymění prvky ve dvou sousedních rozsazích.|  
|[rotate_copy – (STL/CLR)](../dotnet/rotate-copy-stl-clr.md)|Vymění prvky ve dvou sousedních rozsazích v rámci zdrojového rozsahu a zkopíruje výsledek do cílového rozsahu.|  
|[vyhledávání (STL/CLR)](../dotnet/search-stl-clr.md)|Vyhledá první výskyt sekvence v cílovém rozsahu, jejíž prvky jsou rovné prvkům v dané sekvenci prvků nebo jejíž prvky jsou ekvivalentní ve smyslu určeném binárním predikátem prvkům v dané sekvenci.|  
|[search_n – (STL/CLR)](../dotnet/search-n-stl-clr.md)|Vyhledá první dílčí sekvenci v rozsahu zadaného počtu prvků s konkrétní hodnotou nebo vztahem k dané hodnotě podle binárního predikátu.|  
|[set_difference – (STL/CLR)](../dotnet/set-difference-stl-clr.md)|Sjednotí všechny prvky, které patří do jednoho seřazeného zdrojového rozsahu, ale nikoli do druhého seřazeného zdrojového rozsahu, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.|  
|[set_intersection – (STL/CLR)](../dotnet/set-intersection-stl-clr.md)|Sjednotí všechny prvky, které náleží do obou seřazených zdrojových rozsahů, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.|  
|[set_symmetric_difference – (STL/CLR)](../dotnet/set-symmetric-difference-stl-clr.md)|Sjednotí všechny prvky, které náleží do jednoho, ale nikoli obou seřazených zdrojových rozsahů, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.|  
|[set_union – (STL/CLR)](../dotnet/set-union-stl-clr.md)|Sjednotí všechny prvky, které náleží alespoň do jednoho ze dvou seřazených zdrojových rozsahů, do jednoho seřazeného cílového rozsahu, kde kritérium pořadí může být určeno binárním predikátem.|  
|[řazení (STL/CLR)](../dotnet/sort-stl-clr.md)|Uspořádá prvky v zadaném rozsahu do nesestupného pořadí nebo podle setřiďovacího kritéria určeného binárním predikátem.|  
|[sort_heap – (STL/CLR)](../dotnet/sort-heap-stl-clr.md)|Převede haldu na seřazený rozsah.|  
|[stable_partition – (STL/CLR)](../dotnet/stable-partition-stl-clr.md)|Rozdělí prvky v rozsahu do dvou oddělených sad. Prvky, které splňují unární predikát, jsou umístěny před těmi, které jej nesplňují. Relativní pořadí ekvivalentních prvků je zachováno.|  
|[stable_sort – (STL/CLR)](../dotnet/stable-sort-stl-clr.md)|Uspořádá prvky v zadaném rozsahu do nesestupného pořadí nebo podle setřiďovacího kritéria určeného binárním predikátem a zachová relativní pořadí ekvivalentních prvků.|  
|[swap (STL/CLR)](../dotnet/swap-stl-clr.md)|Vymění hodnoty prvků mezi dvěma typy objektů, obsah prvního objektu přiřadí ke druhému objektu a obsah druhého k prvnímu objektu.|  
|[swap_ranges – (STL/CLR)](../dotnet/swap-ranges-stl-clr.md)|Vymění prvky z jednoho rozsahu za prvky druhého rozsahu o stejné velikosti.|  
|[transformace (STL/CLR)](../dotnet/transform-stl-clr.md)|Aplikuje zadaný objekt funkce na každý prvek ve zdrojovém rozsahu nebo na dvojici prvků ze dvou zdrojových rozsahů a zkopíruje vrácené hodnoty objektu funkce do cílového rozsahu.|  
|[jedinečné (STL/CLR)](../dotnet/unique-stl-clr.md)|Odstraní duplicitní prvky, které v zadaném rozsahu sousedí.|  
|[unique_copy – (STL/CLR)](../dotnet/unique-copy-stl-clr.md)|Zkopíruje prvky ze zdrojového rozsahu do cílového rozsahu s výjimkou sousedících duplicitních prvků.|  
|[upper_bound – (STL/CLR)](../dotnet/upper-bound-stl-clr.md)|Najde pozici prvního prvku v seřazeném rozsahu, který má hodnotu větší než zadaná hodnota, kde kritérium pořadí může být určeno binárním predikátem.|  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** \<cliext – / algoritmus >  
  
 **Namespace:** cliext –  
  
## <a name="see-also"></a>Viz také  
 [Referenční příručka knihovny STL/CLR](../dotnet/stl-clr-library-reference.md)