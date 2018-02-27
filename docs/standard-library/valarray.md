---
title: "&lt;valarray –&gt; | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- <valarray>
dev_langs:
- C++
helpviewer_keywords:
- valarray header
ms.assetid: 30835415-21c1-4801-8f24-6bbef7dd8ecd
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 18cc075c2acb4b15c4131aa1926775d63d34928f
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/23/2018
---
# <a name="ltvalarraygt"></a>&lt;valarray&gt;
Definuje valarray – třídy šablony a množství podpůrné šablony třídy a funkce.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
#include <valarray>  
  
```  
  
## <a name="remarks"></a>Poznámky  
 Tyto šablony třídy a funkce nejsou povolené neobvyklou zeměpisnou šířku v zájmu lepší výkon. Konkrétně všechny funkce, které vrací typ **valarray –\<**T1 **>**  může vrátit objekt jiný typ T2. V takovém případě žádné funkce, které přijímá jeden nebo více argumentů typu **valarray –\<**T2 **>**  přetížení, které přijímají libovolné kombinace těchto argumentů, musí mít každý argument typu T2 nahrazen.  
  
### <a name="functions"></a>Funkce  
  
|||  
|-|-|  
|[Abs](../standard-library/valarray-functions.md#abs)|Funguje s prvky vstupní valarray – vrácení valarray –, jehož elementy jsou stejná jako absolutní hodnota elementů vstupní valarray –.|  
|[ACOS](../standard-library/valarray-functions.md#acos)|Funguje s prvky vstupní valarray – vrácení valarray –, jehož elementy jsou rovna Arkus kosinus elementy vstupní valarray –.|  
|[asin](../standard-library/valarray-functions.md#asin)|Funguje s prvky vstupní valarray – vrácení valarray –, jehož elementy jsou rovna Arkus sinus elementy vstupní valarray –.|  
|[atan](../standard-library/valarray-functions.md#atan)|Funguje s prvky vstupní valarray – vrácení valarray –, jehož elementy jsou stejné pro hlavní hodnotu Arkus tangens elementy vstupní valarray –.|  
|[atan2](../standard-library/valarray-functions.md#atan2)|Vrátí valarray –, jehož elementy jsou rovna Arkus tangens kartézských součásti určeného kombinací konstanty a elementy valarray – třídy.|  
|[Cos](../standard-library/valarray-functions.md#cos)|Funguje s prvky vstupní valarray – vrácení valarray –, jehož elementy jsou si rovny kosinu elementů vstupní valarray –.|  
|[cosh](../standard-library/valarray-functions.md#cosh)|Funguje s prvky vstupní valarray – vrácení valarray –, jehož elementy jsou rovna hyperbolický kosinus elementů vstupní valarray –.|  
|[exp](../standard-library/valarray-functions.md#exp)|Funguje s prvky vstupní valarray – vrácení valarray –, jehož elementy jsou si rovny exponenciální elementů vstupní valarray – fyzickým.|  
|[log](../standard-library/valarray-functions.md#log)|Funguje s prvky vstupní valarray – vrácení valarray –, jehož elementy jsou rovna přirozený logaritmus elementů vstupní valarray –.|  
|[log10](../standard-library/valarray-functions.md#log10)|Funguje s prvky vstupní valarray – vrácení valarray –, jehož elementy jsou stejné základní 10 nebo vypočítat dekadický logaritmus elementů vstupní valarray –.|  
|[pow](../standard-library/valarray-functions.md#pow)|Funguje s prvky vstupní valarray – třídy a konstanty, vrácení valarray –, jehož elementy jsou si rovny na základní buď elementy vstupní valarray – nebo konstantní umocněné exponentem zadán buď elementy vstupní valarray – nebo konstanta.|  
|[sin](../standard-library/valarray-functions.md#sin)|Funguje s prvky vstupní valarray – vrácení valarray –, jehož elementy jsou rovna sinus elementů vstupní valarray –.|  
|[sinh](../standard-library/valarray-functions.md#sinh)|Funguje s prvky vstupní valarray – vrácení valarray –, jehož elementy jsou rovna hyperbolický sinus elementů vstupní valarray –.|  
|[sqrt](../standard-library/valarray-functions.md#sqrt)|Funguje s prvky vstupní valarray – vrácení valarray –, jehož elementy jsou stejné pro druhou odmocninu elementů vstupní valarray –.|  
|[swap](../standard-library/valarray-functions.md#swap)||  
|[tan](../standard-library/valarray-functions.md#tan)|Funguje s prvky vstupní valarray – vrácení valarray –, jehož elementy jsou rovna tangens elementů vstupní valarray –.|  
|[tanh](../standard-library/valarray-functions.md#tanh)|Funguje s prvky vstupní valarray – vrácení valarray –, jehož elementy jsou rovna hyperbolický tangens elementy vstupní valarray –.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operator!=](../standard-library/valarray-operators.md#op_neq)|Testuje, jestli odpovídající elementy dva stejně velké valarray – třídy jsou různé nebo zda jsou všechny elementy valarray – nerovné zadanou hodnotu valarray – typ elementu.|  
|[operator%](../standard-library/valarray-operators.md#op_mod)|Získá zbytek po dělení odpovídající elementy dva stejně velké valarray – třídy nebo dělení valarray – zadaná hodnota valarray – element typu nebo dělení valarray – zadaná hodnota.|  
|[operator&](../standard-library/valarray-operators.md#op_amp)|Získá bitové hodnotě **a** mezi odpovídající elementy dva stejně velké valarray – třídy nebo valarray – a zadanou hodnotu typu prvku.|  
|[operator&&](../standard-library/valarray-operators.md#op_amp_amp)|Získá logické **a** mezi odpovídající elementy dva stejně velké valarray – třídy nebo valarray – a zadanou hodnotu valarray – element typu.|  
|[operator>](../standard-library/valarray-operators.md#op_gt)|Ověřuje, zda prvky jeden valarray – jsou větší než elementy stejně velké valarray – nebo zda jsou všechny elementy valarray – větší nebo menší než zadaná hodnota valarray – element typu.|  
|[operator>=](../standard-library/valarray-operators.md#op_gt_eq)|Ověřuje, zda prvky jeden valarray – jsou větší než nebo rovna hodnotě elementy stejně velké valarray – nebo jestli všechny elementy valarray – jsou větší než nebo rovno nebo menší než nebo roven zadané hodnotě.|  
|[operator>>](../standard-library/valarray-operators.md#op_gt_gt)|Posuny vpravo bits pro jednotlivé elementy valarray – po zadaný počet pozic nebo o element-wise částku určeného druhý valarray –.|  
|[operátor <](../standard-library/valarray-operators.md#op_lt)|Ověřuje, zda elementy jeden valarray – je nižší než elementy stejně velké valarray – nebo zda jsou všechny elementy valarray – větší nebo menší než zadanou hodnotou.|  
|[operator<=](../standard-library/valarray-operators.md#op_lt_eq)|Testuje, zda jsou elementy valarray – jeden, menší než nebo rovna hodnotě elementy stejně velké valarray – nebo zda všechny elementy valarray – jsou větší než nebo rovno nebo menší než nebo roven zadané hodnotě.|  
|[operátor <<](../standard-library/valarray-operators.md#op_lt_lt)|Levé posune bitů pro jednotlivé elementy valarray – po zadaný počet pozic nebo o element-wise částku určeného druhý valarray –.|  
|[operátor *](../standard-library/valarray-operators.md#op_star)|Získá element-wise produktu mezi odpovídající elementy dva stejně velké valarray – třídy nebo z mezi valarray – zadaná hodnota valarray – element typu.|  
|[operator+](../standard-library/valarray-operators.md#op_add)|Získá element-wise součet mezi odpovídající elementy dva stejně velké valarray – třídy nebo z mezi valarray – zadaná hodnota valarray – element typu.|  
|[operator-](../standard-library/valarray-operators.md#operator-)|Získá element-wise rozdíl mezi odpovídající elementy dva stejně velké valarray – třídy nebo z mezi valarray – zadaná hodnota valarray – element typu.|  
|[operátor nebo](../standard-library/valarray-operators.md#op_div)|Získá element-wise podílu mezi odpovídající elementy dva stejně velké valarray – třídy nebo z mezi valarray – zadaná hodnota valarray – element typu.|  
|[operator==](../standard-library/valarray-operators.md#op_eq_eq)|Testy, jestli odpovídající elementy dva stejně velké valarray – třídy jsou stejné, nebo zda jsou všechny elementy valarray – rovnat zadanou hodnotu valarray – typ elementu.|  
|[operator^](../standard-library/valarray-operators.md#op_xor)|Získá bitový exkluzivní `OR` mezi odpovídající elementy dva stejně velké valarray – třídy nebo valarray – a zadanou hodnotu typu prvku.|  
|[operator&#124;](../standard-library/valarray-operators.md#op_or)|Získá bitové hodnotě `OR` mezi odpovídající elementy dva stejně velké valarray – třídy nebo valarray – a zadanou hodnotu typu prvku.|  
|[operator&#124;&#124;](../standard-library/valarray-operators.md#op_lor)|Získá logické `OR` mezi odpovídající elementy dva stejně velké valarray – třídy nebo valarray – a zadanou hodnotu valarray – element typu.|  
  
### <a name="classes"></a>Třídy  
  
|||  
|-|-|  
|[gslice – třída](../standard-library/gslice-class.md)|Třída nástrojů k valarray –, který se používá k definování vícerozměrných řezy valarray –.|  
|[gslice_array – třída](../standard-library/gslice-array-class.md)|Třídu interní, pomocného šablony, která podporuje objekty obecné řez tím, že poskytuje mezi poli podmnožina definované obecné řezy valarray – operace.|  
|[indirect_array – třída](../standard-library/indirect-array-class.md)|Třída interní, pomocného šablony, která podporuje objekty, které jsou podmnožiny valarray – třídy tím, že poskytuje operace mezi poli podmnožina definované zadáním podmnožinu indexy valarray – nadřazené.|  
|[mask_array – třída](../standard-library/mask-array-class.md)|Třída interní, pomocného šablony, která podporuje objekty, které jsou podmnožiny nadřazené valarray – třídy, zadaný logický výraz, tím, že poskytuje operace mezi poli podmnožina.|  
|[slice – třída](../standard-library/slice-class.md)|Třída nástrojů k valarray –, který se používá k definování jednorozměrné, vector jako podmnožiny valarray –.|  
|[slice_array – třída](../standard-library/slice-array-class.md)|Třídu interní, pomocného šablony, která podporuje objekty řez tím, že poskytuje operace mezi poli podmnožina definované řezy valarray –.|  
|[valarray – třída](../standard-library/valarray-class.md)|Šablony třídy popisuje objekt, který určuje posloupnost elementy typu **typ** které jsou uloženy jako pole a určené pro provádění vysokorychlostní matematické operace, které jsou optimalizované pro výpočetní výkon.|  
  
### <a name="specializations"></a>Specializace  
  
|||  
|-|-|  
|[valarray –\<bool > – třída](../standard-library/valarray-bool-class.md)|Speciální verzi valarray – třídy šablony\<**typ**> na elementy typu `bool`.|  
  
## <a name="see-also"></a>Viz také  
 [Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)   
 [Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)



