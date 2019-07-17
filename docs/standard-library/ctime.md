---
title: '&lt;CTime –&gt;'
ms.date: 11/04/2016
f1_keywords:
- <ctime>
- std::<ctime>
helpviewer_keywords:
- ctime header
ms.assetid: c1f7d4a4-4bfe-4e35-92cb-f63dbd3c39a8
ms.openlocfilehash: 647e9e65c7dae3686c5e84c58169d2a490c1e084
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68246585"
---
# <a name="ltctimegt"></a>&lt;CTime –&gt;

Obsahuje hlavičku knihovny Standard C \<time.h > a přidá názvy přidružené k `std` oboru názvů.

## <a name="syntax"></a>Syntaxe

```cpp
#include <ctime>
```

## <a name="remarks"></a>Poznámky

Včetně této hlavičky zajišťuje, že názvy deklarované s vnějším spojením v záhlaví knihovny Standard C jsou deklarovány v `std` oboru názvů.

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
    
## <a name="functions"></a>Funkce

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

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[Standardní knihovna C++ – přehled](../standard-library/cpp-standard-library-overview.md)<br/>
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)<br/>
