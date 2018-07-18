---
title: '&lt;nové&gt; | Dokumentace Microsoftu'
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
ms.openlocfilehash: 03d4019f86f99c73ccb25c5cf570637dbf0d7753
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/11/2018
ms.locfileid: "38966499"
---
# <a name="ltnewgt"></a>&lt;new&gt;

Definuje několik typů a funkce ovládacího prvku přidělení a uvolnění úložiště v rámci řízení programu. Definuje také součásti pro vytváření sestav o chybách správu úložiště.

## <a name="syntax"></a>Syntaxe

```cpp
#include <new>

```

## <a name="remarks"></a>Poznámky

Některé funkce deklarované v této hlavičky jsou nahraditelné. Implementace poskytuje výchozí verzi, jejíž chování je popsaný v tomto dokumentu. Program můžete definovat však funkce se stejným podpisem nahradit výchozí verze v době spojení. Verze nahrazení musí splňovat požadavky popsané v tomto dokumentu.

### <a name="objects"></a>Objekty

|||
|-|-|
|[nothrow](../standard-library/new-functions.md#nothrow)|Poskytuje objekt pro použití jako argument **nothrow** verzích **nové** a **odstranit**.|

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[new_handler](../standard-library/new-typedefs.md#new_handler)|Typ, který odkazuje na funkci vhodný pro použití jako novou obslužnou rutinu.|

### <a name="functions"></a>Funkce

|Funkce|Popis|
|-|-|
|[set_new_handler](../standard-library/new-functions.md#set_new_handler)|Nainstaluje funkci uživatele, která se volá, když nové selže při jeho pokusu o přidělení paměti.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[delete – operátor](../standard-library/new-operators.md#op_delete)|Funkci volanou třídou výraz delete se zrušit přidělení úložiště pro jednotlivé objekty.|
|[delete – operátor&#91;&#93;](../standard-library/new-operators.md#op_delete_arr)|Funkci volanou třídou výraz delete se zrušit přidělení úložiště pro pole objektů.|
|[new – operátor](../standard-library/new-operators.md#op_new)|Funkci volanou třídou výraz new k přidělení úložiště pro jednotlivé objekty.|
|[new – operátor&#91;&#93;](../standard-library/new-operators.md#op_new_arr)|Funkci volanou třídou výraz new k přidělení úložiště pro pole objektů.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[bad_alloc – třída](../standard-library/bad-alloc-class.md)|Tato třída popisuje výjimku vyvolanou k označení, že požadavek na přidělení nebylo úspěšné.|
|[nothrow_t – třída](../standard-library/nothrow-t-structure.md)|Třída se používá jako parametr funkce operátoru nové k označení, že funkce by měla vrátit ukazatel s hodnotou null pro sestavy k selhání přidělení, spíše než výjimku.|

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
