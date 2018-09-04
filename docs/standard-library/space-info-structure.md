---
title: space_info – struktura | Dokumentace Microsoftu
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
ms.openlocfilehash: 8a0f1eb9818356e7261125efaea69e275c3e29b8
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43684680"
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
|`unsigned long long available`|Představuje počet bajtů, které jsou k dispozici pro reprezentaci dat na svazku.|
|`unsigned long long capacity`|Představuje celkový počet bajtů, které mohou představovat svazku.|
|`unsigned long long free`|Představuje počet bajtů, které nejsou použity pro reprezentaci dat na svazku.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<filesystem >

**Namespace:** std::experimental::filesystem

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<FileSystem >](../standard-library/filesystem.md)<br/>
[Navigace v systému souborů (C++)](../standard-library/file-system-navigation.md)<br/>
