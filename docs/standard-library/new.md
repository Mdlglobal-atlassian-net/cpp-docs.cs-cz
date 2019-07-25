---
title: '&lt;new&gt;'
ms.date: 11/04/2016
f1_keywords:
- <new>
helpviewer_keywords:
- new header
ms.assetid: 218e2a15-34e8-4ef3-9122-1e90eccf8559
ms.openlocfilehash: 6155a89c9cbba67ce27253aa64ff70ca7871e748
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457679"
---
# <a name="ltnewgt"></a>&lt;new&gt;

Definuje několik typů a funkcí, které řídí přidělování a uvolňování úložiště v rámci řízení programu. Také definuje součásti pro vytváření sestav o chybách správy úložiště.

## <a name="requirements"></a>Požadavky

**Hlavička:** \<nový >

**Obor názvů:** std

## <a name="remarks"></a>Poznámky

Některé funkce deklarované v této hlavičce jsou nahraditelný. Implementace poskytuje výchozí verzi, jejíž chování je popsáno v tomto dokumentu. Program může však definovat funkci se stejnou signaturou, která má nahradit výchozí verzi v době připojení. Náhradní verze musí splňovat požadavky popsané v tomto dokumentu.

## <a name="members"></a>Členové

### <a name="objects"></a>Objekty

|||
|-|-|
|[nothrow](../standard-library/new-functions.md#nothrow)|Poskytuje objekt, který má být použit jako argument pro verze **nového** a **odstranění**ve verzi **throw** .|

### <a name="typedefs"></a>Typedefs

|||
|-|-|
|[new_handler](../standard-library/new-typedefs.md#new_handler)|Typ, který odkazuje na funkci vhodnou pro použití jako nová obslužná rutina.|
|[hardware_constructive_interference_size](../standard-library/new-typedefs.md#hardware_destructive_interference_size)||
|[hardware_destructive_interference_size](../standard-library/new-typedefs.md#hardware_destructive_interference_size)||

### <a name="functions"></a>Funkce

|||
|-|-|
|[get_new_handler](../standard-library/new-functions.md#get_new_handler)||
|[peníze](../standard-library/new-functions.md#launder)||
|[set_new_handler](../standard-library/new-functions.md#set_new_handler)|Nainstaluje uživatelskou funkci, která se zavolá, když se nové v pokusu o přidělení paměti nezdaří.|

### <a name="operators"></a>Operátory

|||
|-|-|
|[delete – operátor](../standard-library/new-operators.md#op_delete)|Funkce volaná výrazem delete pro zrušení přidělení úložiště pro jednotlivé objekty.|
|[delete – operátor&#91;&#93;](../standard-library/new-operators.md#op_delete_arr)|Funkce volaná výrazem delete pro zrušení přidělení úložiště pro pole objektů.|
|[New – operátor](../standard-library/new-operators.md#op_new)|Funkce, která je volána novým výrazem k přidělení úložiště pro jednotlivé objekty.|
|[New – operátor&#91;&#93;](../standard-library/new-operators.md#op_new_arr)|Funkce, která je volána novým výrazem k přidělení úložiště pro pole objektů.|

### <a name="enums"></a>Výčty

|||
|-|-|
|[align_val_t](../standard-library/new-operators.md#op_align_val_t)||

### <a name="classes"></a>Třídy

|||
|-|-|
|[bad_alloc – třída](../standard-library/bad-alloc-class.md)|Třída popisuje vyvolanou výjimku, která označuje, že žádost o přidělení nebyla úspěšná.|
|[bad_array_new_length – třída](../standard-library/bad-array-new-length.md)||
|[nothrow_t – třída](../standard-library/nothrow-t-structure.md)|Třída se používá jako parametr funkce pro operátor New k označení toho, že funkce by měla vracet ukazatel s hodnotou null, aby nahlásila selhání přidělení, namísto vyvolání výjimky.|

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
