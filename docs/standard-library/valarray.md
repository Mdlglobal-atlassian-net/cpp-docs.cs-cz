---
title: '&lt;valarray&gt;'
ms.date: 11/04/2016
f1_keywords:
- <valarray>
helpviewer_keywords:
- valarray header
ms.assetid: 30835415-21c1-4801-8f24-6bbef7dd8ecd
ms.openlocfilehash: 8b8118722d7219e3b30e11ad67411595c3dc36ad
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62365413"
---
# <a name="ltvalarraygt"></a>&lt;valarray&gt;

Definuje valarray – třída šablony a mnoho podpůrných tříd šablon a funkcí.

## <a name="syntax"></a>Syntaxe

```cpp
#include <valarray>
```

## <a name="remarks"></a>Poznámky

Tyto šablony třídy a funkce jsou povolené neobvyklé zeměpisná šířka v zájmu vylepšení výkonu. Konkrétně, všechny funkce vracející typ `valarray<T1>` může vrátit objekt nějakého jiného typu T2. V takovém případě všechny funkce, které přijímá jeden nebo více argumentů typu `valarray<T2>` musí mít přetížení, které přijímají kombinací libovolné z těchto argumentů, každý nahrazeno argument typu T2.

### <a name="functions"></a>Funkce

|Funkce|Popis|
|-|-|
|[abs](../standard-library/valarray-functions.md#abs)|Prvky vstupní valarray – vrácení valarray, jehož prvky jsou rovné absolutní hodnota prvků vstupní valarray pracuje.|
|[acos](../standard-library/valarray-functions.md#acos)|Prvky vstupní valarray – vrácení valarray, jehož prvky jsou rovné Arkus kosinus prvků vstupní valarray pracuje.|
|[asin](../standard-library/valarray-functions.md#asin)|Prvky vstupní valarray – vrácení valarray, jehož prvky jsou rovné Arkus sinus prvků vstupní valarray pracuje.|
|[atan](../standard-library/valarray-functions.md#atan)|Prvky vstupní valarray – vrácení valarray, jehož prvky jsou rovné hlavní hodnotu Arkus tangens prvků vstupní valarray pracuje.|
|[atan2](../standard-library/valarray-functions.md#atan2)|Vrátí valarray, jehož prvky jsou rovné Arkus tangens Kartézském součástí určených kombinaci konstanty a prvky valarrays.|
|[cos](../standard-library/valarray-functions.md#cos)|Prvky vstupní valarray – vrácení valarray, jehož prvky jsou rovné kosinus prvků vstupní valarray pracuje.|
|[cosh](../standard-library/valarray-functions.md#cosh)|Prvky vstupní valarray – vrácení valarray, jehož prvky jsou rovné hyperbolický kosinus hodnoty prvků vstupní valarray pracuje.|
|[exp](../standard-library/valarray-functions.md#exp)|Funguje na prvcích vstupní valarray – vrácení valarray, jehož prvky jsou rovné exponenciální prvků vstupní valarray přirozený.|
|[log](../standard-library/valarray-functions.md#log)|Prvky vstupní valarray – vrácení valarray, jehož prvky jsou rovné přirozený logaritmus prvků vstupní valarray pracuje.|
|[log10](../standard-library/valarray-functions.md#log10)|Prvky vstupní valarray – vrácení valarray, jehož prvky jsou rovné základní 10 nebo vypočítat dekadický logaritmus prvků vstupní valarray pracuje.|
|[Pow](../standard-library/valarray-functions.md#pow)|Funguje na prvcích vstupní valarrays a konstanty vrací valarray, jehož prvky jsou rovné základní zadané buď prvků vstupní valarray nebo konstantu umocněné na exponent zadané buď prvků vstupní valarray nebo Toto je konstanta.|
|[sin](../standard-library/valarray-functions.md#sin)|Prvky vstupní valarray – vrácení valarray, jehož prvky jsou rovné sinus prvků vstupní valarray pracuje.|
|[sinh](../standard-library/valarray-functions.md#sinh)|Prvky vstupní valarray – vrácení valarray, jehož prvky jsou rovné hyperbolický sinus prvků vstupní valarray pracuje.|
|[sqrt](../standard-library/valarray-functions.md#sqrt)|Prvky vstupní valarray – vrácení valarray, jehož prvky jsou rovné druhou odmocninu prvků vstupní valarray pracuje.|
|[swap](../standard-library/valarray-functions.md#swap)||
|[Tan](../standard-library/valarray-functions.md#tan)|Prvky vstupní valarray – vrácení valarray, jehož prvky jsou rovné tangens hodnoty prvků vstupní valarray pracuje.|
|[tanh](../standard-library/valarray-functions.md#tanh)|Prvky vstupní valarray – vrácení valarray, jehož prvky jsou rovné hyperbolický tangens hodnoty prvků vstupní valarray pracuje.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operator!=](../standard-library/valarray-operators.md#op_neq)|Testuje, jestli odpovídající prvky dvou stejně velké valarrays nestejné nebo zda jsou všechny prvky valarray – nerovné zadaná hodnota valarray typ elementu.|
|[% – operátor](../standard-library/valarray-operators.md#op_mod)|Získá zbytek po dělení odpovídající prvky dva stejně velké valarrays nebo dělení valarray zadanou hodnotou typ prvku valarray nebo dělení valarray zadanou hodnotu.|
|[operátor &](../standard-library/valarray-operators.md#op_amp)|Získá bitový `AND` mezi odpovídající prvky dvou valarrays stejně velké nebo valarray a určitou hodnotu na typ prvku.|
|[Operator & &](../standard-library/valarray-operators.md#op_amp_amp)|Získá logickou `AND` mezi odpovídající prvky dvou valarrays stejně velké nebo valarray a určitou hodnotu valarray element typu.|
|[operator>](../standard-library/valarray-operators.md#op_gt)|Ověřuje, zda prvky jeden valarray jsou větší než prvky stejně velké valarray nebo zda jsou všechny prvky valarray větší nebo menší než zadaná hodnota valarray typ elementu.|
|[operator>=](../standard-library/valarray-operators.md#op_gt_eq)|Ověřuje, zda jsou elementy jeden valarray větší než nebo rovna hodnotě prvky stejně velké valarray nebo určuje, zda všechny prvky valarray jsou větší než nebo rovno nebo menší než nebo rovna zadané hodnotě.|
|[operator>>](../standard-library/valarray-operators.md#op_gt_gt)|Posuny doprava bity pro každý prvek valarray zadaný počet pozic, nebo částku element-wise určené druhý valarray.|
|[Operator <](../standard-library/valarray-operators.md#op_lt)|Ověřuje, zda prvky valarray – jeden je menší než prvky stejně velké valarray nebo zda jsou všechny prvky valarray větší nebo menší než zadanou hodnotou.|
|[operator<=](../standard-library/valarray-operators.md#op_lt_eq)|Testuje, jestli prvky jeden valarray jsou menší než nebo rovna hodnotě elementy stejně velké valarray nebo zda všechny prvky valarray jsou větší než nebo rovno nebo menší než nebo rovna zadané hodnotě.|
|[operátor <<](../standard-library/valarray-operators.md#op_lt_lt)|Vlevo posune bitů pro každý prvek valarray zadaný počet pozic, nebo částku element-wise určené druhý valarray.|
|[Operator *](../standard-library/valarray-operators.md#op_star)|Získá produktu mezi odpovídající elementy ve dva stejně velké valarrays nebo mezi valarray – zadaná hodnota valarray typ elementu.|
|[Operator +](../standard-library/valarray-operators.md#op_add)|Získá element-wise součet mezi odpovídající elementy ve dva stejně velké valarrays nebo mezi valarray – zadaná hodnota valarray typ elementu.|
|[Operator-](../standard-library/valarray-operators.md#operator-)|Získá element-wise rozdíl mezi odpovídající elementy ve dva stejně velké valarrays nebo mezi valarray – zadaná hodnota valarray typ elementu.|
|[Operator /](../standard-library/valarray-operators.md#op_div)|Získá element-wise podíl mezi odpovídající elementy ve dva stejně velké valarrays nebo mezi valarray – zadaná hodnota valarray typ elementu.|
|[operator==](../standard-library/valarray-operators.md#op_eq_eq)|Testy, zda odpovídající prvky dvou stejně velké valarrays se rovná nebo zda jsou všechny prvky valarray rovnat zadaná hodnota valarray typ elementu.|
|[operátor ^](../standard-library/valarray-operators.md#op_xor)|Získá bitový exkluzivní `OR` mezi odpovídající prvky dvou valarrays stejně velké nebo valarray a určitou hodnotu na typ prvku.|
|[operator&#124;](../standard-library/valarray-operators.md#op_or)|Získá bitový `OR` mezi odpovídající prvky dvou valarrays stejně velké nebo valarray a určitou hodnotu na typ prvku.|
|[operator&#124;&#124;](../standard-library/valarray-operators.md#op_lor)|Získá logickou `OR` mezi odpovídající prvky dvou valarrays stejně velké nebo valarray a určitou hodnotu valarray element typu.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[gslice – třída](../standard-library/gslice-class.md)|Třídy nástrojů pro valarray –, který se používá k definování multidimenzionální řezů valarray.|
|[gslice_array – třída](../standard-library/gslice-array-class.md)|Interní, pomocné šablony třídy, který podporuje obecné řez objektů zadáním mezi dílčí pole určené obecné řezu valarray – operace.|
|[indirect_array – třída](../standard-library/indirect-array-class.md)|Třída interní, pomocné šablony, která podporuje objekty, které jsou podmnožinou tohoto valarrays tím, že poskytuje operace mezi dílčí pole definovaná zadáním podmnožinu indexy valarray nadřazené.|
|[mask_array – třída](../standard-library/mask-array-class.md)|Třída interní, pomocné šablony, která podporuje objekty, které jsou podmnožinou tohoto nadřazeného valarrays zadaným logický výraz, tím, že poskytuje operace mezi podmnožinu polí.|
|[slice – třída](../standard-library/slice-class.md)|Třídy nástrojů pro valarray –, který se používá k definování jednorozměrné, jako vektor podmnožiny valarray.|
|[slice_array – třída](../standard-library/slice-array-class.md)|Třída interní, pomocné šablony, která podporuje objekty řez tím, že poskytuje operace mezi dílčí pole určené řezu valarray –.|
|[valarray – třída](../standard-library/valarray-class.md)|Třída šablony popisuje objekt, který řídí sekvence elementů typu `Type` , které jsou uloženy jako pole a navržené pro provádění vysokorychlostní matematických operací, které jsou optimalizované pro výpočetní výkon.|

### <a name="specializations"></a>Specializace

|||
|-|-|
|[valarray\<bool> Class](../standard-library/valarray-bool-class.md)|Specializované verze valarray – třída šablony\<**typ**> k elementům typu **bool**.|

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
