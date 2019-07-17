---
title: '&lt;new&gt;'
ms.date: 11/04/2016
f1_keywords:
- <new>
helpviewer_keywords:
- new header
ms.assetid: 218e2a15-34e8-4ef3-9122-1e90eccf8559
ms.openlocfilehash: bc873f278461fcdc6dbb42e7c968c691e3dc7f73
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68243552"
---
# <a name="ltnewgt"></a>&lt;new&gt;

Definuje několik typů a funkce ovládacího prvku přidělení a uvolnění úložiště v rámci řízení programu. Definuje také součásti pro vytváření sestav o chybách správu úložiště.

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<nový >

**Namespace:** std

## <a name="remarks"></a>Poznámky

Některé funkce deklarované v této hlavičky jsou nahraditelné. Implementace poskytuje výchozí verzi, jejíž chování je popsaný v tomto dokumentu. Program můžete definovat však funkce se stejným podpisem nahradit výchozí verze v době spojení. Verze nahrazení musí splňovat požadavky popsané v tomto dokumentu.

## <a name="members"></a>Členové

### <a name="objects"></a>Objekty

|||
|-|-|
|[nothrow](../standard-library/new-functions.md#nothrow)|Poskytuje objekt pro použití jako argument **nothrow** verzích **nové** a **odstranit**.|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[new_handler](../standard-library/new-typedefs.md#new_handler)|Typ, který odkazuje na funkci vhodný pro použití jako novou obslužnou rutinu.|
|[hardware_constructive_interference_size](../standard-library/new-typedefs.md#hardware_destructive_interference_size)||
|[hardware_destructive_interference_size](../standard-library/new-typedefs.md#hardware_destructive_interference_size)||

### <a name="functions"></a>Funkce

|||
|-|-|
|[get_new_handler](../standard-library/new-functions.md#get_new_handler)||
|[praní](../standard-library/new-functions.md#launder)||
|[set_new_handler](../standard-library/new-functions.md#set_new_handler)|Nainstaluje funkci uživatele, která se volá, když nové selže při jeho pokusu o přidělení paměti.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[delete – operátor](../standard-library/new-operators.md#op_delete)|Funkci volanou třídou výraz delete se zrušit přidělení úložiště pro jednotlivé objekty.|
|[delete – operátor&#91;&#93;](../standard-library/new-operators.md#op_delete_arr)|Funkci volanou třídou výraz delete se zrušit přidělení úložiště pro pole objektů.|
|[new – operátor](../standard-library/new-operators.md#op_new)|Funkci volanou třídou výraz new k přidělení úložiště pro jednotlivé objekty.|
|[new – operátor&#91;&#93;](../standard-library/new-operators.md#op_new_arr)|Funkci volanou třídou výraz new k přidělení úložiště pro pole objektů.|

### <a name="enums"></a>Výčty

|||
|-|-|
|[align_val_t](../standard-library/new-operators.md#op_align_val_t)||

### <a name="classes"></a>Třídy

|||
|-|-|
|[bad_alloc – třída](../standard-library/bad-alloc-class.md)|Tato třída popisuje výjimku vyvolanou k označení, že požadavek na přidělení nebylo úspěšné.|
|[bad_array_new_length třídy](../standard-library/bad-array-new-length.md)||
|[nothrow_t – třída](../standard-library/nothrow-t-structure.md)|Třída se používá jako parametr funkce operátoru nové k označení, že funkce by měla vrátit ukazatel s hodnotou null pro sestavy k selhání přidělení, spíše než výjimku.|

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
