---
title: '&lt;valarray&gt;'
ms.date: 11/04/2016
f1_keywords:
- <valarray>
helpviewer_keywords:
- valarray header
ms.assetid: 30835415-21c1-4801-8f24-6bbef7dd8ecd
ms.openlocfilehash: c18b72017e4999e377bf8575f624f8fdda5b0caf
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68448339"
---
# <a name="ltvalarraygt"></a>&lt;valarray&gt;

Definuje třídu šablony valarray a mnoho podporovaných tříd a funkcí šablon.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<valarray >

**Obor názvů:** std

> [!NOTE]
> Knihovna \<> valarray používá příkaz #include < initializer_list >.

## <a name="remarks"></a>Poznámky

Tyto třídy a funkce šablon jsou povolené v zájmu lepšího výkonu neobvyklá Zeměpisná šířka. Konkrétně jakákoli funkce vracející typ `valarray<T1>` může vracet objekt jiného typu T2. V takovém případě všechny funkce, které akceptují jeden nebo více argumentů `valarray<T2>` typu, musí mít přetížení, která přijímají libovolné kombinace těchto argumentů, každý nahrazen argumentem typu T2.

## <a name="members"></a>Členové

### <a name="functions"></a>Funkce

|||
|-|-|
|[abs](../standard-library/valarray-functions.md#abs)|Funguje na prvcích vstupního valarray a vrátí valarray, jehož prvky jsou rovny absolutní hodnotě prvků vstupního valarray.|
|[acos](../standard-library/valarray-functions.md#acos)|Funguje na prvcích vstupního valarray a vrátí valarray, jehož prvky jsou rovny Arkus kosinus prvků vstupního valarray.|
|[ASIN](../standard-library/valarray-functions.md#asin)|Funguje na prvcích vstupního valarray a vrátí valarray, jehož prvky jsou rovny Arkus sinus prvků vstupního valarray.|
|[atan](../standard-library/valarray-functions.md#atan)|Funguje na prvcích vstupního valarray a vrátí valarray, jehož prvky jsou rovny hodnotě objektu zabezpečení arkustangens prvků vstupního valarray.|
|[atan2](../standard-library/valarray-functions.md#atan2)|Vrátí valarray, jehož prvky jsou rovny arkustangens prvků kartézském určených kombinací konstant a prvků valarrays.|
|[ifunctiondiscovery](../standard-library/valarray-functions.md#begin)||
|[Cos](../standard-library/valarray-functions.md#cos)|Funguje na prvcích vstupního valarray a vrátí valarray, jehož prvky jsou rovny kosinus prvků vstupního valarray.|
|[cosh](../standard-library/valarray-functions.md#cosh)|Funguje na prvcích vstupního valarray a vrátí valarray, jehož prvky jsou rovny hyperbolický kosinus prvků vstupního valarray.|
|[účelu](../standard-library/valarray-functions.md#end)||
|[exp](../standard-library/valarray-functions.md#exp)|Funguje na prvcích vstupního valarray a vrátí valarray, jehož prvky jsou rovny přirozenému exponenciálnímu exponenciálnímu z prvků vstupního valarray.|
|[protokolu](../standard-library/valarray-functions.md#log)|Funguje na prvcích vstupního valarray a vrátí valarray, jehož prvky jsou rovny přirozenému logaritmu prvků vstupního valarray.|
|[log10](../standard-library/valarray-functions.md#log10)|Funguje na prvcích vstupního valarray a vrátí valarray, jehož prvky jsou rovny základnímu 10 nebo běžnému logaritmu prvků vstupního valarray.|
|[log](../standard-library/valarray-functions.md#pow)|Funguje na prvcích vstupních valarrays a konstant a vrátí valarray, jehož prvky jsou rovny základ určenému elementy vstupního valarray nebo konstantou umocněnou na exponent zadaný buď prvky vstupního valarray nebo a. změnil.|
|[tlačítek](../standard-library/valarray-functions.md#sin)|Funguje na prvcích vstupního valarray a vrátí valarray, jehož prvky jsou rovny sinus prvků vstupního valarray.|
|[sinh –](../standard-library/valarray-functions.md#sinh)|Funguje na prvcích vstupního valarray a vrátí valarray, jehož prvky jsou rovny hyperbolickýmu sinus prvků vstupního valarray.|
|[sqrt](../standard-library/valarray-functions.md#sqrt)|Funguje na prvcích vstupního valarray a vrátí valarray, jehož prvky jsou rovny čtvercové odmocnině prvků vstupního valarray.|
|[swap](../standard-library/valarray-functions.md#swap)||
|[nádrž](../standard-library/valarray-functions.md#tan)|Funguje na prvcích vstupního valarray a vrátí valarray, jehož prvky jsou rovny tangens prvků vstupního valarray.|
|[tanh –](../standard-library/valarray-functions.md#tanh)|Funguje na prvcích vstupního valarray a vrátí valarray, jehož prvky jsou rovny hyperbolický tangens prvků vstupního valarray.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[operator!=](../standard-library/valarray-operators.md#op_neq)|Testuje, zda odpovídající prvky dvou velikostí valarrays jsou nerovné nebo zda všechny prvky valarray nejsou rovny zadané hodnotě typu elementu valarray.|
|[podnikatel](../standard-library/valarray-operators.md#op_mod)|Získá zbytek dělení odpovídajících prvků dvou stejně velkých valarrays nebo rozdělení valarray na zadanou hodnotu typu elementu valarray nebo rozdělení zadané hodnoty pomocí valarrayu ().|
|[operátor &](../standard-library/valarray-operators.md#op_amp)|Získá bitovou `AND` kopii mezi odpovídajícími prvky dvou stejně velkých valarrays nebo mezi valarray a zadanou hodnotou typu prvku.|
|[operátor & &](../standard-library/valarray-operators.md#op_amp_amp)|Získá logickou `AND` hodnotu mezi odpovídajícími prvky ve dvou stejně velkých valarrays nebo mezi valarray a zadanou hodnotou typu elementu valarray.|
|[operátor >](../standard-library/valarray-operators.md#op_gt)|Testuje, zda prvky jednoho valarray jsou větší než prvky stejné velikosti valarray nebo zda jsou všechny prvky valarray větší nebo menší než zadaná hodnota typu prvku valarray.|
|[operator>=](../standard-library/valarray-operators.md#op_gt_eq)|Testuje, zda prvky jednoho valarray jsou větší než nebo rovny prvkům valarray stejné velikosti nebo zda jsou všechny prvky valarray větší nebo rovny zadané hodnotě.|
|[operátor > >](../standard-library/valarray-operators.md#op_gt_gt)|Posune pravou část bitů pro každý prvek valarray o zadaný počet pozic nebo o hodnotu v rámci prvku určenou druhým valarray.|
|[operátor <](../standard-library/valarray-operators.md#op_lt)|Testuje, zda jsou prvky jednoho valarray menší než prvky stejné velikosti valarray, nebo zda jsou všechny prvky valarray větší nebo menší než zadaná hodnota.|
|[operátor < =](../standard-library/valarray-operators.md#op_lt_eq)|Testuje, zda jsou prvky jednoho valarray menší nebo rovny prvkům valarray stejné velikosti, nebo zda jsou všechny prvky valarray větší nebo rovny hodnotě nebo menší než zadaná hodnota.|
|[operátor < <](../standard-library/valarray-operators.md#op_lt_lt)|Levý posune bity pro každý prvek valarray o zadaný počet pozic nebo o požadovanou hodnotu prvku určenou druhým valarray.|
|[podnikatel](../standard-library/valarray-operators.md#op_star)|Získá produkt z prvku, který je v souladu s odpovídajícími prvky dvou stejně velkých valarrays nebo mezi valarray a zadanou hodnotou typu elementu valarray.|
|[operator + – operátor](../standard-library/valarray-operators.md#op_add)|Získá poměrnou hodnotu mezi odpovídajícími prvky dvou stejně velkých valarrays nebo mezi valarray a zadanou hodnotou typu elementu valarray.|
|[podnikatel](../standard-library/valarray-operators.md#operator-)|Získá rozdíl mezi odpovídajícími prvky ze dvou odpovídajících prvků se stejnou velikostí valarrays nebo mezi valarray a zadanou hodnotou typu elementu valarray.|
|[podnikatel](../standard-library/valarray-operators.md#op_div)|Získá poměr podílu mezi odpovídajícími prvky dvou stejně velkých valarrays nebo mezi valarray a zadanou hodnotou typu elementu valarray.|
|[operator==](../standard-library/valarray-operators.md#op_eq_eq)|Testuje, zda odpovídající prvky dvou velikostí valarrays jsou stejné nebo zda všechny prvky valarray mají stejnou hodnotu jako typ elementu valarray.|
|[operátor ^](../standard-library/valarray-operators.md#op_xor)|Získá bitovou výlučnou `OR` hodnotu mezi odpovídajícími prvky dvou stejně velkých valarrays nebo mezi valarray a zadanou hodnotou typu prvku.|
|[operator&#124;](../standard-library/valarray-operators.md#op_or)|Získá bitovou `OR` kopii mezi odpovídajícími prvky dvou stejně velkých valarrays nebo mezi valarray a zadanou hodnotou typu prvku.|
|[operator&#124;&#124;](../standard-library/valarray-operators.md#op_lor)|Získá logickou `OR` hodnotu mezi odpovídajícími prvky ve dvou stejně velkých valarrays nebo mezi valarray a zadanou hodnotou typu elementu valarray.|

### <a name="classes"></a>Třídy

|||
|-|-|
|[gslice – třída](../standard-library/gslice-class.md)|Třída nástrojů pro valarray, která slouží k definování multidimenzionálních řezů valarray.|
|[gslice_array – třída](../standard-library/gslice-array-class.md)|Interní pomocná třída šablony, která podporuje obecné objekty řezů tím, že poskytuje operace mezi podmnožinami, které jsou definovány v obecné výseči valarray.|
|[indirect_array – třída](../standard-library/indirect-array-class.md)|Interní pomocná třída šablony, která podporuje objekty, které jsou podmnožinou valarrays, poskytováním operací mezi poli podmnožiny, které jsou definovány určením podmnožiny indexů nadřazené valarray.|
|[mask_array – třída](../standard-library/mask-array-class.md)|Interní pomocná třída šablony, která podporuje objekty, které jsou podmnožinou nadřazených valarrays, určené s logickým výrazem, poskytnutím operací mezi poli podmnožiny.|
|[slice – třída](../standard-library/slice-class.md)|Třída nástrojů pro valarray, která slouží k definování jednorozměrného, vektorového podmnožiny valarray.|
|[slice_array – třída](../standard-library/slice-array-class.md)|Interní pomocná třída šablony, která podporuje objekty řezu tím, že poskytuje operace mezi podmnožinou polí definovaných v řezu valarray.|
|[valarray – třída](../standard-library/valarray-class.md)|Třída šablony popisuje objekt, který řídí sekvenci prvků typu `Type` , které jsou uloženy jako pole a jsou určeny pro provádění vysokorychlostních matematických operací optimalizovaných pro výpočetní výkon.|

### <a name="specializations"></a>Specializace

|||
|-|-|
|[valarray\<bool > – třída](../standard-library/valarray-bool-class.md)|Specializovaná verze třídy Template valarray\<**typu**> k prvkům typu **bool**.|

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
