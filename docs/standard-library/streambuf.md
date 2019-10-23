---
title: '&lt;streambuf &gt;'
ms.date: 11/04/2016
f1_keywords:
- <streambuf>
helpviewer_keywords:
- streambuf header
ms.assetid: 4365b25c-5831-488b-b9c2-867bfe961b89
ms.openlocfilehash: ca5f53d67bb32e59c20d1d440879144f0a617c66
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/21/2019
ms.locfileid: "72686026"
---
# <a name="ltstreambufgt"></a>&lt;streambuf &gt;

Zahrňte standardní hlavičku iostreams \<streambuf > k definování šablony třídy [basic_streambuf](../standard-library/basic-streambuf-class.md), která je základní pro operaci iostreams třídy. Tato hlavička je obvykle zahrnutá v jiné hlavičce iostreams; Jenom zřídka je potřeba ho zahrnout přímo.

## <a name="syntax"></a>Syntaxe

```cpp
#include <streambuf>
```

### <a name="typedefs"></a>Typedefs

|Název typu|Popis|
|-|-|
|[streambuf](../standard-library/streambuf-typedefs.md#streambuf)|Specializace `basic_streambuf`, která jako parametry šablony používá **char** .|
|[wstreambuf –](../standard-library/streambuf-typedefs.md#wstreambuf)|Specializace `basic_streambuf`, která používá **wchar_t** jako parametry šablony.|

### <a name="classes"></a>Třídy

|Třída|Popis|
|-|-|
|[basic_streambuf – třída](basic-streambuf-class.md)|Šablona třídy popisuje abstraktní základní třídu pro odvození vyrovnávací paměti datového proudu, který řídí přenos prvků do a z konkrétní reprezentace datového proudu.|

## <a name="see-also"></a>Viz také:

@No__t_1 [referenčních souborů hlaviček](../standard-library/cpp-standard-library-header-files.md)
[Bezpečnost vlákna ve C++ standardní knihovně](../standard-library/thread-safety-in-the-cpp-standard-library.md) \
[iostream – programování](../standard-library/iostream-programming.md) \
[iostreams – konvence](../standard-library/iostreams-conventions.md)
