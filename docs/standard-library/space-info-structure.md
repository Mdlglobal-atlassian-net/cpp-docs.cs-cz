---
title: space_info – struktura
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::tr2::sys::space_info
ms.assetid: f2b35b42-06ff-45bd-8617-39a0f5358a54
ms.openlocfilehash: b6998f4ac7ced2d85063186edbd47227b6d24ca5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50559130"
---
# <a name="spaceinfo-structure"></a>space_info – struktura

Obsahuje informace o svazku.

## <a name="syntax"></a>Syntaxe

```cpp
struct space_info
{
    uintmax_t capacity;
    uintmax_t free;
    uintmax_t available;
};
```

## <a name="members"></a>Členové

### <a name="public-data-members"></a>Veřejné datové členy

|Název|Popis|
|----------|-----------------|
|`unsigned long long capacity`|Představuje celkový počet bajtů, které mohou představovat svazku.|
|`unsigned long long free`|Představuje počet bajtů, které nejsou použity pro reprezentaci dat na svazku.|
|`unsigned long long available`|Představuje počet bajtů, které jsou k dispozici pro reprezentaci dat na svazku.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<filesystem >

**Namespace:** std::experimental::filesystem

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[\<FileSystem >](../standard-library/filesystem.md)<br/>
[Navigace v systému souborů (C++)](../standard-library/file-system-navigation.md)<br/>
