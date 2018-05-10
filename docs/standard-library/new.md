---
title: '&lt;nové&gt; | Microsoft Docs'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- <new>
dev_langs:
- C++
helpviewer_keywords:
- new header
ms.assetid: 218e2a15-34e8-4ef3-9122-1e90eccf8559
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2039da5462d360648f83ebd8890de2f2beba884
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="ltnewgt"></a>&lt;new&gt;

Definuje několik typy a funkce tohoto ovládacího prvku přidělení a uvolnění úložiště pod kontrolou programu. Definuje také součásti pro vytváření sestav o chybách správu úložiště.

## <a name="syntax"></a>Syntaxe

```cpp
#include <new>

```

## <a name="remarks"></a>Poznámky

Některé funkce, které jsou deklarované v této hlavičky jsou nahraditelné. Implementace poskytuje výchozí verze, jehož chování je popsaný v tomto dokumentu. Program může, ale taky definovat funkce se stejným podpisem nahradit výchozí verze v době spojení. Verze nahrazení musí splňovat požadavky popsané v tomto dokumentu.

### <a name="objects"></a>Objekty

|||
|-|-|
|[nothrow](../standard-library/new-functions.md#nothrow)|Poskytuje objekt, který se má použít jako argument `nothrow` verze **nové** a **odstranit**.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[new_handler](../standard-library/new-typedefs.md#new_handler)|Typ, který odkazuje na funkci vhodné pro použití jako novou obslužnou rutinu.|

### <a name="functions"></a>Funkce

|Funkce|Popis|
|-|-|
|[set_new_handler](../standard-library/new-functions.md#set_new_handler)|Nainstaluje funkci uživatele, která je volána, když nové selže při jeho pokusu o přidělení paměti.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[delete – operátor](../standard-library/new-operators.md#op_delete)|Odstranění výrazem se zrušit přidělení úložiště pro jednotlivé objekty volaná funkce.|
|[delete – operátor&#91;&#93;](../standard-library/new-operators.md#op_delete_arr)|Funkci nazvanou odstranění výrazem se zrušit přidělení úložiště pro pole objektů.|
|[new – operátor](../standard-library/new-operators.md#op_new)|Funkci nazvanou nové výrazem se přidělit úložiště pro jednotlivé objekty.|
|[new – operátor&#91;&#93;](../standard-library/new-operators.md#op_new_arr)|Funkci nazvanou nové výrazem se přidělit úložiště pro pole objektů.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[bad_alloc – třída](../standard-library/bad-alloc-class.md)|Třída popisuje výjimka vyvolaná indikující, že žádost o přidělení nebylo úspěšné.|
|[nothrow_t – třída](../standard-library/nothrow-t-structure.md)|Třída se používá jako parametr funkce pro operátor nové indikující, že funkce by měla vrátit ukazatele null do sestavy došlo k chybě přidělení, nikoli výjimku.|

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
