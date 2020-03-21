---
title: '&lt;CTime –&gt;'
ms.date: 11/04/2016
f1_keywords:
- <ctime>
- std::<ctime>
helpviewer_keywords:
- ctime header
ms.assetid: c1f7d4a4-4bfe-4e35-92cb-f63dbd3c39a8
ms.openlocfilehash: 2b3f31ba48ca831b2d2d8cd460b60549c4debe83
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076627"
---
# <a name="ltctimegt"></a>&lt;CTime –&gt;

Obsahuje hlavičku standardní knihovny jazyka C \<Time. h > a přidává přidružené názvy do oboru názvů `std`.

## <a name="syntax"></a>Syntaxe

```cpp
#include <ctime>
```

## <a name="remarks"></a>Poznámky

Včetně této hlavičky zajišťuje, že názvy deklarované s vnějším propojením v hlavičce standardní knihovny jazyka C jsou deklarovány v oboru názvů `std`.

## <a name="constants"></a>Konstanty

```cpp
#define NULL
#define CLOCKS_PER_SEC
#define TIME_UTC

namespace std {
    using size_t = see below;
    using clock_t = see below ;
    using time_t = see below ;
}
```

## <a name="structures"></a>Struktury

```cpp
struct timespec;
struct tm;
```

## <a name="functions"></a>Functions

```cpp
clock_t clock();
double difftime(time_t time1, time_t time0);
time_t mktime(struct tm* timeptr);
time_t time(time_t* timer);
int timespec_get(timespec* ts, int base);
char* asctime(const struct tm* timeptr);
char* ctime(const time_t* timer);
struct tm* gmtime(const time_t* timer);
struct tm* localtime(const time_t* timer);
size_t strftime(char* s, size_t maxsize, const char* format, const struct tm* timeptr);
```

## <a name="see-also"></a>Viz také

\ [referenčních souborů hlaviček](../standard-library/cpp-standard-library-header-files.md)
Přehled standardní knihovny\ [ C++ ](../standard-library/cpp-standard-library-overview.md)
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
