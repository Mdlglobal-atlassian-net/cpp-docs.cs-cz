---
title: space_info – struktura | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- filesystem/std::tr2::sys::space_info
dev_langs:
- C++
ms.assetid: f2b35b42-06ff-45bd-8617-39a0f5358a54
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3506572586f0dc8edc3f9e97955e7612bcea46ae
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
ms.locfileid: "33859183"
---
# <a name="spaceinfo-structure"></a>space_info – struktura

Obsahuje informace o svazku.

## <a name="syntax"></a>Syntaxe

```cpp
struct space_info   {
    uintmax_t capacity;
    uintmax_t free;
    uintmax_t available;
    };
```

## <a name="members"></a>Členové

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|`unsigned long long available`|Představuje počet bajtů, které jsou k dispozici, která bude představovat data na svazku.|
|`unsigned long long capacity`|Představuje celkový počet bajtů, které může představovat svazku.|
|`unsigned long long free`|Představuje počet bajtů, které nejsou používány k reprezentaci dat na svazku.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<filesystem >

**Namespace:** std::experimental::filesystem

## <a name="see-also"></a>Viz také

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<FileSystem >](../standard-library/filesystem.md)<br/>
[space](http://msdn.microsoft.com/en-us/7fce0b0e-523b-4598-b218-47245d0204ca)<br/>
[Navigace v systému souborů (C++)](../standard-library/file-system-navigation.md)<br/>
