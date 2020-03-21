---
title: '&lt;csignal&gt;'
ms.date: 11/04/2016
f1_keywords:
- <csignal>
helpviewer_keywords:
- csignal header
ms.assetid: d18bcf82-a89a-476c-a6bf-726af956f7c0
ms.openlocfilehash: fcad9c1b5ec20a7a10afc40884ece8ae8abec184
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076679"
---
# <a name="ltcsignalgt"></a>&lt;csignal&gt;

Obsahuje hlavičku standardní knihovny jazyka C \<Signal. h > a přidává přidružené názvy do oboru názvů `std`. Včetně této hlavičky zajišťuje, že názvy deklarované s vnějším propojením v hlavičce standardní knihovny jazyka C jsou deklarovány v oboru názvů `std`.

## <a name="syntax"></a>Syntaxe

```cpp
#include <csignal>
```

## <a name="namespace-and-macros"></a>Obor názvů a makra

```cpp
namespace std {
    using sig_atomic_t = see below;

    extern using signal-handler = void(int);
}

#define SIG_DFL
#define SIG_ERR
#define SIG_IGN
#define SIGABRT
#define SIGFPE
#define SIGILL
#define SIGINT
#define SIGSEGV
#define SIGTERM
```

## <a name="functions"></a>Functions

```cpp
signal-handler* signal(int sig, signal-handler* func);
int raise(int sig);
```

## <a name="see-also"></a>Viz také

\ [referenčních souborů hlaviček](../standard-library/cpp-standard-library-header-files.md)
Přehled standardní knihovny\ [ C++ ](../standard-library/cpp-standard-library-overview.md)
[Bezpečný přístup z více vláken ve standardní knihovně C++](../standard-library/thread-safety-in-the-cpp-standard-library.md)
