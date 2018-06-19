---
title: '&lt;iomanip –&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- iomanip/std::<iomanip>
- <iomanip>
dev_langs:
- C++
helpviewer_keywords:
- iomanip header
ms.assetid: 3681c346-4763-4037-bba4-cf0dc3447974
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9a410dae35771d89b9d9ae72c8221501f051d10e
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33846568"
---
# <a name="ltiomanipgt"></a>&lt;iomanip –&gt;

Zahrnout `iostreams` standardní hlavičku \<iomanip – > zadat několik manipulátory, že každý trvat jeden argument.

## <a name="syntax"></a>Syntaxe

```cpp
#include <iomanip>

```

## <a name="remarks"></a>Poznámky

Každá z těchto manipulátory vrátí neurčeného typu, nazývá **T1** prostřednictvím **T10**, které obě přetížení `basic_istream` \< **Elem**, **Tr**>`::`[operátor >>](../standard-library/istream-operators.md#op_gt_gt) a `basic_ostream` \< **Elem**, **Tr** > `::` [operátor <<](../standard-library/ostream-operators.md#op_lt_lt).

### <a name="manipulators"></a>Manipulátory

|||
|-|-|
|[get_money](../standard-library/iomanip-functions.md#iomanip_get_money)|Získá peněžní částku, volitelně v mezinárodním formátu.|
|[get_time](../standard-library/iomanip-functions.md#iomanip_get_time)|Získá čas ve struktuře čas pomocí zadaného formátu.|
|[put_money](../standard-library/iomanip-functions.md#iomanip_put_money)|Poskytuje peněžní částku, volitelně v mezinárodním formátu.|
|[put_time](../standard-library/iomanip-functions.md#iomanip_put_time)|Poskytuje na čas ve struktura časové a řetězec formátu k použití.|
|[v uvozovkách](../standard-library/iomanip-functions.md#quoted)|Umožňuje pohodlný odezvy řetězců s operátory vložení a extrakce.|
|[resetiosflags](../standard-library/iomanip-functions.md#resetiosflags)|Vymaže zadané příznaky.|
|[setbase](../standard-library/iomanip-functions.md#setbase)|Nastavte základ pro celá čísla.|
|[setfill](../standard-library/iomanip-functions.md#setfill)|Nastaví znak, který se použije k vyplnění mezer v zobrazení se zarovnané vpravo.|
|[setiosflags](../standard-library/iomanip-functions.md#setiosflags)|Nastaví zadaný příznaků.|
|[setprecision](../standard-library/iomanip-functions.md#setprecision)|Nastaví přesnost pro hodnoty s plovoucí desetinnou čárkou.|
|[setw](../standard-library/iomanip-functions.md#setw)|Určuje šířku pole zobrazení.|

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
[iostream – programování](../standard-library/iostream-programming.md)<br/>
[iostreams – konvence](../standard-library/iostreams-conventions.md)<br/>
